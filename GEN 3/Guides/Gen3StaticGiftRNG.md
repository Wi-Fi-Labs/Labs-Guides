# Gen 3 Static / Gift RNG

This guide is meant to explain & teach you how to RNG Static & Gift Pokémon in the Gen 3 games.<br>
The process is presented here as done on, and with examples in `BizHawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to the latter noted where relevant.

## Getting Started

Required tools:
- [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [BizHawk 2.8-rc1](https://github.com/TASEmulators/BizHawk/releases/tag/2.8-rc1); [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) or [mGBA](https://mgba.io/downloads.html) emulator
- A copy of any of the Gen 3 games

## Preparation & Basic Info

The various Static & Gift encounters found in the Gen 3 games are all very similar in the way you RNG them, with the differences usually lying solely in the location/final setup, as well as their [Offset](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#offset).<br>
Static Pokémon include both Legendary and non-Legendary (example: Kecleon) encounters, that are initiated by interacting with the Pokémon itself. Gift encounters are all the Pokémon that are given to you by NPCs, in one form or another, such as Starters, Fossils, etc.

To see a full list of all Static & Gift Pokémon you can RNG across the Gen 3 games, and their respective setup & `Offset` values, you should check out the [Gen 3 Final Screens]() page.<br>

In order to obtain better results, you should also familiarize yourself first with the [Gen 3 Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md) guide, as well as the [Pandora's Box](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md#pandoras-box) method, with the former being particularly important!<br>

Below you will find <br>

## Step 1: Searching for Spreads

If you did [TID/SID RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md) for your save, specifically if you did so using the [Pandora's Box](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md#pandoras-box) method, you should know exactly what `PID` and IV spread you'll be targeting. Nevertheless you should always double-check in [PokéFinder](https://github.com/Admiral-Fish/PokeFinder), with your save's profile selected, that your desired spread does occur, and at how many `Advances`.<br>



***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_