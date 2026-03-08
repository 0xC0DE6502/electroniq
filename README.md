# Electroniq

Acorn Electron emulator by [0xC0DE](https://x.com/0xC0DE6502).  

_Note: this is a quick Readme for a work in progress. It is not a full user guide._

## Quickstart

1. Read this entire Readme, especially the [disclaimer](#disclaimer) and [LICENSE.txt](https://github.com/0xC0DE6502/electroniq/blob/main/LICENSE.txt).
2. Open [https://0xC0DE6502.github.io/electroniq](https://0xC0DE6502.github.io/electroniq).
3. Click in the browser window to enable audio.
4. Load any tape (UEF), disk (SSD/DSD), sdcard (MMB) or text (TXT) file.
5. Enjoy the emulator by playing games, creating your own programs, etc.

_Disks and sdcards can be modified and saved. Tapes are read-only!_

### Loading files

There are currently 4 ways to load files into Electroniq:
1. Use the menu: _File | Insert_, _File | Import | Text..._
2. Drag and drop files into the emulator window
3. Use URL parameters (see below)
4. Quickly play a game: _File | Quick play_

_Note: when you load a large file, it may take a few moments for the file to finish loading and become available._

### URL parameters

By default, Electroniq emulates a standard Acorn Electron with 2 disk drives (40/80T, SSD/DSD). Both disk drives are write-protected unless you explicitly disable that in the menu. You configure and expand the system with the following URL parameters:

| Option | Description |
|-|-|
| `tape=`_URL_ | insert tape (UEF file) |
| `disk0=`_URL_ | insert disk (SSD/DSD file) in drive 0 |
| `disk1=`_URL_ | insert disk (SSD/DSD file) in drive 1 |
| `sdcard=`_URL_ | insert sdcard (MMB file) |
| `text=`_URL_ | import text (TXT file) via 'turbo pasting' |
| `text-delay=`_INT_ | set delay before 'turbo pasting' text |
| `autoboot` | automatically boot disk in drive 0 |
| `plus1` | load Plus 1 Expansion 1.00 in ROM bank C |
| `dfs` | load ACP 1770 DFS 2.20 in RAM bank 3 |
| `mmfs` | load MMFS 1.55 in RAM bank E |
| `romX=`_URL_ | load file into ROM bank 0..7, C..F |
| `ramX=`_URL_ | load file into RAM bank 0..7, C..F |
| `cmd=`_STR_ | execute commands at startup |
| `cmd-delay=`_INT_ | set delay before executing commands |

When no URL is specified, the currently inserted medium is ejected or the bank is cleared. Only URLs that link to raw GitHub files have been tested so far. The format of such a URL is: htt<area />ps://0xC0DE6502.github.io/electroniq?disk0=htt<area />ps://raw.githubusercontent.com/_USER_/_REPO_/_BRANCH_/_DISK_

Some examples to get you started:

* [https://0xC0DE6502.github.io/electroniq?dfs&autoboot&disk0=https://raw.githubusercontent.com/0xC0DE6502/flappy-bird-releases/main/flappy-bird.ssd](https://0xC0DE6502.github.io/electroniq?dfs&autoboot&disk0=https://raw.githubusercontent.com/0xC0DE6502/flappy-bird-releases/main/flappy-bird.ssd)
* [https://0xC0DE6502.github.io/electroniq?tape=https://raw.githubusercontent.com/0xC0DE6502/electrobots-releases/main/electrobots.uef&cmd=*TAPE/RCHAIN/D/D/R&cmd-delay=30](https://0xC0DE6502.github.io/electroniq?tape=https://raw.githubusercontent.com/0xC0DE6502/electrobots-releases/main/electrobots.uef&cmd=*TAPE/RCHAIN/D/D/R&cmd-delay=30)

The string following `cmd=` can be URL-encoded, or you can use the following special characters:
* // = slash (/)
* /R or /r = carriage return
* /D or /d = double quote (")
* /S or /s = space
* /P or /p = percent (%)

Examples:
* [https://0xC0DE6502.github.io/electroniq?cmd=10P./DHello!/S/D;/R20G.10/RRUN/R](https://0xC0DE6502.github.io/electroniq?cmd=10P./DHello!/S/D;/R20G.10/RRUN/R)
* [https://0xC0DE6502.github.io/electroniq?cmd=AUTO%0AP.%22Hello%21%20%22%3B%0AG.10%0A%1BRUN%0A](https://0xC0DE6502.github.io/electroniq?cmd=AUTO%0AP.%22Hello%21%20%22%3B%0AG.10%0A%1BRUN%0A)


## Other things to know

Electroniq needs to run at a comfortable 50fps in your browser to work correctly. All (special) browser keys are intercepted and forwarded to Electroniq, including the keys you may want to use to adjust the zoom level of your browser window. Current workaround: click in the address bar of your browser and use `CTRL` + `-` and `CTRL` + `+` to adjust the zoom level.  

### Switching between filing systems
When multiple filing systems are active, you can switch between them with:
* `*TAPE` to switch to CFS (tape)
* `D` + `BREAK` to switch to DFS (disk)
* `*MMFS` to switch to MMFS (sdcard)

### Save early, save often
Nothing you upload is stored on a server, it is all kept in temporary (!) browser memory. That also means you lose all **unsaved** data when you refresh or close the browser window! When you save/export (download) a file (disk, sdcard, screenshot, or your BASIC program as text), it may appear directly in your Downloads folder, without showing a Save Dialog first. This is a browser setting.  

### Turbo pasting

'Turbo pasting' allows you to quickly import a text file via _File | Import | Text..._. When at the BASIC prompt, this rapidly enters your BASIC program. When working in VIEW, this rapidly enters your document. And so on. Press `ESCAPE` or `BREAK` to interrupt turbo pasting.

### Exporting your BASIC program
Use _File | Export | BASIC..._ to instantly export your BASIC program (at `PAGE`) as a text file. Enable _Settings | CR/LF as newline_ if you need CR/LF (0D/0A) instead of just LF (0A) as newlines in your exported text file.

### Exporting RAM
Use _File | Export | RAM..._ to instantly export the entire 32K of RAM as a binary file.

## Credits and licenses

Electroniq uses the following open source libraries and components:
* [raylib](https://www.raylib.com)
* [Dear ImGui](https://www.dearimgui.com)
* [imgui_memory_editor](https://github.com/ocornut/imgui_club?tab=readme-ov-file#imgui_memory_editor)
* [rlImGui](https://github.com/raylib-extras/rlImGui)
* [DejaVu Sans Mono Bold TrueType Font](https://github.com/dejavu-fonts/dejavu-fonts)
* [6502 core](https://github.com/floooh/chips/blob/master/chips/m6502.h)
* [Tiny File Dialogs](https://sourceforge.net/projects/tinyfiledialogs)
* [miniz](https://github.com/richgel999/miniz)
* [libyuarel](https://github.com/jacketizer/libyuarel)
* [argparse](https://github.com/cofyc/argparse)
* [cJSON](https://github.com/DaveGamble/cJSON)
* [OpenSSL](https://github.com/openssl/openssl)
* [curl](https://github.com/curl/curl)
* [libwebsockets](https://github.com/warmcat/libwebsockets)
* [libretro.h](https://github.com/libretro/libretro-common/blob/master/include/libretro.h)
* [cacert.pem](https://curl.se/docs/caextract.html)

See also: [LICENSE.txt](https://github.com/0xC0DE6502/electroniq/blob/main/LICENSE.txt)

## Disclaimer

This is an experimental **work in progress**.  
Expect timing issues, inaccuracies and data loss. Use at your own risk.  
Things can and will break, change, or even be completely unavailable at any time and without notice.  

---

Electroniq - Copyright (C) 2024-2026 [0xC0DE](https://x.com/0xC0DE6502). All rights reserved.
