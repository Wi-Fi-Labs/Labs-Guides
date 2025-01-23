# Citra & Lime3DS Setup & Configuration Guide

This guide aims to be a simple step-by-step set of instructions to configure and setup Citra or Lime3DS for ease of access to its in-depth folders where stuff like savefiles, ips patches etc are stored.<br>
It will also prepare your setup for later ease of installation of PokeReader, which is the recommended assisted tool for 3DS RNG.<br>
_Italicized steps_ in the guides below means that step is optional!<br>
At the end you also have an in-depth explanation of how Citra/Lime3DS's User Directory is arranged and what each folder contains, should you wish to learn more.<br><br>
This guide assumes you have already dumped your own games and update data to use with the emulator. If you haven't done so yet and you need instructions on how to, check out [this guide](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/3DS/Dumping3DSData.md)

## Citra & Lime3DS Setup for Pokemon RNG Guide

### Initial Setup
- Download and extract the latest release .zip from either [Citra](https://github.com/PabloMK7/citra/releases) or the [Lime3DS](https://github.com/Lime3DS/lime3ds-archive/releases) repos.
- Create a folder in your PC wherever you want to have Citra or Lime3DS installed - it is recommended that this folder be outside the standard `Program Files` folder. You can name this folder as you wish (for the purpose of this guide I will be naming mine `CITRA`).
- Copy the folder you extracted from the .zip (example for this guide's purpose: `citra-windows-msvc-xxxx`) into the new folder you created in the previous step. Make sure to copy the 2nd tier folder and not the 'first layer' one - You should have a layout like `CITRA\citra-windows-msvc-xxxx\(several folders, dll, exe files etc)` once you're done.
- _Create a folder inside `CITRA` to place your dumped game ROMs in. You can name it as you wish._
- Create a folder inside `citra-windows-msvc-xxxx` named `user`; then inside that create 2 new folders named `nand` and `sdmc` respectively.
- Inside the `sdmc` folder you just created, create a new folder named `luma`.
- _In `citra-windows-msvc-xxxx`, create a shortcut for the `citra-qt.exe` or `lime3ds-gui.exe` app file. You can name the shortcut whatever you prefer. Then move this shortcut into the base ``CITRA`` folder; or wherever else you'd like to conveniently access the emulator app directly!_
- Once all of the above steps are done, you can now open Citra or Lime3DS for the first time - you can try to do so via your shortcut if you created one!
### In-App Setup
What we will now do is reconfigure the location of the User Directory for ease of access, among other miscellaneous settings in the app
- Once you have the emulator open, navigate to `Emulation>Configure>System>Storage` and check ✅ the 'use custom storage' option. After this select a new location for both the `nand` and `sdmc` folders - assign the respective paths to the ones you created inside the `user` folder in one of the steps above.
- This is a good time to also change/assign any hotkeys and controls you might want to; I especially recommend at least changing the D-Pad control keys to differ from the Circle Pad ones, for ease of usage with PokeReader once you install that later on! This can be done in `Emulation>Configure>Controls`.
- Add a ROMs directory to the emulator - just press the folder icon in its main window and it'll prompt you to pick a folder.
- Install the update .cia for each of your games via `File>Install cia`. If you've dumped and installed the updates correctly, your games should now have `ver 1.x` on top of their icon.
- Open any one of the games you now have available in your list. After opening the game, you can now close it - this is only done in order to create the saves folder. You can now close the emulator.
### Final Setup
- Navigate to the saves folder in order to create a shortcut for it for future ease of access - it can be found in `C:...CITRA\citra-windows-msvc-xxxx\user\sdmc\Nintendo 3DS\00000000000000000000000000000000\00000000000000000000000000000000\title\00040000`
- Make a shortcut of the `00040000` folder, rename it to 'Saves' or something else you prefer, and move that shortcut into your main `CITRA` folder - congrats you now have easy access to your saves!
- To be sure of what folder corresponds to which game inside the saves folder, copy or make note of the `title ID` list below somewhere. The saves will be located inside each `title ID` named folder followed by 2 more folders (example `001b5100\data\00000001`), where a `main` file will be placed - this `main` file is your save file, that you can then copy to your 3DS and restore to a cart with a save manager and vice-versa.
  - `001b5000` Pokemon Ultra Sun
  - `001b5100` Pokemon Ultra Moon
  - `0011c400` Pokemon Omega Ruby
  - `0011c500` Pokemon Alpha Sapphire
  - `00055d00` Pokemon X
  - `00055e00` Pokemon Y
  - `00175e00` Pokemon Moon
  - `00164800` Pokemon Sun

# Citra & Lime3DS User Directory explanation in detail
_This Diagram and in-depth explanation was originally written by the Citra Development team_<br><br>
Diagram of the User Directory:
```bash
"User directory"
├── config
├── nand
│   ├── 00000000000000000000000000000000 (optional)
│   └── data
│       ├── sysdata
│       └── extdata
├── sdmc
│   └── Nintendo 3DS
│       ├── 00000000000000000000000000000000
│       |   └── 00000000000000000000000000000000
│       |       ├── title
│       |       └── extdata
│       └── Private
└── sysdata (optional)
    └── aes_keys.txt (optional)
    └── seeddb.bin (optional)
```

## config
This directory contains files containing information that tell Citra how to run. These files are in plain text and thus are fully editable and contain configurations for mapping controls, which CPU and audio engine to use, rendering and other visual options, the Log Filters, which region the emulated 3DS belongs to, whether to treat the emulated 3DS as a new 3DS, and whether to insert a virtual SD card into the emulated system.<br>
Changing these files is only to be done by advanced users because making changes at random can cause Citra not to work as expected or at all. The Citra executable has options menus that allow users to change most of the aforementioned configurations safely. If Citra has trouble running after changing a file and the user cannot remember what they changed, delete the configuration files and run the executable again so that they are regenerated automatically (albeit as though Citra is being run for the first time so any existing configurations are lost).

## log
This directory contains `citra_log.txt`. This file is automatically generated by Citra and stores the logging. It is overwritten every time Citra is launched.

## nand
This directory is the emulated 3DS system NAND. It does not match an actual console’s NAND exactly due to differences between Citra and a physical 3DS. This directory will contain the `data` directory and potentially also the system archives.<br>

### data
This directory is automatically generated by Citra and contains the system and extra data for the emulated NAND. Inside this directory is another directory, `00000000000000000000000000000000`. On a physical 3DS, the directory inside `data` would be named differently. Its name would be 32 characters long and made of hexadecimal characters (0-9 and A-F) instead of it being all 0’s like Citra. This knowledge is only important if you plan on dumping any NAND system data or extra data from a physical 3DS and associating it with Citra. The `00000000000000000000000000000000` contains two folders, `extdata`, containing NAND extra data, and `sysdata`, containing NAND system save data.<br>

#### sysdata
System save data is identified by a title ID, separated into TID High, the first 8 characters of the title ID, and TID Low, the last 8 characters of the title ID. Most system save data has a TID high of 00000000. An individual piece of system save data is stored in `sysdata/[TID Low]/[TID High]`. For details about the different kinds of system save data, see [3dbrew](https://3dbrew.org/wiki/System_SaveData). For first-time Citra users, there may be nothing inside the `sysdata` directory. In fact this will be the case for most Citra users, and is nothing to be alarmed about. This data will be created automatically in some cases, such as when a Mii is saved in Mii Maker. Almost none of this data is essential for Citra to run homebrew games or backups of licensed titles.<br>
There is one notable exception to the last statement. Citra requires a dump of a physical 3DS’s config savegame in order to run a small number of games. To obtain the config savegame from a 3DS console use and follow the instructions for importing it with `threeSD` [here](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/3DS/Dumping3DSData.md#importing-data-with-threesd).<br>
Other system save data aside from the config savegame can be dumped from a 3DS console by an expert user and placed in the `sysdata` folder. At this time, though, many features that read from or write to system save data have not been implemented so there is currently little value in doing so.

#### extdata
NAND extra data always has a TID High of 00048000, so the `extdata` directory should contain a `00048000` folder, though it has been observed in Citra that there may be a `00000000` folder instead, and users have reported issues if there is both a `00000000` and `00048000` folder contained therein, so it is advised to delete the `00000000` folder if that is the case. Inside the folder may be nothing, or it may contain one or more directories named `F000000#`, where # can be the characters A-F or the numbers 0-9. Each of these folders corresponds to a TID low, which can be used to identify the type of extra data stored therein. See [3dbrew](https://www.3dbrew.org/wiki/Extdata?section=13#NAND_Shared_Extdata) for details about the different kinds of extra data stored in NAND.

#### system archive
This folder, named `00000000000000000000000000000000`, will only exist if the system archives have been dumped from a physical 3DS. The system archives are required for some games to work with Citra. To obtain the system archives, follow the instructions located at [Dumping System Archives & Shared Fonts](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/3DS/Dumping3DSData.md#dumping-system-archives--shared-fonts) from a 3DS Console.

## sdmc
This directory is the equivalent of the SD card inserted into a physical 3DS, which stores game save, extra data and any titles installed to the SD card in encrypted format. Inside the `sdmc` folder, just like on a real 3DS console, is a `Nintendo 3DS` directory, which contains two more directories, `Private` and `00000000000000000000000000000000`.

### Private
The `Private` directory on a real 3DS contains camera data (in `00020400/phtcache.bin`) and sound data (in `00020500/voice/...`). Citra will create camera data while it is running. If a user wants to copy their camera and sound data to Citra, they can do so easily by copying the `Private` folder from their SD card and overwriting Citra’s, but at this time there is no value in doing so.

### 00000000000000000000000000000000
This directory contains another directory of the same name, and inside of that is where game saves (in the `title` directory) and extra data (in the `extdata` directory) can be found. On a real SD card, there would not be two `00000000000000000000000000000000` folders, but instead the folders would be named as hexadecimal characters corresponding to a 3DS console ID. If a user wishes to extract save or extra data from their physical console, they do not need to worry about the console ID not matching Citra’s `00000000000000000000000000000000` folders.

#### title
If any games have been saved while playing them with Citra, there should be a folder inside `sysdata` named `00040000`. This folder contains all of the save data for 3DS titles. It is entirely possible to retrieve save data from an SD card using a physical 3DS console and import it into Citra to continue a game where it was last left off on the console. On a real SD card, the `sysdata` folder will also contain the files required to run any 3DS titles installed to the SD card. This can be mimicked somewhat by Dumping Installed Titles and importing them into Citra’s `sysdata` directory but this is unnecessary since Citra can run them from anywhere on a computer filesystem and doesn’t require the accompanying .tmd and .cmd files.<br>
On a real SD card, there may be two other directories inside `sysdata`. These directories are named `0004000e` and `0004008c` and correspond to downloaded game updates and DLC respectively. The data contained within these directories can be backed up on a computer as decrypted CIA files and installed with Citra (see [Dumping Update Data from a 3DS Console](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/3DS/Dumping3DSData.md#dumping-update-data-from-a-3ds-console)).

#### extdata
This directory contains all of the extra data created when playing 3DS game backups. Citra emulates a console’s behaviour of reading from and writing to extra data, so this data can be dumped from an SD card using a physical 3DS console and imported into Citra.

#### other folders
If a real SD card is compared to Citra’s emulated SD card, Citra may appear to be missing one or more folders present on the real SD card: `dbs`, `backups`, and `Nintendo DSiWare`. The `dbs` folder contains a 3DS console’s title database. The `backups` folder contains saved data backed up via the Home Menu. The `Nintendo DSiWare` folder contains exported DSi exports. Citra does not need any of these folders so there is currently no value in dumping them.

## sysdata
This directory can contain two files:

- `shared_font.bin`: this was a legacy system font data dumped from old versions of `3dsutils` and is no longer supported. If the user does not have shared font installed, Citra will use the open source font replacement instead. Users should re-dump their shared font since the open source font replacement may not always look accurate. See [Dumping System Archives & Shared Fonts](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/3DS/Dumping3DSData.md#dumping-system-archives--shared-fonts) for more information.
- `aes_keys.txt`: this file holds decryption keys
- `seeddb.bin`: SeedDB used for seed crypto & FS SeedDB functions

***
_The contents of this guide were all written by SexyMalasada except where noted otherwise._
