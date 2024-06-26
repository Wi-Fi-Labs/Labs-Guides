# Gen 3 TID/SID RNG

This guide is meant to explain & teach you how to RNG your TID and/or SID in the Gen 3 games, which can be desired either for aesthetic reasons, or play a key part in making the RNGing of any Pokémon as Shiny and with the best possible IV spread much easier.<br>
The process is presented here as done on, and with examples in `Bizhawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to this emulator noted where relevant.

## Getting Started

Required tools:
- [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [Lego's 'SID-For-Shiny' Tool](https://legofigure11.github.io/tools/sid-for-shiny/)
- [Gen 3 TID/SID Frame Finder](https://github.com/DevonStudios/Gen3TIDSIDFrameFinder/releases)
- [Bizhawk 2.8](https://github.com/TASEmulators/BizHawk/releases/tag/2.8) or [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) emulator
- A copy of any of the Gen 3 games

## Preparation & Basic Info

When starting a new game, you'll get assigned a combination of a Trainer ID (TID), and Secret ID (SID). These values combined, make Pokémon with certain [Personality Values](https://bulbapedia.bulbagarden.net/wiki/Personality_value#Shininess), or `PID` for short, Shiny when encountered or received in-game.<br>
A common and efficient way of RNGing perfect Pokémon, is to use what's called the `Pandora's Box` method; which consists of first finding a `PID` for a given Nature & IV spread you would like to have Shiny, and then RNG your TID & SID combo in order to make it so. You can even combine a specific TID with a given PID for a twofold 'flex' on your RNGd Pokémon!<br>

PokéFinder (PF) is an RNG tool that allows you to calculate, search for and predict results of these values on a new save, which combined with certain actions performed in-game, at the right moment, allow you to obtain your desired TID & SID combo.<br>

The way you RNG this however, differs somewhat between RS and FRLGE, mostly due to the different methods by which Initial Seeds are generated in each game. You should check out the [Gen 3 Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Emulator/Gen3InitialSeedRNG.md) guide to learn more about this if you haven't yet.<br>
Below you will find a section for each of these different processes, fully explaining them, as well as a section on `Pandora's Box`. If you don't care about making a particular spread Shiny and just want to RNG a TID or SID for aesthetic reasons, you can just skip this first section.

# Pandora's Box

The `Pandora's Box` method allows you to RNG a save's TID & SID combo, so that a specific `PID` (or pair of `PIDs`) can be made Shiny when encountered in-game. In this section I will explain how to do it, when you're preparing to RNG a new save's TID & SID.<br>

Open PokéFinder and in the Gen 3 tab select either the `Wild` or `Static` option. You can select `None` in profiles, since we're just looking for spreads right now, meaning the TID & SID from the profile is irrelevant.<br>
In the `Searcher` tab, configure the filters as you see fit, and after doing so click `Search`. In my examples below I searched for any Jolly -SpAtk IV spreads on both the `Wild` & `Static` tabs, and have decided on the Jolly 31/31/31/24/31/31 spread with a PID of `505C1B54`:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDPandora1.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDPandora2.png"/></p><br>

If you want to get even more out of your TID RNG, you can also look for a specific 'Nature Pair'; which is a pair of two `PID` that share the exact same IV spread, but with different Natures. This is especially useful if you plan on RNGing many different Static or Wild Pokémon that prefer different Natures, as you won't have to TID RNG two different saves if you can find a desirable pair.<br>
These Nature Pairs can be visually identified by sharing the exact same IV spread as mentioned, and having only a different 1st and 5th digit. An example of this would be the perfect IV Timid + Modest or Calm + Modest pairs showcased in the image below:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDPandora3.png"/></p><br>

You can manually search for these pairs, or you can alternatively use [this nifty Google Sheet](https://docs.google.com/spreadsheets/d/1yrotkmuGlvQwI1qX8DgJkCVFkIeThHgA_Llbf48dxVI/edit?gid=875594700) that Labs user Unknown Warrior created, which can calculate different Nature Pairs for you.<br>

Once you're satisfied with your selected `PID` or Nature Pair, you can then proceed to the RNG proper.

# RS TID/SID RNG




# FRLGE TID/SID RNG



***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._