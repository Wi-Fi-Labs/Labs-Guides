# Dumping 3DS Data

The various guides listed below have the purpose of teaching you how to dump varied data from your 3DS for use with an emulator like Citra or Lime3DS, such as game carts, game/update/dlc titles, system files, save data & more.<br>
It is assumed here you already have a 3DS with CFW and that you have GodMode9 updated to the latest version in said console.<br>
If you don't have either, make sure to check out these [3DS CFW](https://3ds.hacks.guide/) & [GodMode9](https://3ds.hacks.guide/godmode9-usage) guides first.<br>

Citra & Lime3DS can run many games without needing to do any special work on a physical 3DS. However, some games, such as Pokémon, _may_ require some system files dumped from a 3DS in order to function properly.<br>

These files are copyrighted and are not allowed to be shared, so dumping them from your own 3DS is the only way to legally obtain them. If you do not own a 3DS to dump the files from, you are out of luck.<br>

There are 2 ways to import/dump digital files to use with Citra or Lime3DS: one is using zhaowenlan1779's `threeSD` program; the other is using several 3DS Homebrew tools to dump what you may require.

## Importing Data with threeSD

[threeSD](https://github.com/zhaowenlan1779/threeSD) is a tool written to help import data from your 3DS for Citra/Lime3DS more conveniently.

Refer to threeSD's [Quickstart Guide](https://github.com/zhaowenlan1779/threeSD/wiki/Quickstart-Guide) for importing your installed titles, updates, DLCs, save data, extra data, system files, etc. 

# Dumping Data with 3DS Homebrew apps

All guides listed below require you to have either an SD card reader or a way to transfer files to and from your 3DS and PC wirelessly - using [ftpd](https://github.com/mtheall/ftpd) on 3DS and any FTP client on PC for example.

## Dumping a Game Cartridge from a 3DS Console
_This guide is courtesy of Nintendo Homebrew_
- Insert the game cartridge you intend to dump into your console
  - 3DS game cartridges will be dumped to a `.3ds`format
  - NDS game cartridges will be dumped to a `.nds` format
- Press and hold (Start), and while holding (Start), power on your console. This will launch GodMode9
- Navigate to `[C:] GAMECART`
- For 3DS carts:
  - Press (A) on `[TitleID].trim.3ds` to select it
  - Select `NCSD Image Options` and then select "Decrypt File (0:/gm9/out)"
- For NDS carts:
  - Press (A) on `[TitleID].nds` to select it - _Trimmed dumps are not recommended for NDS games in general, as they can cause various playback issues_
  - Select “Copy to 0:/gm9/out”
- Your non-installable `.3ds` or `.nds` formatted file will be outputted to the `/gm9/out/` folder on your SD card

_Note: To dump SM or USUM a 4GB SD card might not be enough so it is recommended that you have an 8GB card or larger to dump these games_

## Dumping an Installed or System Title from a 3DS Console
_This guide is courtesy of Nintendo Homebrew_
- Press and hold (Start), and while holding (Start), power on your console. This will launch GodMode9
- Press (Home) to bring up the action menu
- Select “Title manager”
- Select one of the following depending on the type of title you wish to dump:
  - User Installed Title: `[A:] SD CARD`
  - System Title / DSiWare: `[1:] NAND / TWL`
- Select the title you wish to dump
- Select “Manage Title…”
- Select “Build CIA (standard)”
- Your installable `.cia` formatted file will be outputted to the `/gm9/out/` folder on your SD card

## Dumping Update Data from a 3DS Console
- Press and hold (Start), and while holding (Start), power on your console. This will launch GodMode9
- Navigate to `A: SYSNAND SD>title>0004000e>game title id` - see [here](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/3DS/CitraSetup.md#final-setup) for Pokemon games' title ID list
- In your respective game's folder, navigate further into `content>00000004.app`
- Once that .app is open, select `NCCH image options...>Build .cia from file`
- Your installable `.cia` formatted file will be outputted to the `/gm9/out/` folder on your SD card

## Dumping Save Data & Extra Data from a 3DS Console
_This guide was originally written by the Citra Development team_<br><br>
For this guide you will require the Homebrew app [Checkpoint](https://github.com/BernardoGiordano/Checkpoint) save manager if you don't have it installed yet.<br>
Save data lives in Citra’s emulated SD card directories `(user/sdmc/Nintendo 3DS/000...0/000...0/title/[game-TID-high]/[game-TID-low]/data/00000001/)`.<br>
In addition to save data, some games and system applications use extra data. Game extra data is stored on the SD card and can be extracted and used by Citra.<br>
To dump and transfer Save data or Extra Data:
- Open Checkpoint. If this is the first time launching Checkpoint, it may take a considerably longer than usual depending on the amount of installed titles.
- Highlight the game you want to dump save or extra data of by navigating to it with the D-pad.
- Press A and select `Backup` on the bottom screen. You will be prompted `Yes` or `No`. Select `Yes` by pressing A.
- You will have the option to name the save folder. Name it whatever you want or use the name given to it. Press `OK` on the bottom screen.
- The top screen will flash a message `Success! Progress correctly saved to disk`. Exit out of Checkpoint.
- **For Save Data** transfer all files located in `/3ds/Checkpoint/saves/[Game Name]/[Folder created in Step 4]` to the computer.
  - Place the files in Citra’s emulated SD card’s save directory. You can open the save directory by right-clicking on a game in Citra and clicking “Open Save Data Directory”. If the directory doesn’t exist, start the game once and the directory will be created.
- **For Extra Data** transfer all files located in `/3ds/Checkpoint/extdata/[Game Name]/[Folder created in Step 4]` to the computer.
  - Place the files in Citra’s emulated SD card’s extra data directory. You can open the extra data directory by right-clicking on a game in Citra and clicking “Open Extra Data Directory”, and you should put the files inside the `user` folder. These directories may have to be created if the title the extra data was dumped from has not been played in Citra yet. 

## Dumping System Archives & Shared Fonts
_This guide was originally written by the Citra Development team_<br><br>
For this guide you will require the Homebrew app [3dsutils](https://github.com/ahmubashshir/3ds-utils) if you don't have it installed yet - you can find [here](https://cdn.discordapp.com/attachments/242442830486700045/357712552999911424/3dsutils-master-f73f28f.3dsx) an unofficial compiled version.<br>
To dump and transfer System Archives & Shared Fonts:
- Run `3dsutils` via the homebrew launcher.
- Press A when prompted to begin. The system archives will be dumped. Wait for the process to finish, then press A when prompted to be taken back to the homebrew launcher.
- There will now be a `3dsutils` folder at the root of the 3DS’s SD card. Inside that folder is a folder `nand`. Transfer the folder `nand` to the User Directory. The folder will merge with the existing `nand` folder contained therein. If prompted to overwrite any files, say yes.

***
For more misc Dumping guides check out [3DS Homebrew](https://3ds.hacks.guide/dumping-titles-and-game-cartridges) or [Lime3DS Wiki](https://lime3ds.github.io/pages/wiki.html)

_The contents of this guide were all written by SexyMalasada except where noted otherwise._
