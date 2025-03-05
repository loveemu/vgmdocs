# Conversion Tools for Video Game Music (Focuses on Sequenced Music → MIDI)

This article introduces conversion tools for various video game music format, mainly focuses on sequenced music. If your best favorite tool is missing, let me know!

This document is Unlicensed. Please feel free to copy and modify any part of its content as necessary. Credits are preferred but not required.

主にゲーム音楽を MIDI, DLS, Soundfont などに変換するツールを紹介しています。Google 翻訳を使って読めばだいたいの内容はわかると思います。

## Allround

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/vgmtrans/vgmtrans">VGMTrans</a></td>
    <td>♥</td>
    <td><a href="https://github.com/mikelow">Mike</a></td>
    <td>zlib License</td>
    <td>GUI</td>
    <td>Music player for sequenced music. MIDI/DLS/SF2 export is available. Various formats are supported with varying degrees of accuracy.</td>
  </tr>
  <tr>
    <td><a href="https://sourceforge.net/projects/vgmtoolbox/">VGMToolbox</a></td>
    <td>♥</td>
    <td><a href="https://github.com/snakemeat">Snakemeat</a></td>
    <td>MIT License</td>
    <td>GUI</td>
    <td>Collection of small tools with integrated interface. You may want this if you have some general file extraction/conversion tasks (especially when you face to xSF formats in my opinion.)</td>
  </tr>
  <tr>
    <td><a href="https://hcs64.com/vgmstream.html">vgmstream</a></td>
    <td>♥</td>
    <td><a href="https://github.com/kode54">kode54</a> and <a href="https://github.com/kode54/vgmstream/graphs/contributors">more</a></td>
    <td><a href="https://opensource.org/licenses/ISC">ISC License</a></td>
    <td>GUI/CLI</td>
    <td>Library for streamed music formats. My favorite frontend is <a href="https://www.foobar2000.org/components/view/foo_input_vgmstream">foo_input_vgmstream</a>, a component for <a href="https://www.foobar2000.org/">foobar2000</a>.</td>
  </tr>
</table>

## NES / Famicom

