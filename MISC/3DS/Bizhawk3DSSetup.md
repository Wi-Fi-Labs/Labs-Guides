# Bizhawk 3DS Setup & Configuration Guide

This guide aims to be a simple step-by-step set of instructions to configure and setup Bizhawk's 3DS Encore core for ease of access to its in-depth folders where stuff like savefiles are stored.<br>
It will also prepare your setup for later ease of installation of PokeReader, which is the recommended assisted tool for 3DS RNG.<br>
This guide assumes you have already dumped your own games and update data to use with the emulator. If you haven't done so yet and you need instructions on how to, check out [this guide](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/3DS/Dumping3DSData.md)

## Bizhawk 3DS Setup for Pokemon RNG Guide

[BizHawk 2.10](https://github.com/TASEmulators/BizHawk/releases/tag/2.10) added a 3DS core (named Encore), which means 3DS emulation (and RNG abuse) is now supported on its platform.<br>

### Setup
- Boot the official Updates first (.cia files), BizHawk will 'crash' afterwards but this is normal; it should still install the patches (ie. XY on 1.5, USUM on 1.2).
- Boot the game; this'll create a 3DS directory in your main BizHawk folder if it didn't exist yet.
- Put [PokeReader's](https://github.com/zaksabeast/PokeReader) `default.3gx` file in the following directory (create the directories if they don't exist): `C:\...BizHawk\3DS\User\sdmc\luma\plugins`.
- Circle pad controls can only be done via analog controls, so that means you'll need to use an external device like a controller to make use of them - This is essential for Gen 7 games and advised for Gen6 as well, since PokeReader controls use the D-Pad keys.

luascripts could be used in the future.

Directories are:
- Config: (if using your 3DS's own dumped configs - for making use of the geolocations): `C:\...BizHawk\3DS\User\nand\data\00000000000000000000000000000000\sysdata\00010017\00000000`
- Save file locations: `C:\...BizHawk3DS\User\sdmc\Nintendo 3DS\00000000000000000000000000000000\00000000000000000000000000000000\title\00040000`
- To be sure of what folder corresponds to which game inside the saves folder, copy or make note of the `title ID` list below somewhere. The saves will be located inside each `title ID` named folder followed by 2 more folders (example `001b5100\data\00000001`), where a `main` file will be placed - this `main` file is your save file, that you can then copy to your 3DS and restore to a cart with a save manager and vice-versa.
  - `001b5000` Pokemon Ultra Sun
  - `001b5100` Pokemon Ultra Moon
  - `0011c400` Pokemon Omega Ruby
  - `0011c500` Pokemon Alpha Sapphire
  - `00055d00` Pokemon X
  - `00055e00` Pokemon Y
  - `00175e00` Pokemon Moon
  - `00164800` Pokemon Sun

### Emulator Settings
When booting BizHawk, make sure to change the following default settings in `3DS > Sync Settings` for RNG purposes:

- **Region Value**: __Only__ if you imported a config from your 3DS or dumped your concole's System Settings app - do **NOT** leave on Auto-Select but change to the one that matches the config file.
- **Use Real Time + Initial Time:** Self-explanatory.
- **Random Initial Ticks:** False if you want to do initial seed RNG for either G6 or G7.
- **Enable 3GX Plugin Loaders:** True if you want to use PokeReader.

***
_The contents of this guide were all written by [Unknown Warrior](https://github.com/Unknown-Warrior) with small additions and rewrites by SexyMalasada._<br><br>
_[< Back to the Miscellaneous Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/MISC)_