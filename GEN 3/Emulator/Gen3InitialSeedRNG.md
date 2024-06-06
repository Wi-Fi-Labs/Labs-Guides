# Gen 3 Initial Seed RNG

This guide is meant to explain & teach you how to RNG Initial Seeds in the Gen 3 games, something which is essential and usually the first step of every other RNG you'll likely want to do.<br>
The process is presented here as done on, and with examples in `Bizhawk` (which runs an mGBA core); but it can be followed in `VBA` just as well, with specifics to this emulator noted where relevant.

## Getting Started

What you'll need:
- [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [Bizhawk 2.8](https://github.com/TASEmulators/BizHawk/releases/tag/2.8) or [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) emulator
- [RunAsDate](https://www.nirsoft.net/utils/run_as_date.html) (if using VBA)
- A copy of any of the Gen 3 games

## Preparation & Basic Info

When you start a game, a combination of values are used to determine the `Initial Seed`. This value serves as the starting point from which the game's algorithm generates subsequent hexadecimal values, which in turn determine the features of any encountered Pokémon (or any game event really).<br><br>
PokéFinder is an RNG tool that allows you to calculate, search for and predict results of these values for a given RNG `advance` (also commonly but inaccurately called "frame"), which combined with certain actions performed in-game, timed at the right moment, allow you to obtain perfect IV & Shiny Pokémon.<br><br>

In the Generation 3 games, there are several methods by which Initial seeds can be RNGd: `Live Battery`, `Dead Battery` (`RS` or `E`) & `FRLG Initial Seeds`.<br>
- `Live Battery`: is only applicable and usable in __Ruby & Sapphire__ and is a method that involves starting the game at a specific Date & Time, that provides you a lot more options for RNG in these games. On an actual cartridge it is the method used when the battery in it is still running and keeping the in-game time - which in an emulator means using the RTC functions of Bizhawk, or use RunAsDate with VBA.
- `Dead Battery RS`: is the method used in __Ruby & Sapphire__ when an actual cartridge's battery has run dry - which in an emulator means _not_ using Bizhawk's Date & Time function, or have _Real-Time Clock_ un-checked in VBA. With a dead battery, these games always starts with an Initial seed of `05A0`, which in practice means a lot fewer feasible options, so this method is usually only used for TID/SID RNG.
- `Dead Battery E`: more commonly known as "Painting Re-seed" or "Painting method", is the method used in __Emerald__. Because this game has a programming error that makes the Initial Seed always be `0000` on game start-up, regardless of the cartridge's battery status, after you first save it, this method allows you to bypass this issue by taking advantage of an unintended game mechanic.<br>
- `FRLG Initial Seeds`: is the method used in __FireRed & LeafGreen__. As these two lack a battery to begin with, the Initial seed is instead generated upon pressing A or Start at the Title screen.

Below you will find a section for each method, outlining how to RNG Initial Seeds with each them.

## Live Battery

For this section I will be using an example target Initial seed of `92B8`, which can be obtained by setting the date & time as `31/12/2023 00:00:00`.<br>
When reading up on other guides such as [Gen 3 TID/SID RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Emulator/Gen3TIDSIDRNG.md) or [Gen 3 Captures RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Emulator/Gen3CapturesRNG.md), you'll learn how to first find a desired Initial seed.

### Bizhawk

Open Bizhawk, load your game, and go to `GBA>Settings>Sync Settings`.<br>
In this tab you can see several configurable RTC options; you'll want to set these as follows:
- RTC Use Real Time: `False`
- RTC initial Time: The target seed's Date & Time in the format `DD/MM/YYYY HH:MM:SS`
- RTC: `True`<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3InitialSeedLBBH1.png"/></p><br><br>

After configuring the above, load the `RS_RNG_2.0_Bizhawk` script, reboot core, and Bizhawk will launch the game with your specified Date & Time, giving you your desired Initial Seed!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3InitialSeedLBBH2.png"/></p><br>

### VBA

Open VBA, navigate to `Options>Emulation>Real Time Clock` and :white_check_mark: it:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3InitialSeedLBVBA1.png"/></p><br><br>

After doing the above, open RunAsDate and configure it as follows:
- Select the path of your target application (in this case where your `VBA.exe` is located)
- Date/Time: `Absolute date/time`
  - The target seed's Date & Time in the format `DD/MM/YYYY HH:MM:SS`
- :white_check_mark: `Immediate Mode`<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3InitialSeedLBVBA2.png"/></p><br><br>

After configuring the above press `Run`, and VBA will launch with your specified Date & Time, keeping it static. All you need to do afterwards is launch your game, load the `RS_RNG_2.0` VBA script, and you'll get your desired Initial Seed!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3InitialSeedLBVBA3.png"/></p><br><br>

_Note: Depending on the architecture of the app you're using (32bit or 64bit), you need to download and use the corresponding RunAsDate version to launch it! The recommended VBA version in this guide is 32bit.<br>
Depending on how your computer's permissions are set, you may also need to use the `Run As Administrator` option in RunAsDate._

## Dead Battery RS

The Dead Battery method in Ruby & Sapphire is usually not used and advised against except in TID/SID RNG, as it gives you way less desirable possibilities vs the Live Battery method. With a dead battery, RS will always have an Initial seed of `05A0`. Below you can learn how to configure both emulators to use this method.<br>

### Bizhawk

Open Bizhawk, load your game, and go to `GBA>Settings>Sync Settings`.<br>
In this tab you can see several configurable RTC options; for this method you only need to set one of them, as follows:
- RTC: `False`<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3InitialSeedDBBH1.png"/></p><br><br>

After configuring the above, load the `RS_RNG_2.0_Bizhawk` script, reboot core, and Bizhawk will launch the game disregarding any Date & Time settings, giving you the expected Initial Seed of `05A0`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3InitialSeedDBBH2.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3InitialSeedDBBH3.png"/></p><br>

### VBA



## Dead Battery E (Painting Re-seed)

## FRLG Initial Seeds

***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._