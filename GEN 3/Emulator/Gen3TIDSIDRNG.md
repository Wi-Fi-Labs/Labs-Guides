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
- [BizHawk 2.8-rc1](https://github.com/TASEmulators/BizHawk/releases/tag/2.8-rc1) or [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) emulator
- A copy of any of the Gen 3 games

## Preparation & Basic Info

When starting a new game, you'll get assigned a combination of a Trainer ID (TID), and Secret ID (SID). These values combined, make Pokémon with certain [Personality Values](https://bulbapedia.bulbagarden.net/wiki/Personality_value#Shininess), or `PID` for short, Shiny when encountered or received in-game.<br>
A common and efficient way of RNGing perfect Pokémon, is to use what's called the `Pandora's Box` method; which consists of first finding a `PID` for a given Nature & IV spread you would like to have Shiny, and then RNG your TID & SID combo in order to make it so. You can even combine a specific TID with a given PID for a twofold 'flex' on your RNGd Pokémon!<br>

`PokéFinder` (PF) is an RNG tool that allows you to calculate, search for and predict results of these values on a new save, which combined with certain actions performed in-game, at the right moment, allow you to obtain your desired TID & SID combo.<br>

The way you RNG this however, differs somewhat between RS and FRLGE, mostly due to the different methods by which Initial Seeds are generated in each game. You should check out the [Gen 3 Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Emulator/Gen3InitialSeedRNG.md) guide to learn more about this first, if you haven't yet.<br>
Below you will find a section for each of these different processes, fully explaining them, as well as a section on `Pandora's Box`. If you don't care about making a particular spread Shiny and just want to RNG a TID or SID for aesthetic reasons, you can just skip this first section, and go straight to the one for your game.
- [RS TID/SID RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Emulator/Gen3TIDSIDRNG.md#rs-tidsid-rng)
- [FRLGE TID/SID RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Emulator/Gen3TIDSIDRNG.md#frlge-tidsid-rng)

# Pandora's Box

The `Pandora's Box` method allows you to RNG a save's TID & SID combo, so that a specific `PID` (or pair of `PIDs`) can be made Shiny when encountered in-game. In this section I will explain how to do it, when you're preparing to RNG a new save's TID & SID.<br>

Open [PokéFinder](https://github.com/Admiral-Fish/PokeFinder) and in the Gen 3 tab select either the `Wild` or `Static` option. You can select `None` in profiles, since we're just looking for spreads right now, meaning the TID & SID from the profile is irrelevant.<br>
In the `Searcher` tab, configure the filters as you see fit, and after doing so click `Search`. In my examples below I searched for any Jolly -SpAtk IV spreads on both the `Wild` & `Static` tabs, and have decided on the Jolly 31/31/31/24/31/31 spread with a PID of `505C1B54`:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDPandora1.png"/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDPandora2.png"/></p><br>

If you want to get even more out of your TID RNG, you can also look for a specific 'Nature Pair'; which is a pair of two `PID` that share the exact same IV spread, but with different Natures. This is especially useful if you plan on RNGing many different Static or Wild Pokémon that prefer different Natures, as you won't have to TID RNG two different saves if you can find a desirable pair.<br>
These Nature Pairs can be visually identified by sharing the exact same IV spread as mentioned, and having only a different 1st and 5th digit. An example of this would be the perfect IV Timid + Modest or Calm + Modest pairs showcased in the image below:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDPandora3.png"/></p><br>

You can manually search for these pairs, or you can alternatively use [this nifty Google Sheet](https://docs.google.com/spreadsheets/d/1yrotkmuGlvQwI1qX8DgJkCVFkIeThHgA_Llbf48dxVI/edit?gid=875594700) that Labs user Unknown Warrior created, which can calculate different Nature Pairs for you.<br>

Once you're satisfied with your selected `PID` or Nature Pair, you can then proceed to the RNG proper.

# RS TID/SID RNG

In Pokémon Ruby & Sapphire, there are 2 ways you can approach TID/SID RNG depending on which Initial Seed method you want to use (Live Battery vs Dead Battery). For the purpose of this guide, we will be using the [RS Live Battery](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Emulator/Gen3InitialSeedRNG.md#live-battery-rs) method, which is the advised method for the sake of getting more options in terms of TID & SID combos, as well as the target `PID` obtained from the `Pandora's Box` method above.<br>

## Step 1: Searching for a TID/SID combo

There are also 2 ways to search for a desired TID/SID combo, which require a different tool between them, and are presented below:
- **Option A**: advised if you're doing the `Pandora's Box` method and want **a specific TID**; it requires [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) (an old PokéFinder fork with some extra features) and that you use the [RS Live Battery](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Emulator/Gen3InitialSeedRNG.md#live-battery-rs) method for the Initial Seed generation.
- **Option B**: advised if you're not doing the `Pandora's Box` method or don't care about a specific TID; it just requires the standard latest [PokéFinder](https://github.com/Admiral-Fish/PokeFinder).

_Important note: If you have an official PokeFinder 4.0.0 version or later installed, keep in mind you will need to have a separate `profiles.json` file just for Finder-Toolbox, in order to avoid conflicts. Follow [this PokeFinder profiles](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/MISC/DS/PokeFinderProfiles.md) management guide for more info!_<br>

_Note 2: It is also possible to RNG your save so that your desired spread, and Pokémon you obtain with it, are rendered as [Square Shiny](https://bulbapedia.bulbagarden.net/wiki/Shiny_Pok%C3%A9mon#Variants) in the SwSh games. This has no practical effect or meaning in any other games besides those Gen 8 titles, but if you're curious on what specific TID & SID combo gives your `PID` the Square Shiny trait, you can calculate it with [Lego's 'SID-For-Shiny' Tool](https://legofigure11.github.io/tools/sid-for-shiny/)._

### Option A: Searching with Finder-Toolbox

Open [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) and in the Gen 3 tab select the `TID/SID` option. In the new window, select the `Gen III RS Search` tab, and input your target `PID` and desired `TID`; after this just click 'Search'.<br>
You should now have a few results for Dates + Times where you'll get a combo of your desired TID + an SID that will make your desired `PID` Shiny - including if it will be Square Shiny when transferred over to SwSh. If no Square Shiny option appears, it unfortunately means that there is no Initial Seed where that specific TID+SID combo is possible.<br>
On the example below we will be selecting the option that gives us the Initial Seed `CA23`, as it gives us the Square Shiny combo (for aesthetic reasons).<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS1.png"/></p>

_Note: All of the Dates are calculated in the year 2000, as this window can't search for the specific combos in other years; however if you want to start your save in a different year, you can get a different date & time that will give you this Initial Seed by using the feature `Gen 3 Tools > Seed To Time` that you can find in the main window menu._

### Option B: Searching with PokéFinder

Open [PokéFinder](https://github.com/Admiral-Fish/PokeFinder) and in the Gen 3 tab select the `IDs` option. In the new window, select the `RS` tab - here you can input a variety of values you'd like to search for. Because we're using the `Pandora's Box` method, we want a TID & SID that will make our `PID` Shiny above all else, so we select the PID option and input it there; after this you would select a given Date & Time you'd like to start your game at (or check Dead Battery if you're using that method), a maximum amount of advances you're willing to wait/go for, and click 'Search'.<br>
You should now have a few results for different TID/SID combos that make your `PID` Shiny! Simply select one of them as your target, and note the required RNG advancements. If you want to know if any of the results will yield a Square Shiny combo, you can check the values with [Lego's 'SID-For-Shiny' Tool](https://legofigure11.github.io/tools/sid-for-shiny/).<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS2.png"/></p>

## Step 2: RNGing the TID & SID

Once you've found a suitable target from either of the 2 search methods above, you can now proceed with the RNG proper! For this example we shall be using the option that gives us the Initial Seed `CA23`, that we found with [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) above.<br>

Load your emulator & game with the required Date & Time (in my case `04/02/2000 15:57:00`), and then load the `RS_RNG_BizHawk_SM` script in the `Pandora` tab - if you set everything correctly, you should get your target Initial Seed.<br>
Start a New Game, selecting your gender and entering your desired character name, proceeding all the way until you reach the screen shown below:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS3.png"  width=480 height=320/></p><br>

Upon pressing A on this screen, your TID & SID will be generated; let the RNG advance until you're ~200 frames before your target, pause the game and make a save state so that you can return to this point if something goes wrong or you miss your frame.<br>
The reason we pause at this point is because there is a delay of around `-75` frames between the moment you press A and your TID & SID are actually generated, due to the character shrinking animation. In this case, given a target advance of `46031`, this means we should hold A and un-pause on this screen at advances `45956`.<br>
While paused, manually advance until you reach this calculated value. Once you're there, hold A and un-pause - you should see your desired TID & SID appear at the bottom right corner of the script, once you're in the back of the moving truck!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS4.png"  width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS5.png"  width=480 height=320/></p>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS6.png"  width=480 height=320/></p><br>

### Troubleshooting

If your obtained TID & SID combo doesn't match what is expected, it is advised to make a few practice runs at the final screen, restoring to your previous save state, to properly calibrate your delay for this situation, as it may differ slightly from `-75`.<br>
Alternatively you can also use the IDs' window RS tab in [PokéFinder](https://github.com/Admiral-Fish/PokeFinder), as per the example below, to check which frame you are actually hitting and from there re-calculate your actual delay.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDRS7.png"/></p>

# FRLGE TID/SID RNG

In Pokémon Emerald, FireRed & LeafGreen the TID & SID are generated separately, where the TID is generated upon pressing A on `END` when selecting your character's name, and the SID is generated when pressing A on the last dialogue from the Professor, before the shrinking down animation of your character.<br>
Because the TID generation is based on a parameter that changes very quickly, it's more practical to actually bot for a TID and then RNG the SID, than attempting to RNG both values. Such a TID Bot is one of the features of the Emerald and FRLG lua scripts, which performs a series of rapid Save State and Save Restores to accomplish this.<br>
Unlike in RS, you also don't need to RNG a specific Initial Seed or search for a specific TID/SID combo beforehand in these games.<br>
There are 2 ways to tackle FRLGE TID/SID RNG, assuming you're doing the `Pandora's Box` method:
- If you **want a specific TID**, you should follow the guide below in it's entirety.
- If you **do not** want a specific TID, you can skip Step 1.

## Step 1: Botting for a target TID

Using PokéFinder or FinderToolbox to search for results won't be required, as you will be botting the TID - instead you must first must specify some desired TIDs as your targets for the TID Bot in the lua script. This is done by opening the `E_RNG_BizHawk_SM` or `FRLG_RNG_BizHawk_SM` script in a text editor like Notepad, and navigating to the following line, pasting the target TID values between the brackets, as shown below (don't forget to save the file when done):<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDFRLGE1.png"/></p><br>

The more TIDs you specify, the faster the Bot will find a result, so keep that in mind if you're not too picky for a very specific TID!<br>

After the above is done, load your emulator & game together with the `E_RNG_BizHawk_SM` or `FRLG_RNG_BizHawk_SM` script in the `TID Bot` tab. Open the Bot's instructions and follow them after starting a New Game - the instructions are similar between `BizHawk/mGBA` and `VBA`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDFRLGE2.png"  width=480 height=320/></p><br>

As you un-pause at the end of the instructions above, the Bot should start resetting the name selection screen over and over, flashing the screen in the process. It's advisable to _turbo_ your emulator, so as to speed up the process as much as you can, and reduce the overall time spent waiting for the Bot to find a TID.<br>
Once the bot finds a result, it pauses the emulator immediately. As soon as you un-pause, you'll see the script display a `Found!` message as shown below, listing what TID from your list it found. In my example here it found `44444`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDFRLGE3.png"  width=480 height=320/></p>

_Note: If all you care about is your TID and you're not using the `Pandora's Box` method, then you're all set after this and can skip the rest of this guide._<br>

## Step 2: RNGing the SID

Once you check what TID you got, change the script to the `Pandora` tab, progress until you reach the final screen as shown below, pause the emulator again and perform a save state.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDFRLGE4.png"  width=480 height=320/></p>

_Note: The final screen for FRLG is when you're at the second-to-last textbox that reads "Your own very Pokémon legend is about to unfold!"_<br>


Now that we have our TID, it's time to make the preparations to RNG our SID! For the purpose of this guide, we will be using the `PID` value obtained from the `Pandora's Box` method above as our target; so we'll now want to RNG an SID that, together with our obtained `44444` TID will make the `PID` value `505C1B54` and its corresponding spread Shiny.<br>
To accomplish this, we will be using the [Gen 3 TID/SID Frame Finder](https://github.com/DevonStudios/Gen3TIDSIDFrameFinder/releases) tool, so open it and set up the `Config` fields as below, and press 'Find Frame To Hit' button to generate results:
- **TID**: Your obtained TID in the previous step
- **Desired PID**: The `PID` you want to make Shiny
- **PRNG State**: The `Current Seed` value as displayed in the Lua script
- **Starting Frame**: The current `Advances` value as displayed in the Lua script
- **Max Results**: The maximum amount of advances you're willing to wait

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDFRLGE5.png"/></p>

_Note 2: It is also possible to RNG your save so that your desired spread, and Pokémon you obtain with it, are rendered as [Square Shiny](https://bulbapedia.bulbagarden.net/wiki/Shiny_Pok%C3%A9mon#Variants) in the SwSh games. This has no practical effect or meaning in any other games besides those Gen 8 titles, but if you're curious on what specific TID & SID combo gives your `PID` the Square Shiny trait, you can calculate it with [Lego's 'SID-For-Shiny' Tool](https://legofigure11.github.io/tools/sid-for-shiny/)._<br>


Pick one of the results the tool above gives you and note the target 'frame' or advancement to hit; usually you would pick the earliest one, unless you'd like a specific SID as per the note above.<br>
In this case I don't particularly care about the Shiny type, so I'll just go for the first result, with a target advancement of `24930` and an SID of `59029`. Un-pause your emulator and let the game run until you're at about ~500 frames before your target, then pause it again and make a new Save State.<br>
The reason we pause at this point is because there is a delay between the moment you press A at the final screen, and your SID is actually generated, due to the character shrinking animation. This value is usually `-75` for Emerald and `-465` for FRLG. In this case, given a target advance of `24930`, this means we should hold A and un-pause on this screen at advances `24855`.<br>
While paused, manually advance until you reach this calculated value. Once you're there, hold A and un-pause - you should see your desired TID & SID appear at the bottom right corner of the script, once you're in the back of the moving truck (Emerald) or you're in your room in Pallet Town (FRLG)!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDFRLGE6.png"  width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDFRLGE7.png"  width=480 height=320/></p>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDFRLGE8.png"  width=480 height=320/></p>

### Troubleshooting

If your obtained TID & SID combo doesn't match what is expected, you can use the [Gen 3 TID/SID Frame Finder](https://github.com/DevonStudios/Gen3TIDSIDFrameFinder/releases) tool to properly calibrate your delay for this situation, as it may differ slightly from the default values mentioned above.<br>
In the example below, I attempted to hit my target without considering any delay, so I would now like to calibrate it; to do this set up the `Frame Correction` fields as below, and press the 'Adjust Frame' button:
- **Attempted Frame:** The advancements value at which you pressed A on
- **Acquired SID:** The SID value you obtained instead of your target one as displayed in the Lua script

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Emulator/Images/G3TIDSIDFRLGE9.png"/></p>

The tool will then calculate your delay as 'Frame Offset', and display what advancement you should actually hold A on, in order to hit your target!<br><br>

_Note: If you don't want to use the `Pandora's Box` method, but you still want to RNG a specific SID, you can use [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)'s `FRLGE ID's` tab from the Gen 3 section, in a similar manner that Gen 3 TID/SID Frame Finder is used above, in order to do so._<br>

***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_