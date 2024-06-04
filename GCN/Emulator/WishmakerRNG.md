# Wishmaker Jirachi RNG Guide

This guide is meant to teach you how to RNG a Wishmaker Jirachi from the ENG Colosseum Bonus Disc.<br>
Contrary to what you may think, most of this RNG is actually done on a Gen 3 game (Ruby or Sapphire), rather than being an actual GCN RNG.<br>
Due to the current unavailability of a lua script for Bizhawk, this guide follows the process in VBA instead.

## Getting Started

What you'll need:

- [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) (an old fork of PokéFinder with some extra functionalities)
- [Jirachi Finder](https://github.com/Lincoln-LM/Jirachi-Finder/)
- [RS_Checksums_RNG](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main) Gen 3 VBA Lua Script
- [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) emulator
- [Dolphin](https://dolphin-emu.org/download/) emulator (official build with an integrated VBA connection)
- A dumped ROM of Pokémon Ruby or Sapphire
- A dumped ISO of the Colosseum Bonus Disc

## Preparation & Basic Info

Wishmaker Jirachi is generated when the the GBA (VBA) is connected to the GameCube (Dophin) running the Colosseum Bonus Disc, with it's stats being decided during this interaction by checking a value in the Ruby or Sapphire game's save, called a `Checksum`.<br>
This `Checksum` is an internal value that is used to 'check' and validate a save's `block`, which is something all RS saves always have 2 of, consisting of the last saved game and the previous saved game.<br>
If this all sounds a bit too 'techy' for you, fret not, as all you need to understand is that this RNG essentially consists of preparing a new Ruby or Sapphire save with a specific Checksum value, in order to obtain your desired target WISHMKR Jirachi!

## Step 1: Searching for a target

_Important note: If you have an official PokeFinder 4.0.0 version or later installed, keep in mind you will need to have a separate `profiles.json` file just for Finder-Toolbox, in order to avoid conflicts. Follow [this PokeFinder profiles](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/MISC/DS/PokeFinderProfiles.md) management guide for more info!_

Open Finder-Toolbox and select the `Stationary` option under the `Gen 3` tab.<br>
In the new window, open the `Searcher` tab, and configure it as follows (example image below):
- Method: Wishmaker
- Filters: IV ranges, Shinyness and Nature options as you desire.
_Note 1: No profile setup is required to be loaded for the searching of Wishmaker Seeds and spreads._<br>
_Note 2: Because the `seed` values for Wishmaker RNG are only 16-bit (4 digits), the available IV spreads and Nature combos are very limited! As a well known example of this limitation: there are **only** 9 different Shiny Wishmaker Jirachi possible combos!_<br>

Once you're satisfied with your search parameters, click `Search` and let Finder-Toolbox run the search.<br>
After it has found some results select a suitable IV spread & Nature combo, and note down your target seed somewhere.<br>

![](https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/Wishmaker1.png)<br>

## Step 2: RNGing a new save's Checksum