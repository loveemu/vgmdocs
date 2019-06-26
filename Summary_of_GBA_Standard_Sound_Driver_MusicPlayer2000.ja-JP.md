# GBA 標準サウンドドライバ（MusicPlayer2000）の概要

任天堂のゲームボーイアドバンスのSDKには、ゲームで音楽や効果音を鳴らすためのサウンドドライバライブラリが添付されています。
このドライバは公式には MusicPlayer2000 あるいは m4a と称されており、しばしば非公式に Sappy という名前でも呼ばれます。（以降は MP2k と称します）

必然的に、MP2k は（とくに日本国内でリリースされた）非常に多くのゲームで使用されています。
また、古くから多くの人々によって解析されてきたため、とても多くの解析情報やツールが存在します。

本記事では MP2k への深い説明はしませんが、MP2k の概要と詳細を知るための各種リソースを紹介します。

[English version](Summary_of_GBA_Standard_Sound_Driver_MusicPlayer2000.md)

## MusicPlayer2000 の仕様概要

ほとんどあらゆることは以下のドキュメントで説明されています。

[Romhacking.net - Documents - GBA "Sappy" sound engine information](https://www.romhacking.net/documents/462/)

主な説明をまとめると MP2k は次の特徴を持ちます。

* ソフトウェア合成によるPCMサウンド（DirectSound）＋GB互換サウンドが使用可能
* PCMサウンド（DirectSound）
  * 再生周波数は 5734 ～ 42048 Hz の間で選択可能（デフォルトは 13379 Hz）
  * チャンネル数は 1～12 の間で選択可能（デフォルトは 8）
  * インストゥルメントごとの ADSR 設定が可能（8-bit）
  * 線形補間ありのリサンプリング
  * ディレイ固定の単純なリバーブ（エコー）エフェクトを搭載
  * ミキサーの処理速度や出力品質はあまり良くない（遅い、量子化ノイズが多いなどの問題があります。詳細は上記ドキュメントを参照）
* GB互換サウンド
  * 矩形波×2 ＋ 波形メモリ×1 ＋ ノイズ×1
* データフォーマット
  * MIDI/AIFF ファイルをアセンブリ（*.s）にコンバートし、GBA ROM をビルドする
  * シーケンスデータは SMF Format 1 のようなマルチトラックフォーマット（分解能は 24）
  * サンプルデータは無圧縮の符号つき 8-bit PCM（Microsoft Wave とは符号が逆なので注意）
  * BGM と SFX の区別はない。すべてのサウンドはシーケンス＋バンクの組み合わせで構成される

いくつかのゲームでは MP2k を改善・拡張した互換ドライバが使用されています。

* ポケットモンスターシリーズ（圧縮サンプルを扱える）
* 黄金の太陽など、株式会社キャメロットによって開発されたタイトル
* メトロイドフュージョン、メトロイドゼロミッション
* など

## MusicPlayer2000 ドライバ関数の基本利用

基本的には 4 つの関数を使用して動作します。

まずは初期化ルーチンで m4aSoundInit 関数を呼び出し、サウンドを初期化します。

```c
void m4aSoundInit(void);
```

VBlank 割り込みハンドラでは、割り込み直後に m4aSoundVSync 関数を呼び出します。

```c
void m4aSoundVSync(void);
```

メインルーチンでは各フレーム（約1/60秒）ごとに m4aSoundMain 関数を呼び出します。

```c
void m4aSoundMain(void);
```

あとは m4aSongNumStart 関数で曲番号を指定して演奏を開始します。

```c
void m4aSongNumStart(u16 n);
```

これらの関数のアドレスは通常 saptapper （MP2k 向けの自動化されたリッピングツール）で検出することができます。

[loveemu/saptapper: Automated GSF ripper](https://github.com/loveemu/saptapper)

## MusicPlayer2000 シーケンスのコマンド一覧

シーケンスデータのイベント一覧を下表に示します。

原則として、1バイト引数は 0～127 の範囲内の値を使用し、0x80 ～ 0xFF の範囲は使用しません。

|コマンド     |シンボル   |引数                                    |繰り返し |説明                                                                          |
|-------------|-----------|----------------------------------------|---------|------------------------------------------------------------------------------|
|0x00 ～ 0x7F |n/a        |n/a                                     |可       |コマンド自身を第一引数として、前回の繰り返し可能コマンドを繰り返す            |
|0x80 ～ 0xB0 |W00 ～ W96 |void                                    |不可     |デルタタイム（Wait）                                                          |
|0xB1         |FINE       |void                                    |不可     |トラック終了                                                                  |
|0xB2         |GOTO       |u32 dest                                |不可     |指定先アドレス（0x8XXXXXX のような絶対ハードウェアアドレス）にジャンプ        |
|0xB3         |PATT       |u32 dest                                |不可     |パターン開始（サブルーチンジャンプ、ネスト不可）                              |
|0xB4         |PEND       |void                                    |不可     |パターン終了                                                                  |
|0xB5         |REPT       |u8 count, u32 dest                      |不可     |パターンを繰り返す（繰り返し回数 0～255）                                     |
|0xB9         |MEMACC     |u8 mem_set, u8 adr, u8 dat [, u32 dest] |不可     |メモリアクセス（ダイナミックな条件付きジャンプに使用。詳細は後述）            |
|0xBA         |PRIO       |u8                                      |不可     |トラックの優先度を設定（0～255、高い値ほど高優先度）                          |
|0xBB         |TEMPO      |u8                                      |不可     |テンポ。BPM の半分の値を指定する（11～255, tempo 75 のとき 1 frame = 1 tick） |
|0xBC         |KEYSH      |s8                                      |不可     |トランスポーズ（-128～127、トラックごとに適用）                               |
|0xBD         |VOICE      |u8                                      |可       |インストゥルメント                                                            |
|0xBE         |VOL        |u8                                      |可       |ボリューム                                                                    |
|0xBF         |PAN        |u8                                      |可       |パン（0: 左, 64: 中央, 127: 右）                                              |
|0xC0         |BEND       |u8                                      |可       |ピッチベンド（0～127、64 が中央）                                             |
|0xC1         |BENDR      |u8                                      |可       |ピッチベンドレンジ（半音単位で指定、デフォルトは 2）                          |
|0xC2         |LFOS       |u8                                      |不可     |LFO の速度（高い値ほど高速、実際の速度はテンポとともに変動）                  |
|0xC3         |LFODL      |u8                                      |不可     |LFO のディレイ（ティック数で指定）                                            |
|0xC4         |MOD        |u8                                      |可       |LFO の深さ                                                                    |
|0xC5         |MODT       |u8                                      |不可     |LFO の種類（0: ピッチ (デフォルト), 1: ボリューム, 2: パン）                  |
|0xC8         |TUNE       |u8                                      |可       |マイクロチューニング（0: 半音低下, 64: 変更なし: 127: 半音増加）              |
|0xCD 0x08    |XCMD xIECV |u8                                      |可       |疑似エコーのボリューム（0～127）                                              |
|0xCD 0x09    |XCMD xIECL |u8                                      |可       |疑似エコーの長さ（0～127、フレーム数（xx/60 秒）で指定）                      |
|0xCE         |EOT        |[u8 key]                                |可       |タイ終了／ノートオフ                                                          |
|0xCF         |TIE        |[u8 key [, u8 velo]]                    |可       |タイ開始／ノートオン（0xCE に到達するまで長さは不定）                         |
|0xD0 ～ 0xFF |N01 ～ N96 |[u8 key [, u8 velo [, u8 gtp]]]         |可       |ノート（第三引数はゲートタイムの微調整用、ティック単位で指定）                |

### ノート

Wxx コマンド (0x80 ～ 0xB0)  と Nxx コマンド (0xD0 ～ 0xFF) は、以下のテーブルに基づいて 1～96 までの長さを表現します。

```c
const u8 noteLengthTable[48] = {
   1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
  17, 18, 19, 20, 21, 22, 23, 24, 28, 30, 32, 36, 40, 42, 44, 48,
  52, 54, 56, 60, 64, 66, 68, 72, 76, 78, 80, 84, 88, 90, 92, 96
};
```

### メモリアクセス (MEMACC)

MEMACC (0xB9) は共有のメモリ領域（最大 256 バイトの RAM 領域 `m4a_memacc_area`）を使用し、ゲームの状態に応じて動作に条件付きジャンプを実行するためのコマンドです。ほとんど使用されていません。

このコマンドは基本的に3つの引数を取りますが、条件分岐命令では4つめの引数に分岐先アドレスを指定します。

```asm
@ for arithmetic operations
MEMACC, mem_set, adr, dat

@ for branching instructions
MEMACC, mem_set, adr, dat, dest
```

mem_set で演算の種類を指定し、adr と dat で演算の引数（0～255）を指定します。

mem_set には次の値を指定可能です。

|値 |シンボル    |説明                        |疑似構文                      |
|---|------------|----------------------------|------------------------------|
|0  |mem_set     |代入（即値）                |`$adr = #dat`                 |
|1  |mem_add     |加算（即値）                |`$adr += #dat`                |
|2  |mem_sub     |減算（即値）                |`$adr -= #dat`                |
|3  |mem_mem_set |代入（間接）                |`$adr = $dat`                 |
|4  |mem_mem_add |加算（間接）                |`$adr += $dat`                |
|5  |mem_mem_sub |減算（間接）                |`$adr -= $dat`                |
|6  |mem_beq     |条件分岐（即値） 等しい     |`if ($adr == #dat) goto dest` |
|7  |mem_bne     |条件分岐（即値） 等しくない |`if ($adr != #dat) goto dest` |
|8  |mem_bhi     |条件分岐（即値） より大きい |`if ($adr > #dat) goto dest` |
|9  |mem_bhs     |条件分岐（即値） 以上       |`if ($adr >= #dat) goto dest`  |
|10 |mem_bls     |条件分岐（即値） 以下       |`if ($adr <= #dat) goto dest` |
|11 |mem_blo     |条件分岐（即値） より小さい |`if ($adr < #dat) goto dest`  |
|12 |mem_mem_beq |条件分岐（間接） 等しい     |`if ($adr == $dat) goto dest` |
|13 |mem_mem_bne |条件分岐（間接） 等しくない |`if ($adr != $dat) goto dest` |
|14 |mem_mem_bhi |条件分岐（間接） より大きい |`if ($adr > $dat) goto dest` |
|15 |mem_mem_bhs |条件分岐（間接） 以上       |`if ($adr >= $dat) goto dest`  |
|16 |mem_mem_bls |条件分岐（間接） 以下       |`if ($adr <= $dat) goto dest` |
|17 |mem_mem_blo |条件分岐（間接） より小さい |`if ($adr < $dat) goto dest`  |

## 既知の関数の一覧

```c
void m4aSoundVSync(void);
void m4aSoundInit(void);
void m4aSoundMode(u32 mode);
void m4aSoundMain(void);
void m4aSongNumStart(u16 n);
void m4aMPlayStart(MusicPlayerArea *ma, SongHeader *so);
void m4aSongNumStartOrChange(u16 n);
void m4aSongNumStartOrContinue(u16 n);
void m4aSongNumStop(u16 n);
void m4aMPlayStop(MusicPlayerArea *ma);
void m4aSongNumContinue(u16 n);
void m4aMPlayAllStop(void);
void m4aMPlayContinue(MusicPlayerArea *ma);
void m4aMPlayAllContinue(void);
void m4aMPlayFadeOut(MusicPlayerArea *ma, u16 sp);
void m4aMPlayImmInit(MusicPlayerArea *ma);
void m4aSoundVSyncOff(void);
void m4aSoundVSyncOn(void);
void m4aMPlayTempoControl(MusicPlayerArea *ma, u16 te);
void m4aMPlayVolumeControl(MusicPlayerArea *ma, u16 tb, u16 vo);
void m4aMPlayPitchControl(MusicPlayerArea *ma, u16 tb, s16 pi);
void m4aMPlayPanpotControl(MusicPlayerArea *ma, u16 tb, s8 pa);
void m4aMPlayModDepthSet(MusicPlayerArea *ma, u16 tb, u8 md);
void m4aMPlayLFOSpeedSet(MusicPlayerArea *ma, u16 tb, u8 ls);
```

## ドキュメント

[Romhacking.net - Documents - GBA "Sappy" sound engine information](https://www.romhacking.net/documents/462/) (by Bregalad, ipatix)

## ツール・ソースコード

* [ipatix/agbplay: Music player for the most common GBA sound format](https://github.com/ipatix/agbplay)
  * MP2k フォーマットを再生可能な PC 向けミュージックプレイヤー（LGPLv3）
  * ソースコードがドライバを理解するうえで参考になります（シーケンスデータ周りは StreamGenerator.cpp 参照）
  * ipatix 氏は著名な MP2k の解析者の一人で、同氏の github には m4a2s, midi2agb, wav2agb など、他の MP2k 用ツールもあります（ハックロム開発などに便利）
* [Kermalis/VGMusicStudio: A program that lets you listen to the music from popular video game formats.](https://github.com/Kermalis/VGMusicStudio)
  * agbplay より後発の類似ツール、C# 製（LGPLv3）
* [loveemu/saptapper: Automated GSF ripper](https://github.com/loveemu/saptapper) (A reimplementation of Caitsith2's saptapper)
  * MP2k 向けの全自動の GSF リッピングツール
  * m4a の基本的な関数を検出する用途にも使える
  * フォーク元: [GSF Ripping Tools - caitsith2.net](http://gsf.caitsith2.net/ripping.html)
* [jpmac26/gba-mus-ripper: A fork of Bregalad's "GBA Mus Riper" program](https://github.com/jpmac26/gba-mus-ripper)
  * MP2k フォーマットを MIDI/SF2 形式でエクスポートできるツール
  * sappy_detector.exe は MP2k の検出と基本情報の確認に使える
  * フォーク元: [Utilities - GBA Mus Riper - Romhacking.net](https://www.romhacking.net/utilities/881/)
* [pret/pokeruby: Disassembly of Pokémon Ruby/Sapphire](https://github.com/pret/pokeruby)
  * 音楽データの参考例
  * [m4a_internal.h](https://github.com/pret/pokeruby/blob/master/include/gba/m4a_internal.h) は MP2k の内部データ構造をよく表しています
