# Gen 3 TID/SID RNG

This guide is meant to explain & teach you how to RNG your TID and/or SID in the Gen 3 games, which can be desired either for aesthetic reasons, or play a key part in making the RNGing of any Pokémon as Shiny and with the best possible IV spread much easier.<br>
The process is presented here as done on, and with examples in `BizHawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to the latter noted where relevant.

## Getting Started

Required tools:
- [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)
- [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [Lego's 'SID-For-Shiny' Tool](https://legofigure11.github.io/tools/sid-for-shiny/)
- [Gen 3 TID/SID Frame Finder](https://github.com/DevonStudios/Gen3TIDSIDFrameFinder/releases)
- [Bizhawk 2.8](https://github.com/TASEmulators/BizHawk/releases/tag/2.8) or [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) emulator
- A copy of any of the Gen 3 games

## Preparation & Basic Info

When starting a new game, you'll get assigned a combination of a Trainer ID (TID), and Secret ID (SID). These values combined, make Pokémon with certain [Personality Values](https://bulbapedia.bulbagarden.net/wiki/Personality_value#Shininess), or `PID` for short, Shiny when encountered or received in-game.<br>
A common and efficient way of RNGing perfect Pokémon, is to use what's called the `Pandora's Box` method; which consists of first finding a `PID` for a given Nature & IV spread you would like to have Shiny, and then RNG your TID & SID combo in order to make it so. You can even combine a specific TID with a given PID for a twofold 'flex' on your RNGd Pokémon!<br>

PokéFinder (PF) is an RNG tool that allows you to calculate, search for and predict results of these values on a new save, which combined with certain actions performed in-game, at the right moment, allow you to obtain your desired TID & SID combo.<br>

The way you RNG this however, differs somewhat between RS and FRLGE, mostly due to the different methods by which Initial Seeds are generated in each game. You should check out the [Gen 3 Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Emulator/Gen3InitialSeedRNG.md) guide to learn more about this first, if you haven't yet.<br>
Below you will find a section for each of these different processes, fully explaining them, as well as a section on `Pandora's Box`. If you don't care about making a particular spread Shiny and just want to RNG a TID or SID for aesthetic reasons, you can just skip the next section.

# Pandora's Box

The `Pandora's Box` method allows you to RNG a save's TID & SID combo, so that a specific `PID` (or pair of `PIDs`) can be made Shiny when encountered in-game. In this section I will explain how to do it, when you're preparing to RNG a new save's TID & SID.<br>

Open `PokéFinder` and in the Gen 3 tab select either the `Wild` or `Static` option. You can select `None` in profiles, since we're just looking for spreads right now, meaning the TID & SID from the profile is irrelevant.<br>
In the `Searcher` tab, configure the filters as you see fit, and after doing so click `Search`. In my examples below I searched for any Jolly -SpAtk IV spreads on both the `Wild` & `Static` tabs, and have decided on the Jolly 31/31/31/24/31/31 spread with a PID of `505C1B54`:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDPandora1.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDPandora2.png"/></p><br>

If you want to get even more out of your TID RNG, you can also look for a specific 'Nature Pair'; which is a pair of two `PID` that share the exact same IV spread, but with different Natures. This is especially useful if you plan on RNGing many different Static or Wild Pokémon that prefer different Natures, as you won't have to TID RNG two different saves if you can find a desirable pair.<br>
These Nature Pairs can be visually identified by sharing the exact same IV spread as mentioned, and having only a different 1st and 5th digit. An example of this would be the perfect IV Timid + Modest or Calm + Modest pairs showcased in the image below:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDPandora3.png"/></p><br>

