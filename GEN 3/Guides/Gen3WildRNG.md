# Gen 3 Wild / Static / Gift RNG

This guide is meant to explain & teach you how to RNG Wild Pokémon in the Gen 3 games, Wild including all of grass, cave, water, fishing encounters, and even Rock Smash.<br>
The process is presented here as done on, and with examples in `BizHawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to the latter noted where relevant.

## Getting Started

Required tools:
- [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [BizHawk 2.8-rc1](https://github.com/TASEmulators/BizHawk/releases/tag/2.8-rc1); [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) or [mGBA](https://mgba.io/downloads.html) emulator
- A copy of any of the Gen 3 games

## Preparation & Basic Info

The various Wild encounter types have differing [Methods](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods) by which the Pokémon you encounter are generated. These methods and the probability of them occurring differ between RSFRLG and Emerald.<br>
When an encounter is generated with a non-expected Method, we say that a 'Method-shift' occurred. This is usually caused by [VBlank interference](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#vblank), which if it happens at the critical point in your RNG it can influence your result, where a different IV spread than what you desired occurs instead.<br>

To trigger the various Wild encounters when RNGing, the following methods are used:
- Grass, Cave & Water encounters are triggered by using Sweet Scent (recommended), or by turning/walking in the grass (FRLG only)
- Fishing encounters are triggered by pressing A when the character has found a 'bite' with the fishing rod
- Rock Smash encounters are triggered by pressing A on the last dialogue of the field move's animation

To obtain better results, you should familiarize yourself first with the [Gen 3 Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md) guide, as well as the [Pandora's Box](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md#pandoras-box) method, with the former being particularly important!<br>

Below you will find a first section explaining how to RNG Wild Pokémon, that is common to all encounter types, followed by sub-sections with specifics for each encounter type.<br>


***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_