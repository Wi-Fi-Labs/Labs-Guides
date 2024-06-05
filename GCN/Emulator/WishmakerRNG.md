# Wishmaker Jirachi RNG Guide

This guide is meant to teach you how to RNG a Wishmaker Jirachi from the ENG Colosseum Bonus Disc.<br>
Due to the current unavailability of a lua script for Bizhawk, this guide follows the process using VBA instead.

## Getting Started

What you'll need:

- [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) (an old fork of PokéFinder with some extra functionalities)
- [Jirachi Finder](https://github.com/Lincoln-LM/Jirachi-Finder/)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main) (specifically `RS_Checksums_RNG` & `RS_RNG_2.0`)
- [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) emulator
- [Dolphin](https://dolphin-emu.org/download/) emulator (official build with an integrated VBA connection)
- A dumped ROM of Pokémon Ruby or Sapphire
- A dumped ISO of the Colosseum Bonus Disc

## Preparation & Basic Info

Wishmaker Jirachi is generated when the the GBA (VBA) is connected to the GameCube (Dophin) running the Colosseum Bonus Disc, with it's stats being decided during this interaction by checking a value in the Ruby or Sapphire game's save, called a `Checksum`.<br>
Contrary to what you may think, most of this RNG is actually done on a Gen 3 game (Ruby or Sapphire), rather than being an actual GCN RNG, as the process essentially consists of preparing a new Ruby or Sapphire save with a specific `Checksum` value, in order to obtain your desired target WISHMKR Jirachi!<br>
If you wish to learn more about what the `Checksum` is, please refer to [this page](https://bulbapedia.bulbagarden.net/wiki/Save_data_structure_(Generation_III)).<br>
_Important note: If you have an official PokeFinder 4.0.0 version or later installed, keep in mind you will need to have a separate `profiles.json` file just for Finder-Toolbox, in order to avoid conflicts. Follow [this PokeFinder profiles](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/MISC/DS/PokeFinderProfiles.md) management guide for more info!_

## Step 1: Searching for a target

Open Finder-Toolbox and select the `Stationary` option under the `Gen 3` tab.<br>
In the new window, open the `Searcher` tab, and configure it as follows (example image below):
- Method: `Wishmaker`
- Filters: `IV ranges`, `Shiny` and `Nature` options as you desire.<br>
_Note 1: No profile setup is required to be loaded for the searching of Wishmaker Seeds and spreads._<br>
_Note 2: Because the seed values for Wishmaker RNG are only 16-bit (4 digits), the available IV spreads and Nature combos are very limited! A well known example of this limitation is that there are **only** 9 different Shiny Wishmaker Jirachi possible combos!_<br>

Once you're satisfied with your search parameters, click `Search` and let Finder-Toolbox run the search.<br>
After it has found some results select a suitable IV spread & Nature combo, and note down the respective target seed somewhere.<br>

![](https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Emulator/Images/Wishmaker1.png)

## Step 2: Finding Checksum save parameters

Open Jirachi Finder.<br>
This tool makes it possible for you to essentially 'configure' a new save's parameters for you to get the desired `Checksum` value, that will match your target Jirachi `seed` (example image below).<br><br>

Start by configuring things like `Name`, `IDs`, `Clock`, and `Starter`. If you don't particularly care about any of these, I suggest to just use whatever values get you closer to your target seed (ie Checksum) as displayed in the small box at the center-bottom area of the tool.<br>
Once you're done with those, you can then fiddle with the `Game Options` settings.<br>
Lastly, configure the `Playing Time` until you get the desired Checksum - It is advised to allow for a play time of _at least_ 10:00 minutes, in order to be able to safely walk to Route 103 and back, and obtain the Pokédex!<br>
You can always go back to one of the previous parameters and adjust it slightly until you get the desired result.<br>
After you've successfully found a combination of parameters you're happy with, you can double check if your desired spread will be obtained with this Checksum by configuring the `Info>Time` section of the tool with a `Starting Time` of -1F from your `Playing Time`, a `Wait Time` of just 1F, and then clicking `Generate`.<br>

![](https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Emulator/Images/Wishmaker2.png)<br>

Once you're done you can then proceed to the actual RNGing of the save itself!<br>

_Important Note: It is imperative that you don't run into any wild encounters during your playthrough as those can change your final Checksum value considerably. For this reason you should leave the `Pokémon` section with no checks, and use save states when RNGing the save, so that you can restore it in case you accidentally run into any._

## Step 3: Finding TID/SID



## Step 4: RNG the save

Before opening the emulator, ensure there is no save for your game (Ruby or Sapphire) in the saves folder (by default on VBA it's the `Battery` folder). Once you've confirmed this, open VBA and launch your game and run the `RS_RNG_2.0` lua script.<br>
