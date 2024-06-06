# Gen 3 Initial Seed RNG

This guide is meant to explain & teach you how to RNG Initial Seeds in the Gen 3 games, something which is essential and at the core of every other RNG you'll likely want to do.<br>
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

In the Generation 3 games, there are four methods by which Initial seeds can be RNGd: `Live Battery` & `Dead Battery` (`RS` / `FRLG` / `E` respectively).<br>
- `Live Battery`: is only applicable and usable in __Ruby & Sapphire__ and is a method that involves starting the game at a specific Date & Time, that provides you a lot more options for RNG in these games. On an actual cartridge it is the method used when the battery in it is still running and keeping the in-game time - which in an emulator means using the RTC functions of Bizhawk, or use RunAsDate with VBA.
- `Dead Battery RS`: is the method used in __Ruby & Sapphire__ when an actual cartridge's battery has run dry - which in an emulator means _not_ using Bizhawk's Date & Time function, or have _Real-Time Clock_ un-checked in VBA. With a dead battery, these games always starts with an Initial seed of `05A0`.
- `Dead Battery FRLG`: is the method used in __FireRed & LeafGreen__. As these two lack a battery to begin with, the Initial seed is instead generated upon pressing A or Start at the Title screen.
- `Dead Battery E`: more commonly known as "Painting Re-seed" or "Painting method", is the method used in __Emerald__. Because this game has a programming error that makes the Initial Seed always be `0000` on game start-up, regardless of the cartridge's battery status, after you first save it, this method allows you to bypass this issue by taking advantage of an unintended game mechanic.<br>

Below you will find a section for each method, outlining how to RNG Initial Seeds with each them.

## Live Battery

## Dead Battery RS

## Dead Battery FRLG

## Dead Battery E (Painting Re-seed)


***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._