NES music is usually ripped as [NSF](https://wiki.nesdev.com/w/index.php/NSF) and its extended format [NSFe](https://wiki.nesdev.com/w/index.php/NSFe). NSFe can be turned back to NSF by VGMToolbox, if necessary.

[Extract DPCM samples from NES/NSF](http://loveemu.hatenablog.com/entry/20080227/nsf_dcm_dump) is possible, but I don't know what approach is the easiest. Is there a good tool for it?

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="http://gigo.retrogames.com/download.html">nsf2midi</a></td>
    <td>♥</td>
    <td>Gigo</td>
    <td>Not Specified (Closed Source)</td>
    <td>GUI</td>
    <td>Classic Win32 application. Extra sound chips are supported. Frame-based emulation (i.e. approximately 1/60s resolution with fixed tempo; it's pretty enough for music but you may want more resolution for SFX). Unable to define instrument per duty cycle, sadly.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/gocha/emu2midi-lua">nes2midi.lua</a></td>
    <td></td>
    <td><a href="https://github.com/gocha">gocha</a></td>
    <td>MIT License</td>
    <td>GUI (Lua Console)</td>
    <td>Lua script for <a href="http://www.fceux.com/">FCEUX</a>. User interface is not very fancy (see <a href="http://loveemu.hatenablog.com/entry/20130627/Emu2MIDI_Lua_Tools">my guide</a>). Extra sound chips are not supported. Frame-based emulation. It's worth a try when you couldn't be satisfied with nsf2midi.</td>
  </tr>
</table>

### Specific Companies / Titles

In this era, there are no standard for in-game music formats. The music formats of some major games (Mega Man for example) are reversed by ROM hack communities.

Let me know if there is a fancy resource for them!

## Game Boy

Game Boy music is usually ripped as [GBS](http://www.vgmpf.com/Wiki/index.php?title=GBS). GBS can be turned back to ROM by [GBS2GB](http://www.angelfire.com/nc/ugetab/), if necessary.

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/gocha/emu2midi-lua">gb2midi.lua</a></td>
    <td></td>
    <td><a href="https://github.com/gocha">gocha</a></td>
    <td>MIT License</td>
    <td>GUI (Lua Console)</td>
    <td>Lua script for <a href="https://code.google.com/archive/p/vba-rerecording/">VBA-RR V23</a>. User interface is not very fancy (see <a href="http://loveemu.hatenablog.com/entry/20130627/Emu2MIDI_Lua_Tools">my guide</a>). Frame-based emulation (i.e. approximately 1/60s resolution with fixed tempo). <a href="http://www.angelfire.com/nc/ugetab/">GBS2GB</a> required for conversion from GBS.</td>
  </tr>
</table>

## SNES / Super Famicom

There are two music formats for SNES. Most games are ripped as [SPC](http://www.vgmpf.com/Wiki/index.php?title=SPC) format. Some other undumpable games are ripped as [SNSF](http://www.vgmpf.com/Wiki/index.php?title=SNSF) format. 99% of tools accept SPC files as input.

SPC file can be converted to ROM by [SPC2ROM](https://alpha-ii.com/Download/MainOld.html) command-line tool. SNSF file can be turned back to ROM by [snsfopt](https://github.com/loveemu/snsfopt) command-line tool.

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Export Samples</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="http://gigo.retrogames.com/download.html">spc2midi</a></td>
    <td>♥</td>
    <td>Gigo</td>
    <td>Not Specified (Closed Source)</td>
    <td>GUI</td>
    <td>No</td>
    <td>Classic Win32 application. Emulation-based (i.e. fixed tempo, pitch detection can be wrong sometimes). Conversion options are fairly adjustable.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/gocha/split700">split700</a></td>
    <td>♥</td>
    <td><a href="https://github.com/gocha">gocha</a></td>
    <td>MIT License</td>
    <td>CLI</td>
    <td>Yes</td>
    <td>Command-line tool to extract SNES BRR samples from SPC file.</td>
  </tr>
  <tr>
    <td><a href="https://www.smwcentral.net/?p=section&a=details&id=4600">SPCTool</a></td>
    <td></td>
    <td>Alpha-II Production</td>
    <td>Not Specified (Source Code Available)</td>
    <td>GUI</td>
    <td>Yes</td>
    <td>Advanced SPC player/debugger/converter. It looks great despite it's very aged. However, it's unfortunately buggy and MIDI converter is not implemented.</td>
  </tr>
</table>

I'm not satisfied with spc2midi for several reasons. Creating my own converter is one of my dreams since 2016, but I have no progress as of now.

### Specific Companies / Titles

[Loveemu](https://github.com/loveemu) (it's me!) have reversed major music engines developed by a number of companies (collections of disassembly are archived at [vgm-disasm](https://github.com/loveemu/vgm-disasm)). The music parsers are ported to VGMTrans, with some heuristic-based music engine detection. It's worth a try!

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Export Samples</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/vgmtrans/vgmtrans">VGMTrans</a></td>
    <td>♥</td>
    <td><a href="https://github.com/mikelow">Mike</a></td>
    <td>zlib License</td>
    <td>GUI</td>
    <td>Yes</td>
    <td>The music parser is pretty accurate, but it lacks some MIDI conversion features such as <a href="https://github.com/vgmtrans/vgmtrans/issues/108">pitch bend slider</a>, vibrato, tremolo, etc. (as of 2018).</td>
  </tr>
  <tr>
    <td><a href="https://github.com/ValleyBell/MidiConverters">sg2mid</a></td>
    <td></td>
    <td>ValleyBell</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>No</td>
    <td>This converts SPC files from Speedy Gonzales: Los Gatos Bandidos to MIDI. No precompiled binary.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/ValleyBell/MidiConverters">top2mid</a></td>
    <td></td>
    <td>ValleyBell</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>No</td>
    <td>This tool converts SPC files from SFC Tales of Phantasia and Star Ocean to MIDI. No precompiled binary.</td>
  </tr>
</table>

## Nintendo 64

[USF](https://www.hcs64.com/usf/) is a portable music format for Nintendo 64. USF may contain an N64 save state and/or ROM image.

USF file can be turned back to ROM by hcs's usf2rom command-line tool. However I don't know where I can download his ripping tools.

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Export Samples</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/jombo23/N64-Tools/tree/master/N64%20Soundbank%20Tool">N64 Soundbank Tool</a></td>
    <td>♥</td>
    <td><a href="https://twitter.com/subdrag">SubDrag</a></td>
    <td>Unlicense</td>
    <td>GUI</td>
    <td>Yes</td>
    <td>Able to extract sound data as MIDI/DLS files from ROM. A number of games are supported (despite there is a variety of format differences!)</td>
  </tr>
  <tr>
    <td><a href="https://github.com/sauraen/seq64">Seq64</a></td>
    <td>♥</td>
    <td><a href="https://github.com/sauraen">sauraen</a></td>
    <td>GPLv3</td>
    <td>CLI</td>
    <td>No</td>
    <td>Command-line tool for Nintendo's Audioseq format. It's integrated to N64 Soundbank tool, so you probably don't need to download and use it separately.</td>
  </tr>
</table>

## Game Boy Advance

Most of GBA games uses a standard music engine named MusicPlayer2000 (also known as Sappy) developed by Nintendo. Detailed informations are available at the [Bregalad's guide](http://www.romhacking.net/docs/462/) (and also explained well in the official SDK).

However, MP2000 is not the only sound driver of GBA. Some games use a custom driver based on MP2000 (Metroid Fusion, Golden Sun, Mario & Luigi: Superstar Saga for example), some other games use a completely different driver such as [GAX](https://www.shinen.com/music/music.php3?gax) (by Shin'En), MusyX (by Factor 5), [Krawall](https://github.com/sebknzl/krawall), SCM3LT, etc.

[GSF](http://www.caitsith2.com/gsf/) is a portable sound format for GBA. GSF contains a GBA ROM image with an extra header data. GSF can be turned back to GBA ROM by [saptapper](https://github.com/loveemu/saptapper), or you can also use VGMTrans if you don't like a command-line tool.

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Export Samples</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://www.romhacking.net/utilities/881/">GBA Mus Riper</a></td>
    <td>♥</td>
    <td>Bregalad</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>Yes</td>
    <td>Input a GBA ROM, and MIDI/SF2 files shall be given for you. Even PCM channels are supported. Incredible!</td>
  </tr>
  <tr>
    <td><a href="https://github.com/Kermalis/GBAMusicStudio">GBA Music Studio</a></td>
    <td>♥</td>
    <td><a href="https://github.com/Kermalis">Kermalis</a></td>
    <td>LGPLv3</td>
    <td>GUI</td>
    <td>Yes</td>
    <td>Integrated music tool. Good replacement for Sappy. Still in development. Requires Visual Studio (Visual C#) for compiling.</td>
  </tr>
  <tr>
    <td><a href="https://u3.getuploader.com/pkkai/download/136/sappy2006mod17.1.zip">Sappy 2006 mod 17.1</a></td>
    <td></td>
    <td><a href="http://helmet.kafuka.org/">Kyoufu Kawa</a>, nagona</td>
    <td>MIT License</td>
    <td>GUI</td>
    <td>Yes</td>
    <td>Integrated music tool. Able to export/import MusicPlayer2000 sound data. Not maintained anymore. You must install <a href="http://helmet.kafuka.org/">original Sappy 2006</a> first, otherwise a wild VB6 error will appear.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/vgmtrans/vgmtrans">VGMTrans</a></td>
    <td></td>
    <td><a href="https://github.com/mikelow">Mike</a></td>
    <td>zlib License</td>
    <td>GUI</td>
    <td>No</td>
    <td>Not recommended, as of 2018.</td>
  </tr>
</table>

## GameCube

[HCS Forum \- Gamecube Sequence Format?](https://hcs64.com/mboard/forum.php?showthread=55673)

Sound files can be sometimes compressed/packed. In such a case, you may need an unpacker like [WArchive-Tools](https://github.com/LordNed/WArchive-Tools).

### JAudio/JaiSeq (aka. BMS) by Nintendo EAD

While many researchers had worked on the BMS format, the specification isn't documented very much. You can find some resources from the following topics.

* [HCS Forum - Gamecube BMS sequence ripper/editor - Design? Language? Existing DAW/sequencer plugin?](https://www.hcs64.com/mboard/forum.php?showthread=44951)
* [HCS Forum - BMS finally figured out!!! BMS to MIDI Converter/Exporter coming soon! BMS Collection Thread~](https://hcs64.com/mboard/forum.php?showthread=37639)

Here's a list of tools for GameCube BMS. I haven't tried them so I don't know what tool is the best.

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Export Samples</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/magcius/vgmtrans">VGMTrans (Jasper's fork)</a></td>
    <td>♥</td>
    <td>Jasper St. Pierre (<a href="https://github.com/magcius">magcius</a>)</td>
    <td>zlib License</td>
    <td>GUI</td>
    <td>Yes</td>
    <td>Fork of VGMTrans that supports GameCube JaiSeq and NintendoWare RSAR.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/fuzziqersoftware/gctools">gctools</a></td>
    <td></td>
    <td>Martin Michelsen (<a href="https://github.com/fuzziqersoftware">fuzziqersoftware</a>)</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>Yes?</td>
    <td>Set of tools for reading and translating GameCube files. No precompiled binary.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/derselbst/BMS_DEC">BMS_DEC</a></td>
    <td></td>
    <td><a href="https://github.com/Yoshimaster96">Yoshimaster96</a>, <a href="https://github.com/derselbst">derselbst</a></td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>No</td>
    <td>No precompiled binary.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/camthesaxman/bms2mid">bms2mid</a></td>
    <td></td>
    <td>Cameron Hall (<a href="https://github.com/camthesaxman">camthesaxman</a>)</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>No</td>
    <td>No precompiled binary.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/Sage-of-Mirrors/BMSTool">BMSTool</a></td>
    <td></td>
    <td>Dylan Ascencio (<a href="https://github.com/Sage-of-Mirrors">Sage-of-Mirrors</a>)</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>No</td>
    <td>No precompiled binary. Requires Visual Studio (Visual C#) for compiling.</td>
  </tr>
</table>

### MusyX audio engine by Factor 5

[HCS Forum - Gamecube MusyX Audio Thread](https://hcs64.com/mboard/forum.php?showthread=39182)

Here's a list of tools for MusyX. I haven't tried them so I don't know what tool is the best.

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Export Samples</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/AxioDL/amuse">amuse</a></td>
    <td></td>
    <td><a href="https://github.com/AxioDL">Axiomatic Data Laboratories</a></td>
    <td>MIT License</td>
    <td>CLI</td>
    <td>Yes?</td>
    <td>MIDI and SFX sequencer, designed for compatibility with MusyX audio groups.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/soneek/GCMusyXTools">GCMusyXTools</a></td>
    <td></td>
    <td>Joseph Gibbs (<a href="https://github.com/soneek">soneek</a>)</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>?</td>
    <td>No precompiled binary.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/Nisto/musyx-extract">musyx-extract</a></td>
    <td></td>
    <td><a href="https://github.com/Nisto">Nisto</a></td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>Yes (Extraction Only)</td>
    <td>Sample extractor for GameCube MusyX files. Requires Python interpreter to run.</td>
  </tr>
</table>

## Nintendo DS

[SDAT](http://dshack.wikia.com/wiki/.sdat) is the standard archive file format for the official Nitro Composer framework developed by Nintendo. The following file formats can be found in the game that uses Nitro Composer.

* Nintendo DS (Nitro Composer)
    - [SDAT](http://dshack.wikia.com/wiki/.sdat): Nitro Composer Sound Archive
    - [STRM](http://dshack.wikia.com/wiki/.strm): Nitro Composer SDAT Audio Stream
    - [SBNK](http://dshack.wikia.com/wiki/.sbnk): Nitro Composer SDAT Sound Bank File
    - [SWAR](http://dshack.wikia.com/wiki/.swar): Nitro Composer SDAT Wave Archive
    - SWAV: Nitro Composer Wave File
    - [SSEQ](http://dshack.wikia.com/wiki/.sseq): Nitro Composer SDAT Sound Sequence
    - SSAR: Nitro Composer SDAT Sound Sequence Archive (collection for sound effect)

Unlike GBA, DS games have a filesystem in ROM. If you want to explorer and extract files in DS ROM, there are so many tools to do that. I personally prefer [Tinke](https://github.com/pleonex/tinke), an advanced viewer and editor for files of NDS games, or [ndstool](https://gbatemp.net/download/nintendo-ds-rom-tool-ndstool.29352/) if you prefer CLI.

[2SF](http://www.vgmpf.com/Wiki/index.php?title=2SF) is the portable sound format for Nintendo DS. As usual, 2SF contains a DS ROM image with an extra header data. 2SF can be turned back to DS ROM by [2sf2rom](https://github.com/loveemu/2sf2rom), or you can also use VGMTrans if you don't like a command-line tool.

[NCSF](http://www.cyberbotx.com/NCSF/) is another PSF format specialized to Nitro Composer. NCSF contains a SDAT file with no extra header. You can turn an NCSF back to SDAT by xSF2EXE tool of [VGMToolbox](https://sourceforge.net/projects/vgmtoolbox/).

### SDAT Tools

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Export Samples</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/vgmtrans/vgmtrans">VGMTrans</a></td>
    <td>♥</td>
    <td><a href="https://github.com/mikelow">Mike</a></td>
    <td>zlib License</td>
    <td>GUI</td>
    <td>Yes</td>
    <td>Good for exploring sequenced music (SSEQ/SBNK/SWAR).</td>
  </tr>
  <tr>
    <td><a href="http://dshack.wikia.com/wiki/NDS_Sound_Extractor">NDS Sound Extractor</a></td>
    <td>♥</td>
    <td>Nintendon</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>Yes</td>
    <td>Probably the best if you want to convert all files in SDAT at a time.</td>
  </tr>
  <tr>
    <td><a href="https://sourceforge.net/projects/vgmtoolbox/">VGMToolbox</a></td>
    <td>♥</td>
    <td><a href="https://github.com/snakemeat">Snakemeat</a></td>
    <td>MIT License</td>
    <td>GUI</td>
    <td>Yes (Extraction Only)</td>
    <td>Includes some nice generic SDAT/2SF tools.</td>
  </tr>
</table>

There are more choices. Try searching what you like the best!

### Tools for Digital Sound Elements by Procyon Studio (SMD/SWD)

[Pokemon Mystery Dungeon Utilities](https://github.com/PsyCommando/ppmdu) and [smd2mid](https://github.com/ipatix/smd2mid) are available.

Read the [PMD2 research notes by psy_commando](https://github.com/vgmtrans/vgmtrans/issues/48#issuecomment-394045958) for specifications.

## Wii, Wii U, Switch, etc.

Recent Nintendo consoles use formats very similar to Nitro Composer.

* Wii (NW4R; NintendoWare for Revolution)
    - [BRSTM (RSTM)](http://wiki.tockdom.com/wiki/BRSTM_\(File_Format\)): NW4R Audio Stream
    - [BRSAR (RSAR)](http://wiki.tockdom.com/wiki/BRSAR_\(File_Format\)): NW4R Sound Archive
    - [BRWSD (RWSD)](http://wiki.tockdom.com/wiki/BRWSD_\(File_Format\)): NW4R RSAR Sound File
    - BRWAR (RWAR): NW4R RSAR Wave Archive
    - BRWAV (RWAV): NW4R RSAR Wave File
    - [BRBNK (RBNK)](http://wiki.tockdom.com/wiki/BRBNK_\(File_Format\)): NW4R RSAR Sound Bank File
    - [BRSEQ (RSEQ)](http://wiki.tockdom.com/wiki/BRSEQ_\(File_Format\)): NW4R RSAR Sound Sequence
* Wii U (NW4F; NintendoWare for Café)
    - [BFSTM (FSTM)](http://mk8.tockdom.com/wiki/BFSTM_\(File_Format\)): NW4F Audio Stream
    - [BFSAR (FSAR)](http://mk8.tockdom.com/wiki/BFSAR_\(File_Format\)): NW4F Sound Archive
    - BFWSD (FWSD): NW4F FSAR Sound File
    - BFWAR (FWAR): NW4F FSAR Wave Archive
    - [BFWAV (FWAV)](http://mk8.tockdom.com/wiki/BFWAV_\(File_Format\)): NW4F FSAR Wave File
    - BFBNK (FBNK): NW4F FSAR Sound Bank File
    - [BFSEQ (FSEQ)](http://mk8.tockdom.com/wiki/BFSEQ_\(File_Format\)): NW4F FSAR Sound Sequence
* Nintendo 3DS (NW4C; NintendoWare for CTR)
    - [BCSTM (CSTM)](https://www.3dbrew.org/wiki/BCSTM): NW4C Audio Stream
    - [BCSAR (CSAR)](https://www.3dbrew.org/wiki/BCSAR): NW4C Sound Archive
    - BCWSD (CWSD): NW4C CSAR Sound File
    - BCWAR (CWAR): NW4C CSAR Wave Archive
    - BCWAV (CWAV): NW4C CSAR Wave File
    - BCBNK (CBNK): NW4C CSAR Sound Bank File
    - BCSEQ (CSEQ): NW4C CSAR Sound Sequence

I haven't tried any tools below so I don't know what tool is the best.

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Export Samples</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/libertyernie/brawltools">BrawlBox</a></td>
    <td></td>
    <td><a href="https://github.com/libertyernie">libertyernie</a></td>
    <td>Not Specified (Source Code Available)</td>
    <td>GUI</td>
    <td>Yes</td>
    <td>Integrated tool for Super Smash Bros. Brawl. Supports a lot of NintendoWare file formats.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/magcius/vgmtrans">VGMTrans (Jasper's fork)</a></td>
    <td></td>
    <td>Jasper St. Pierre (<a href="https://github.com/magcius">magcius</a>)</td>
    <td>zlib License</td>
    <td>GUI</td>
    <td>Yes</td>
    <td>Fork of VGMTrans that supports GameCube JaiSeq and NintendoWare RSAR.</td>
  </tr>
  <tr>
    <td><a href="http://wiki.tockdom.com/wiki/BRSAR_Extractor">BRSAR Extractor</a></td>
    <td></td>
    <td><a href="http://wiki.tockdom.com/wiki/Atlas">Atlas</a></td>
    <td>Not Specified (Closed Source)</td>
    <td>GUI</td>
    <td>Yes (Extraction Only)</td>
    <td>Unpacker for BRSAR sound archive.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/soneek/3DSUSoundArchiveTool">3DSUSoundArchiveTool</a></td>
    <td></td>
    <td>Joseph Gibbs (<a href="https://github.com/soneek">soneek</a>)</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>Yes (Extraction Only)</td>
    <td>Unpacker for BCSAR and BFSAR sound archives. No precompiled binary.</td>
  </tr>
</table>

## Genesis / Mega Drive

[VGM format](https://en.wikipedia.org/wiki/VGM_\(file_format\)) is widely used for logging Genesis sound. VGM file can be converted to standard MIDI by [vgm2mid](https://vgmrips.net/wiki/Vgm2mid), but it may not be accurate sometimes since it's kinda old. Also, you can [extract FM synth presets from VGM file](http://loveemu.hatenablog.com/entry/Guide_for_Extracting_FM_Synth_Presets_of_Sega_Genesis) by using [vgm2pre](https://vgmrips.net/wiki/Vgm2pre).

### Specific Companies / Titles

I highly recommend to check for [ValleyBell's MIDI Converters](https://github.com/ValleyBell/MidiConverters), a number of command-line tools for various sound drivers are available.

## Sega Saturn

[seq2mid by Cyber Warrior X: Tool and documentation for the Sega Saturn SEQ format](https://www.romhacking.net/utilities/668/)

Needs more information.

## Dreamcast

Needs information.

## TurboGrafx-16 / PC Engine

Needs more information.

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/gocha/emu2midi-lua">pce2midi.lua</a></td>
    <td></td>
    <td><a href="https://github.com/gocha">gocha</a></td>
    <td>MIT License</td>
    <td>GUI (Lua Console)</td>
    <td>Lua script for <a href="https://code.google.com/archive/p/pcejin/">PCEjin</a>. User interface is not very fancy (see <a href="http://loveemu.hatenablog.com/entry/20130627/Emu2MIDI_Lua_Tools">my guide</a>). Frame-based emulation (i.e. approximately 1/60s resolution with fixed tempo). Conversion from HES/VGM isn't possible?</td>
  </tr>
</table>

## Playstation

In-game sound data formats of Playstation are very PC-friendly. Usually, they are designed to be self-contained, so a song set or a sound bank can be extracted as a single file.

Sony designed standard music format for Playstation. SEQ for music sequence, and VAB for sound banks. VAB is often represented as separate two files, VH (header) and VB (body). SEQ/VAB are widely used, but there are some other formats designed by each developer companies are used as well.

The data is stored in CD-ROM. You can explore files by PC and you may find a music file so easily, if you are fortunate. Sometimes the data may be archived or compressed. In this case, it will be harder to identify the music data.

[PSF](http://www.vgmpf.com/Wiki/index.php?title=PSF) is a portable sound format for Playstation. PSF represents a single PS-X EXE. Uncompressed PS-X EXE can be extracted by xSF2EXE tool of [VGMToolbox](https://sourceforge.net/projects/vgmtoolbox/).

### How To Find Music Data

The easiest first step is to drop a PSF file into [VGMTrans](https://github.com/vgmtrans/vgmtrans). It doesn't always work, but it's a good starting point. The next recommendation is to try PSF Data Finder of [VGMToolbox](https://sourceforge.net/projects/vgmtoolbox/), which has more powerful VH/VB search than VGMTrans.

If no results are given, you may need to save an intermediate dump file which contains the raw sound data, then scan sound files from the file (I will introduce scanning tools later). Here's some example methods for saving the raw dump.

* Decompress PSF by xSF2EXE tool of VGMToolbox (easy)
* Save a whole RAM image by PS1 emulator, such as [XEBRA](http://drhell.web.fc2.com/ps1/) or [BizHawk](http://tasvideos.org/BizHawk.html) (especially effective for compressed formats)
* Save a whole RAM image by PSF player (requires external memory viewer tool?)

If all the steps above are not effective, probably you will need an advanced research specific to the game.

### Tools

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Supported Formats</th>
    <th>Export Samples</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/vgmtrans/vgmtrans">VGMTrans</a></td>
    <td>♥</td>
    <td><a href="https://github.com/mikelow">Mike</a></td>
    <td>zlib License</td>
    <td>GUI</td>
    <td>Various (see README)</td>
    <td>Yes</td>
    <td>VGMToolbox has more powerful VH/VB search. Not supporting <a href="http://web.archive.org/web/20170723173216/http://wiki.qhimm.com:80/view/FF7/PSX/Sound/AKAO_frames">the early version of AKAO</a>, as of 2018.</td>
  </tr>
  <tr>
    <td><a href="https://sourceforge.net/projects/vgmtoolbox/">VGMToolbox</a></td>
    <td>♥</td>
    <td><a href="https://github.com/snakemeat">Snakemeat</a></td>
    <td>MIT License</td>
    <td>GUI</td>
    <td>SEQ/VAB</td>
    <td>Yes (Extraction Only)</td>
    <td>Includes various PSF utilities. I prefer using PSF Data Finder for extracting VAB.</td>
  </tr>
  <tr>
    <td><a href="https://www16.atwiki.jp/soundfile/pages/6.html#id_574b7125">bin2seq</a></td>
    <td>♥</td>
    <td>Anonymous</td>
    <td>MS-PL</td>
    <td>CLI</td>
    <td>SEQ/VAB, SSSQ/SSHD, KCET, SNTP, SQV, SEQQ and more (see Readme.txt)</td>
    <td>Yes (Extraction Only)</td>
    <td>Scanning tool for extracting various sound sequence formats.</td>
  </tr>
  <tr>
    <td><a href="https://www16.atwiki.jp/soundfile/pages/6.html#id_574b7125">PGconv</a></td>
    <td></td>
    <td>tamogami</td>
    <td>Not Specified (Closed Source)</td>
    <td>GUI</td>
    <td>SEQ/VAB and few others</td>
    <td>Yes</td>
    <td>Classic Win32 application often used by Japanese researchers.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/ValleyBell/MidiConverters">seq2mid</a></td>
    <td></td>
    <td>ValleyBell</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>SEQ</td>
    <td>No</td>
    <td>SEQ to MIDI converter with some advanced options, including volume conversion and instrument remapping. No precompiled binary.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/loveemu/seq2mid">seq2mid</a></td>
    <td></td>
    <td>loveemu</td>
    <td>MIT License</td>
    <td>CLI</td>
    <td>SEQ and Dragon Quest SSEQ</td>
    <td>No</td>
    <td>Simple SEQ to MIDI converter, with no special options.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/ValleyBell/MidiConverters">AKAO2MID</a></td>
    <td></td>
    <td>ValleyBell</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>AKAO v1 and v2</td>
    <td>No</td>
    <td>Square AKAO sequence to MIDI converter. No precompiled binary.</td>
  </tr>
  <tr>
    <td><a href="https://github.com/loveemu/loveemu-lab/tree/master/ps1/dmfMus">dmfMus</a></td>
    <td></td>
    <td><a href="https://github.com/loveemu">loveemu</a></td>
    <td>MIT License</td>
    <td>CLI</td>
    <td>Natsume's PAC Sound Archive</td>
    <td>Yes</td>
    <td>Byproduct of <a href="https://github.com/loveemu/psf-drivers/blob/master/psf/natsume/hokuto/SLPS_02993.md">creating Hokuto no Ken PSF</a>. Not very user-friendly.</td>
  </tr>
</table>

By the way, [jPSXdec](https://github.com/m35/jpsxdec) is good for extracting audio/video resources. It's [free for non-commercial use](https://github.com/m35/jpsxdec/blob/readme/.github/LICENSE.md).

TODO:

* [sssq2mid](https://www16.atwiki.jp/soundfile?cmd=upload&act=open&pageid=6&file=Sssq2mid.7z) (for games developed by Sony)
* [sqv2mid](https://www16.atwiki.jp/soundfile?cmd=upload&act=open&pageid=6&file=Sqv2mid.7z) (for Brave Fencer Musashiden)

## Playstation 2

Try [VGMTrans](https://github.com/vgmtrans/vgmtrans) and [VGMToolbox](https://sourceforge.net/projects/vgmtoolbox/) in the same way as Playstation. That should be enough for you, if the game uses the standard SQ/HD/BD data. Those tool can read [PSF2](http://www.vgmpf.com/Wiki/index.php?title=PSF2), the portable sound format for Playstation 2.

## Playstation Portable

You can extract MID/PHD/PBD files by PSP Data Finder of [VGMToolbox](https://sourceforge.net/projects/vgmtoolbox/).

PSFP is a portable sound format for Playstation Portable. You may find [further informations about PSFP](https://hcs64.com/mboard/forum.php?showthread=19333&showpage=0#post_48951) on HCS forum.

## Retouching Tools

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Author</th>
    <th>License</th>
    <th>GUI/CLI</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/gocha/midisplit">MidiSplit</a></td>
    <td>♥</td>
    <td><a href="https://github.com/gocha">gocha</a></td>
    <td>MIT License</td>
    <td>CLI</td>
    <td>Command-line tool that splits single track into each tracks according to instruments.</td>
  </tr>
  <tr>
    <td><a href="http://zex0.web.fc2.com/">SmfExTime</a></td>
    <td></td>
    <td>ZEX</td>
    <td>Not Specified (Source Code Available)</td>
    <td>CLI</td>
    <td>Command-line tool that flexibily scales timebase and tempo with keeping actual song speed. Usually used for correcting the tempo of MIDI data dumped by emulators.</td>
  </tr>
</table>

## VST/AU Plug-ins for DAW

### Soundfont Player

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Developed by</th>
    <th>Platform</th>
    <th>Pricing</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://www.plogue.com/products/sforzando.html">sforzando</a></td>
    <td>♥</td>
    <td><a href="https://www.plogue.com/">Plogue</a></td>
    <td>Windows, macOS</td>
    <td>Free</td>
    <td>Powerful SFZ player with SF2 import feature.</td>
  </tr>
</table>

### Chip Emulator/Simulator

<table>
  <tr>
    <th>Application</th>
    <th>♥</th>
    <th>Developed by</th>
    <th>Platform</th>
    <th>Pricing</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://www.plogue.com/products/chipsynth-sfc.html">chipsynth SFC</a></td>
    <td>♥</td>
    <td><a href="https://www.plogue.com/">Plogue</a></td>
    <td>Windows, macOS</td>
    <td>$39.95</td>
    <td>A bit accurate recreation of the Super Famicom (SNES) unique sound playback capabilities inside an easy to use and powerful virtual synthesizer. The plug-in has a built-in SPC player, which works very well with the instrument editor.</td>
  </tr>
  <tr>
    <td><a href="https://www.plogue.com/products/chipsynth-md.html">chipsynth MD</a></td>
    <td>♥</td>
    <td><a href="https://www.plogue.com/">Plogue</a></td>
    <td>Windows, macOS</td>
    <td>$49.95</td>
    <td>A bit accurate recreation of the Mega Drive (Genesis) audio capabilities inside an easy to use and powerful virtual synthesizer. The plug-in has a built-in VGM player, which works very well with the instrument editor.</td>
  </tr>
  <tr>
    <td><a href="https://www.plogue.com/products/chipsounds.html">chipsounds (Legacy)</a></td>
    <td></td>
    <td><a href="https://www.plogue.com/">Plogue</a></td>
    <td>Windows, macOS</td>
    <td>$95</td>
    <td>8-bit soft synthesizer. Features chips like the NES, Atari ST, ZX Spectrum 128, Nintendo Game Boy, Commodore 64 and VIC-20, Atari 400/800 and 2600.</td>
  </tr>
  <tr>
    <td><a href="http://picopicose.com/software.html">C700</a></td>
    <td></td>
    <td><a href="https://github.com/osoumen">osoumen</a></td>
    <td>Windows, macOS</td>
    <td>Free</td>
    <td>Sampler that emulates SNES S-DSP. By the way, you may want to check <a href="https://github.com/osoumen/dpcmc">dpcmc</a> from the same author, if you want a NES DPCM converter.</td>
  </tr>
  <tr>
    <td><a href="http://www.alyjameslab.com/alyjameslabfmdrive.html">FMDrive</a> and <a href="http://www.alyjameslab.com/alyjameslabsuperpsg.html">Super PSG</a></td>
    <td></td>
    <td><a href="http://www.alyjameslab.com/">Aly James Lab</a></td>
    <td>Windows</td>
    <td>€10+</td>
    <td>Virtual synthesizer instruments for Sega game consoles. VST bridge is required for 64bit DAW.</td>
  </tr>
</table>

### Other Instruments

<table>
  <tr>
    <th>Application</th>
    <th>Developed by</th>
    <th>Platform</th>
    <th>Pricing</th>
    <th>Note</th>
  </tr>
  <tr>
    <td><a href="https://github.com/m-masaki72/SANA_8BIT_VST">SANA 8BIT VST</a></td>
    <td><a href="https://github.com/m-masaki72">Masaki Mori</a></td>
    <td>Windows, macOS</td>
    <td>Free (GPLv3)</td>
    <td>Simple waveform synthesizer for chiptune, having pitch sweep function, vibrato function and wave scope.</td>
  </tr>
  <tr>
    <td><a href="https://impactsoundworks.com/product/super-audio-cart/">Super Audio Cart</a></td>
    <td><a href="https://impactsoundworks.com/">Impact Soundworks</a></td>
    <td>Kontakt Player</td>
    <td>$149</td>
    <td>Sample library that features eight legendary systems: NES, FC, SNES, GB, 2600, C64, SMS, GEN. Includes standalone SNESVerb plugin. Easy-to-use UI.</td>
  </tr>
  <tr>
    <td><a href="https://www.roland.com/global/products/sound_canvas_va/">Sound Canvas VA</a></td>
    <td><a href="https://www.roland.com/">Roland</a></td>
    <td>Windows, macOS</td>
    <td>$125</td>
    <td>Virtual instrument of legendary '90s synthsizer. You might want to subscribe <a href="https://www.rolandcloud.com/">Roland Cloud</a> if you want more Roland synths.</td>
  </tr>
  <tr>
    <td><a href="https://korg.shop/software/korg-collection-series/korg-collection-m1.html">KORG Collection - M1</a></td>
    <td><a href="https://www.korg.com/">Korg</a></td>
    <td>Windows, macOS</td>
    <td>$49.99</td>
    <td>Virtual instrument of legendary '90s synthsizer. Full bundle of KORG Collection has more synths.</td>
  </tr>
  <tr>
    <td><a href="https://www.uvi.net/vintage-synth/digital-synsations.html">Digital Synsations</a></td>
    <td><a href="https://www.uvi.net/">UVI</a></td>
    <td>Windows, macOS</td>
    <td>$149</td>
    <td>Virtual 90's synthesizers instruments. Features the Korg M1, Ensoniq VFX, SY77 and D50.</td>
  </tr>
  <tr>
    <td><a href="http://www.creative.com/emu/proteusvx/">Proteus VX</a></td>
    <td>E-mu</td>
    <td>Windows</td>
    <td>Free</td>
    <td>Virtual instrument of legendary '90s synthsizer. VST bridge is required for 64bit DAW.</td>
  </tr>
</table>

## Community

* [HCS Forum](https://hcs64.com/mboard/forum.php)
* [HCS Discord Server](https://discord.gg/7ddT4pP)

## Credits

* [内蔵音源midi変換まとめ - 【聞き専】内蔵音源の曲データ倉庫【sound file】 - アットウィキ](https://www16.atwiki.jp/soundfile/pages/56.html)
