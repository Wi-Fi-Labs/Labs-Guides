# Wishmaker Jirachi RNG Guide

This guide is meant to teach you how to RNG a Channel Jirachi from the PAL version of Pokémon Channel.

## Getting Started

What you'll need:

- [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) (an old fork of PokéFinder with some extra functionalities)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [Dolphin-Lua Core](https://github.com/Real96/Dolphin-Lua-Core) emulator
- [VBA -m](https://visualboyadvance.org/download/vba-m/) emulator
- [RunAsDate](https://www.nirsoft.net/utils/run_as_date.html)
- A copy of the PAL version of Pokémon Channel
- A copy of Pokémon Ruby or Sapphire

## Preparation & Basic Info

Channel Jirachi is generated when you claim it within Pokémon Channel itself, after you've completed the game by watching all shows it has to offer.<br>
It is a quite simple RNG to perform, but requires some preparation, such as a completed save of Channel, as well as a Ruby/Sapphire save where you have both entered the Hall of Fame _and_ have not yet received either a Channel or Wishmaker Jirachi previously. This guide assumes you already have such 2 savefiles.<br>
The RNG is performed 100% on `Dolphin`, after which you simply connect it to `VBA -m` in order to transfer it to your RS savefile. The specific VBA version linked must be used, as it's the only one you can use to connect with `Dolphin-LuaCore`.<br>
Before attempting this RNG, you should first familiarize yourself with the process for [GCN Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GCN/Guides/GCNInitialSeedRNG.md) if you haven't yet.<br>

_**Important Note:** If you have an official PokeFinder 4.0.0 version or later installed, keep in mind you will need to have a separate `profiles.json` file just for Finder-Toolbox, in order to avoid conflicts. Follow [this PokeFinder profiles](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/DS/PokeFinderProfiles.md) management guide for more info!_

## Step 1: Configuring Dolphin & VBA Connection

The first thing you should do is set up Dolphin-LuaCore and VBA -m so that they can successfully connect to each other. In order to do this you should configure the settings below on each emulator, as follows:

### Dolphin Lua-Core
- Options > Configure > General > Basic Settings > Enable Dual Core (speedup): :x:
- Options > Configure > General > Advances Settings > JIT Recompiler: :white_check_mark:
- Options > Configure > Audio > Sound Settings > DSP LLE recompiler: :white_check_mark:
- Options > Configure > GameCube > Device Settings > Slot A: `Memory Card`
- Options > Configure > General > Basic Settings > Enable Dual Core (speedup): :x:
- Options > Configure > Advanced > CPU Options > Enable CPU Clock Override: :x:
- Options > Controller Settings > Port 2: `VBA`

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG1.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG2.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG3.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG4.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG5.png"/></p>

### VBA -m
- Emulation > Pause when inactive: :x:
- Options > GameBoy Advance > Configure > Boot ROM > Browse and select your GBA BIOS ROM file (you need to procure or dump the BIOS yourself)
- Options > GameBoy Advance > Real-time clock: :white_check_mark:
- Options > GameBoy Advance > Use BIOS file: :white_check_mark:
- Options > Link > Local mode: :white_check_mark:
- Options > Link > Link at boot: :white_check_mark:

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG6.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG7.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG8.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG9.png"/></p><br>

Once you've configured all the settings above, you may proceed to the next step.

## Step 2: Searching for a target

Open [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) and select the `GameCube` option under the `Gen 3` tab.<br>
In the new window, open the `Searcher` tab, and configure it as follows (example image below):
- Method: `Channel`
- Filters: `IV ranges`, `Shiny` and `Nature` options as you desire.<br>

_Note: No profile setup is required to be loaded for the searching of Channel Seeds and spreads._<br>

Once you're satisfied with your search parameters, click `Search` and let Finder-Toolbox run the search.<br>

After it has found some results select a suitable IV spread & Nature combo, and note down the respective target seed somewhere. In our example we will be going for the Jolly Jirachi with `PID: D1F2B146` and a target Seed of `36198EC7`<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG10.png"/></p><br>

Now in the main window, select _Gen 3 Tools > GameCube > GameCube RTC_. A small window will pop-up, which you will need to configure in order to find a suitable GCN Initial Seed to obtain your target.<br>
Configure the filters as such:
- Origin Seed: The `Origin Seed` you obtained in your Dolphin-Lua Core with Pokémon Channel
- Target Seed: Your target Seed, obtained previously
- End Date: How far from the Origin date (2000/01/01) you want the search to run. Using the full year 2000 is recommended, but going beyond that may give slightly different Initial Seed on emulator start-up
- Channel Menu: :white_check_mark:
- Max Menus: Maximum number of Menu Advances you're willing to make; usually 100 should suffice

Once you've filled in all of the above, click `Search` and let Finder-Toolbox run the search.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG11.png"/></p><br>

Hopefully you'll have some results you can pick from; if not you can always extend your search by increasing the number of Max Advances or extending the End Date. In our example we will perform 50 Menu Advances with an `Initial Seed` of `EA8C2044`.<br>

Finally, with our `Initial Seed` we will now check at how many RNG `Advances` our Jirachi will be generated. To do this, return to the GameCube RNG window in Finder-Toolbox, and this time select the `Generator` tab.<br>
Configure the window as such:
- RNG Info: 
  - Method: `Channel`
  - Initial/Max Advances: can leave on default values. Increase your Max Advances if you don't find your target Jirachi
  - Seed: Input your target `Initial Seed` here
- Filters: Configure them as appropriate to find your target Jirachi

Once the above is done, click `Generate` and you should see your target Jirachi, with the number of RNG `Advances` you will advance with the Menu until your target, as will be shown in the lua script.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG12.png"/></p>

## Step 3: RNGing your Jirachi

Open up [Dolphin-Lua Core](https://github.com/Real96/Dolphin-Lua-Core) via [RunAsDate](https://www.nirsoft.net/utils/run_as_date.html) as detailed in the [GCN Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GCN/Guides/GCNInitialSeedRNG.md) guide. Then open up the `Channel_RNG_Dolphin` lua script via Tools > Execute Script.<br>
Load Pokémon Channel with your completed save in the Memory Card and click `Start` in the Lua Script pop-up to initiate said script. You should have your desired `Initial Seed` displayed.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG13.png" width=720 height=504/></p><br>

Once you're at the Pokémon Channel Main Menu, open up the `Jirachi Advancer` in Finder-Toolbox via _Gen 3 Tools > GameCube > Jirachi Advancer_. In this window you can see how many Menu Advances you need to do before you claim your Jirachi, depending on your `Current Seed` (particularly useful if you lose track of how many advances you did!).<br>
To make use of it, configure the window as such:
- Starting Seed: Input here whatever your `Current Seed` is
- Target Seed: Input here the target Seed for your Jirachi (not the initial Seed!)
- Max Advances: Input here whatever `Advances` you found in the Generator tab
- Brute Force Range & Min Actions: leave these blank and unchecked, respectively

After you click `Generate`, you'll be presented a list of numbered actions to do until you reach your target Jirachi. You can have 'refresh' it as you go along, by inputting a new Starting Seed as you do Menu Advances.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG14.png"/></p><br>

Now it's time to perform the actual Menu Advances! To do this, you press A to enter the `Options` in Pokémon Channel's main menu, and then leave back to the main menu by pressing B - when the main menu is reloaded the RNG will advance by a given number of `Advances`; these vary somewhat but the amount they do each time is not really important, all you need to do is to keep checking in Jirachi Advancer frequently, to confirm you're still on a path to your target.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG15.png"/></p><br>

_**Important Note:** At no point during the Menu Advances stage should you select any other option or enter any other menu, as this will surely advance the RNG by an amount that the RNG tool was not prepared to account for, making you have to restart the RNG process from scratch. We recommend you make use of save states as you go along, so as to safeguard your progress with Menu Advances._<br>

Once you do your calculated Menu Advances, your lua script should display an RNG `Advances` value that's slightly lower than your actual target - this is expected, as the Jirachi redemption cutscene itself advances the RNG a few more, so that you'll actually hit your target after selecting the `Jirachi` button in the Options Menu.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG16.png" width=720 height=504/></p><br>

Click the `Jirachi` Option to hit your target. Prof. Oak will appear and congratulate you on completing the game, when suddenly a cutscene with Jirachi 'appearing for a visit' will begin. As this cutscene unfolds, you'll see the RNG advance the last required `Advances`, with the attributes of your target Jirachi being displayed in the lua script, once you reach your target `Advances`. Make a save state here to avoid losing your progress.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG17.png" width=720 height=504/></p>

## Step 4: Transferring the Jirachi to Ruby/Sapphire

After you hit your target Prof. Oak will then ask if you wish to transfer Jirachi to your Ruby/Sapphire game, which you will do in this last Step.<br>

_Note: The transfer process must be done immediately upon claiming Jirachi. You cannot 'save' Jirachi and do the transfer later. If you answer No to Prof. Oak, your current Jirachi will be lost, and you'll need to restart the RNG process from Step 3._

Start by opening [VBA -m](https://visualboyadvance.org/download/vba-m/), after having and configured it as per _Step 1_.<br>
In Dolphin, proceed through Prof. Oak's prompts asking if you wish to transfer the Jirachi, until the game asks you 'Are you ready?' after requesting that you connect your GBA to socket #2 of your GameCube. Press A to confirm you are ready, and the game will now request and wait for you to power on your GBA.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG18.png" width=720 height=504/></p><br>

Now in VBA -m, load your Ruby/Sapphire game. You should see a special screen in the GBA that confirms the transfer process being initiated, and then completed, as shown below:

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG19.png" width=720 height=504/></p><br>

Finally once the transfer is complete, you can reload your GBA emulator of choice and respective lua script, in order to confirm the stats of the Jirachi you obtained do indeed line up with the one you RNGd for!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GCN/Images/ChannelRNG20.png" width=480 height=320/>

***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the GCN Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GCN)_