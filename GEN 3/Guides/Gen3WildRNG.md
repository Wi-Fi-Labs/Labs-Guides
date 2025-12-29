# Gen 3 Wild RNG

This guide is meant to explain & teach you how to RNG Wild Pokémon in the Gen 3 games, Wild including all of grass, cave, water, fishing encounters, and even Rock Smash.<br>
The process is presented here as done on, and with examples in `BizHawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to the latter noted where relevant.

## Getting Started

Required tools:
- [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [BizHawk](https://github.com/TASEmulators/BizHawk/releases); [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) or [mGBA](https://mgba.io/downloads.html) emulator
- A copy of any of the Gen 3 games

## Preparation & Basic Info

The various Wild encounter types have differing [Methods](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods) by which the Pokémon you encounter are generated. These methods and the probability of them occurring differ between RSFRLG and Emerald.<br>
When an encounter is generated with a non-expected Method, we say that a 'Method-shift' occurred. This is usually caused by [VBlank interference](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#vblank), which if it happens at the critical point in your RNG it can influence your result, where a different IV spread than what you desired occurs instead.<br>
Depending on your target's location and game, their [Offset](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#offset) will also be different.<br>

To trigger the various Wild encounter types when RNGing, the following methods are used:
- Grass, Cave & Water encounters are triggered by using **Sweet Scent** (recommended), or by turning/walking in the grass (FRLG only)
- Fishing encounters are triggered by pressing A when the character has had a 'bite' with the fishing rod
- Rock Smash encounters are triggered by pressing A on the last dialogue of the field move's animation

To obtain better results, you should familiarize yourself first with the [Gen 3 Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md) guide, as well as the [Pandora's Box](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md#pandoras-box) method, with the former being particularly important!<br>

Lastly, you should prepare your save by saving at the location where your target spawns before proceeding.<br>

Below you will find the steps required to successfully perform this RNG.

## Step 1: Searching for Spreads & Initial Seed

Open [PokéFinder](https://github.com/Admiral-Fish/PokeFinder) and in the Gen 3 tab select the `Wild` option. In the new window, select the appropriate profile and then open the `Searcher` tab; in it configure the options as follows:
- RNG Info: Select the appropriate or desired [Method](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods). In RSFRLG the most common is `Wild 1`, whereas in Emerald it is `Wild 2`. Make sure to specify the appropriate `Lead` as well, if using one for RNGing in Emerald.
- Settings: Select the Encounter type, Location and the specific Pokémon
- Filters: Set the IV and other filters as you wish

Once you've configured all the necessary fields, click and run a 'Search'; PokéFinder should give you some results almost instantly.<br>
In our example today, we will be aiming for a Shiny Jolly 5IV -SpA Wurmple in Ruby on Route 101, with a `PID` of `505C1B54` and Seed of `26C43323` as shown below:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3WildRNG1.png"</p><br><br>

Once you have found a desired target, there's 2 different ways you should proceed, depending on which game you're RNGing on:
- For RS it is recommended that you use the [Live Battery RS](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#live-battery-rs) Initial Seed RNG method. Right-click the obtained 32bit (8-digit) Seed of your target, and select 'Generate times for seed'. This will open up the `Gen 3 Seed to Time` window; select your desired year and click 'Find' - Your target Seed should now ´convert´ to a suitable `Initial Seed`, and you'll have several combinations of Date & Time you can use to obtain said Initial Seed, as well as the target RNG `Advances` you will aim for. Below you can see this for our example:

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3WildRNG2.png"</p><br><br>

- For FRLGE it is recommended that you use the [Emerald Painting / FRLG Initial Seed Bot](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#emerald-painting--frlg-initial-seed-bot) method. Copy the obtained 32bit (8-digit) Seed of your target over to [Lego's 'Painting-Seed' Tool](https://legofigure11.github.io/tools/painting-seed/), and find some suitable `Initial Seeds`. Use the Initial Seed Bot of the lua script to obtain one of these to perform your RNG:

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3WildRNG2a.png"</p><br><br>

Once you have your target Initial Seed, it's time to move over to the 'Generator' tab of PokéFinder. Configure all the Settings and Filters as appropriate once more; in the 'RNG Info' part select/input the following:
- Method: Select the Method you found your spread on in the `Searcher` tab
- Seed: Input the Initial Seed you obtained previously
- Initial Advances: Can leave as 0. Alternatively input the `Advances` you're starting at with once you're ready for the RNG in-game and paused.
- Max Advances: Leave the default or increase to a value that allows for your target to be displayed
- Offset: Input the [Offset](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#offset) value for your target. Specific baseline values can be found on [this page](https://github.com/Wi-Fi-Labs/Labs-Guides/wiki/Final-Screens-Gen3-RNG) of Gen 3 Final Screens

Once the above is done click 'Generate' to have your target be displayed with the `Advances` you will aim for, accounting for the `Offset`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3WildRNG3.png"</p>

## Step 2: RNGing your target

Load up your game with the accompanying lua script, navigating to the `Capture` tab of the script, then position yourself at the [Final Screen](https://github.com/Wi-Fi-Labs/Labs-Guides/wiki/Final-Screens-Gen3-RNG) for your relevant target.<br>
Make a Save State at that point, and let the RNG advance until you're a few hundred `Advances` or so before your target, then pause the emulator. Manually advance what remains until you're at your target:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3WildRNG4.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3WildRNG5.png" width=480 height=320/></p><br>

Once you're at your target, hold the A button (or take a step) and un-pause the emulator. If you did everything correctly, you should see the desired attributes of your target appear in the lua script. Afterwards all that remains is catching your obtained Pokémon in the Poke Ball of your choice, and checking your party:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3WildRNG6.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3WildRNG7.png" width=480 height=320/></p><br>

_Note: There is a tab of the lua script named `100% Catch` that allows you to RNG the catching sequence to guarantee a capture with whatever Ball you decide to use. This is quite useful if you're not using a Master Ball, so be sure to check it's instructions and give it a try!_

## Troubleshooting

If when holding A and un-pausing you don't obtain your expected `PID` and IV spread, it's likely that your `Offset` is slightly different than the standard one. This can happen depending on your emulator of choice or specific setup, but is usually never more than one or two off.<br>
To find out what your Offset actually is, configure the filters in the 'Generator' so that you can find the Pokémon you _actually_ got and compare it's `Advances` with the value you aimed for; then simply add or subtract the difference to your Offset value in the Offset box, and re-calculate your new target `Advances`.<br>
If you **overshot** your target (ie you hit something afterwards), you add the difference; if you **undershot** (ie you hit something earlier), you subtract the difference!<br>

If your `PID` was correct but your IV spread was only half correct, you probably fell victim to [VBlank interference](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#vblank) and got instead a spread generated through a different [Method](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods). This is not uncommon and tends to happen more on less accurate emulators (such as `VBA`).<br>
If you run into this issue, try a few of the solutions presented in the VBlank explanation page until you manage to obtain your target.

***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_