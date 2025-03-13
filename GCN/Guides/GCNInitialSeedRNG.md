# GameCube Initial Seed RNG

This guide is meant to explain & teach you how to RNG Initial Seeds in the GameCube games, which is something essential and usually the first practical step of any RNG you'll likely want to do.<br>
The process is presented here as done on, and with examples in `Dolphin-Lua Core`, which is a special fork of the Dolphin Emulator that supports Lua Scripting.

## Getting Started

Required tools:
- [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) (an old fork of [PokéFinder](https://github.com/Admiral-Fish/PokeFinder) with some extra functionalities)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [Dolphin-Lua Core](https://github.com/Real96/Dolphin-Lua-Core) emulator
- [RunAsDate](https://www.nirsoft.net/utils/run_as_date.html)
- A copy of any of the GCN games

## Preparation & Basic Info

When you load a game, a combination of values are used to determine the `Initial Seed`. This value serves as the starting point from which the game's algorithm generates subsequent hexadecimal values, which in turn determine the features of any encountered Pokémon (or any game event really).<br>

[Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) is an RNG tool that allows you to calculate, search for and predict results of these values for a given RNG `Advance` (also previously and still commonly named 'frame'), which combined with certain actions performed in-game, at the right moment, allow you to obtain perfect IV & Shiny Pokémon.<br>
This tool is an old fork of [PokéFinder](https://github.com/Admiral-Fish/PokeFinder) with some extra functionalities, namely support for `GameCbue RTC`, which is the process that allows us to manipulate the initial Seed in the GCN games.<br>
This functionality is not present in official builds of PokéFinder, hence why we must use this fork. The Dolphin emulator version we use is also a specific fork that has lua scripting support, which is missing from official builds of Dolphin.<br>
When reading up on other GCN RNG guides, you'll learn more in-depth how to use Finder-Toolbox to first find a desired target and Initial Seed, so in this guide we'll just aim to manipulate an example Initial Seed that would allow us to reach a `Current State: 017292D1`, which would give us a desirable specific Channel Jirachi target.<br>

_**Important Note:** If you have an official PokeFinder 4.0.0 version or later installed, keep in mind you will need to have a separate `profiles.json` file just for Finder-Toolbox, in order to avoid conflicts. Follow [this PokeFinder profiles](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/DS/PokeFinderProfiles.md) management guide for more info!_

## Step 1: Finding your Origin Seed

The first thing you must do is find the `Origin Seed` for your game. This is the Initial Seed you obtain on the Date & Time of `01/01/2000 00:00:00` when loading a particular game. In order to find it, we need to launch [Dolphin-Lua Core](https://github.com/Real96/Dolphin-Lua-Core) with [RunAsDate](https://www.nirsoft.net/utils/run_as_date.html).<br>

To do this, open RunAsDate and configure it as follows:
- Select the path of your target application (in this case where your `Dolphin.exe` is located)
- Date/Time: `Absolute date/time`
  - The target seed's Date & Time in the format `DD/MM/YYYY HH:MM:SS`
- :white_check_mark: `Immediate Mode`<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/GCNInitialSeedRNG1.png"/></p><br>

After configuring the above press `Run`, and Dolphin will launch with your specified Date & Time, keeping it static. All you need to do afterwards is load the relevant lua script via Tools > Execute Script, launch your game and click `Start` in the Lua Script pop-up to initiate said script. You should then have your `Initial Seed` displayed - this will be your `Origin Seed` value! In our example this turned out as `001823C4`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/GCNInitialSeedRNG2.png" width=720 height=504/></p><br>

_Note: Depending on the architecture of the app you're using (32bit or 64bit), you need to download and use the corresponding RunAsDate version to launch it! The recommended VBA version in this guide is 32bit.<br>
Depending on how your computer's permissions are set, you may also need to use the `Run As Administrator` option in RunAsDate._

## Step 2: 

Now that you have your `Origin Seed`, you can manipulate the `Initial Seed` for any desired target. As mentioned previously, in this example we'll be aiming to find an Initial Seed that allows us to hit a specific Channel Jirachi spread, which is generated with a Current State of `017292D1`.<br>
In the main window of [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox), select _Gen 3 Tools > GameCube > GameCube RTC_. A small window will pop-up, which you will need to configure in order to find a suitable GCN Initial Seed to obtain your target.<br>
Configure the filters as such:
- Origin Seed: The `Origin Seed` you obtained in the previous Step
- Target Seed: Your target Seed or Current State
- End Date: How far from the Origin date (2000/01/01) you want the search to run. Using up to the full year 2000 is acceptable, but going beyond that may give slightly different Initial Seed on emulator start-up due to a greater distance from the `Origin Seed`
- Min/Max Advances: Minimum & Maximum number of Advances you're willing to make
- Ageto 0 Dif/Channel Menu/Rumble/Box: Check/uncheck these as applicable depending on which game or specific RNG you're performing

Once you've filled in all of the above, click `Search` and let Finder-Toolbox run the search.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/GCNInitialSeedRNG3.png"/></p><br>

Once you find a result you deem acceptable, make note of the Initial Seed you'll be targeting, as well as the required Date & Time. In our example we will aim for an `Initial Seed: F06C94E4`, with a Date & Time of `2000-08-22 15:05:21`.<br>

Configure RunAsDate with your new Date & Time values and then click `Run` to launch Dolphin. Load the relevant lua script via Tools > Execute Script, launch your game and click `Start` in the Lua Script pop-up to initiate said script.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/GCNInitialSeedRNG4.png"/></p><br>

If you did everything correctly, you should see your targeted `Initial Seed` displayed by the lua script. You can then proceed with whatever you are Pokémon target you are aiming to RNG!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/GCNInitialSeedRNG5.png" width=720 height=504/></p>

***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the GCN Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GCN)_