You can manually search for these pairs, or you can alternatively use [this nifty Google Sheet](https://docs.google.com/spreadsheets/d/1yrotkmuGlvQwI1qX8DgJkCVFkIeThHgA_Llbf48dxVI/edit?gid=875594700) that Labs user Unknown Warrior created, which can calculate different Nature Pairs for you.<br>

It is also possible to RNG your save so that your desired spread, and Pokémon you obtain with it, are rendered as [Square Shiny](https://bulbapedia.bulbagarden.net/wiki/Shiny_Pok%C3%A9mon#Variants) in the SwSh games. This has no practical effect or meaning in any other games besides those Gen 8 titles, but if you're curious on what specific TID & SID combo gives your `PID` the Square Shiny trait, you can calculate it with [Lego's 'SID-For-Shiny' Tool](https://legofigure11.github.io/tools/sid-for-shiny/).<br>

Once you're satisfied with your selected `PID` or Nature Pair, you can then proceed to the RNG proper.

# RS TID/SID RNG

In Pokémon Ruby & Sapphire, there are 2 ways you can approach TID/SID RNG depending on which Initial Seed method you want to use (Live Battery vs Dead Battery). For the purpose of this guide, we will be using the Live Battery method, which is the advised method for the sake of getting more options in terms of TID & SID combos.<br>
There are also 2 ways to search for a desired TID/SID combo, which require a different tool between them, and are presented below:
- First one is advised if you're doing the Pandora's Box method, want **a specific TID**, and don't care about your save's starting date; it requires `Finder-Toolbox` (an old PokéFinder fork with some extra features) and that you use the RS Live Battery method for the Initial Seed generation.
- Second one is advised if you're not doing the Pandora's Box method, don't care about a specific TID and/or care about your save's starting date; it just requires the standard latest `PokéFinder`.

### Searching with Finder-Toolbox

Open `Finder-Toolbox` and in the Gen 3 tab select the `TID/SID` option. In the new window, select the `Gen III RS Search` tab, and input your target `PID` and desired `TID`; after this just click 'Search'.<br>
You should now have a few results for Dates + Times where you'll get a combo of your desired TID + an SID that will make your desired `PID` Shiny - including if it will be Square Shiny when transferred over to SwSh. If no Square Shiny option appears, it unfortunately means that there is no Initial Seed where that specific TID+SID combo is possible.<br>
Unfortunately all the Dates are calculated in the year 2000, as the tool can't search for the specific combos in other years, so you'll be stuck with a save starting date on that year. On the example below we will be selecting the option that gives us the Initial Seed `CA23`, as it gives us the Square Shiny combo (for aesthetic reasons).<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS1.png"/></p>

### Searching with PokéFinder

Open `PokéFinder` and in the Gen 3 tab select the `IDs` option. In the new window, select the `RS` tab - here you can input a variety of values you'd like to search for. Because we're using the Pandora's Box method, we want a TID that will make our `PID` Shiny above all else, so we select the PID option and input it there; after this you would select a given Date & Time you'd like to start your game at (or check Dead Battery if you're using that method), a maximum amount of advances you're willing to wait/go for, and click 'Search'.<br>
You should now have a few results for different TID/SID combos that make your `PID` Shiny! Simply select one of them as your target, and note the required RNG advancements. If you want to know if any of the results will yield a Square Shiny combo, you can check the values with [Lego's 'SID-For-Shiny' Tool](https://legofigure11.github.io/tools/sid-for-shiny/).<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS2.png"/></p>

## RS TID/SID RNG Proper

Once you've found a suitable target from either of the 2 search methods above, you can now proceed with the RNG proper! For this example we shall be using the option that gives us the Initial Seed `CA23`, that we found with `Finder-Toolbox` above.<br>

Load your emulator & game with the required Date & Time (in my case `04/02/2000 15:57:00`), and then load the `RS_RNG_BizHawk_SM` script in the `Pandora` tab - if you set everything correctly, you should get your target Initial Seed.<br>
Start a New Game, selecting your gender and entering your desired character name, proceeding all the way until you reach the screen shown below:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS3.png"  width=480 height=320/></p><br>

Upon pressing A on this screen, your TID & SID will be generated; let the RNG advance until you're ~200 frames before your target, pause the game and make a save state so that you can return to this point if something goes wrong or you miss your frame.<br>
The reason we pause at this point is because there is a delay of around 75 frames between the moment you press A and your TID & SID are actually generated, due to the character shrinking animation. In this case, given a target advance of `46031`, this means we should hold A and un-pause on this screen at advances `45956`.<br>
After you press A at the final screen, you should see your desired TID & SID appear at the bottom right corner of the script, once you're in the back of the moving truck!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS4.png"  width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS5.png"  width=480 height=320/></p>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS6.png"  width=480 height=320/></p><br>


_Note: If your obtained TID & SID combo doesn't match what is expected, it is advised to make a few practice runs at the final screen, restoring to your previous save state, to properly calibrate your delay for this situation, as it may differ slightly from 75._<br>
_Alternatively you can also use the IDs' window RS tab in PokéFinder, as per the example below, to check which frame you are actually hitting and from there re-calculate your actual delay._<br>_

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS7.png"/></p>

# FRLGE TID/SID RNG



***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._