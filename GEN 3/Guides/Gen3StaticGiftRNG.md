# Gen 3 Static / Gift RNG

This guide is meant to explain & teach you how to RNG Static & Gift Pokémon in the Gen 3 games.<br>
The process is presented here as done on, and with examples in `BizHawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to the latter noted where relevant.

## Getting Started

Required tools:
- [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [BizHawk](https://github.com/TASEmulators/BizHawk/releases); [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) or [mGBA](https://mgba.io/downloads.html) emulator
- A copy of any of the Gen 3 games

## Preparation & Basic Info

The various Static & Gift encounters found in the Gen 3 games are all very similar in the way you RNG them, with the differences usually lying solely in the location/final setup, as well as their [Offset](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#offset).<br>
Static Pokémon include both Legendary and non-Legendary (example: Kecleon) encounters, and are Pokémon that stand _static_ in the overworld, that you can interact with; Gift encounters are all the Pokémon that are given to you by NPCs, in one form or another, such as Starters, Fossils, etc.<br>

To trigger an encounter with a Static Pokémon, all you need to do is interact with them until the battle starts. This is usually done by pressing A on a final text box, or sometimes via taking a final step to a tile that triggers said encounter.
To receive a Gift Pokémon, you must interact with the specific NPC that gives them to you, and press A on a final text box that is usually accompanied by a `Yes? / No?` prompt.<br>

To see a full list of all Static & Gift Pokémon you can RNG across the Gen 3 games, and their respective setup & `Offset` values, you should check out the [Gen 3 Final Screens](https://github.com/Wi-Fi-Labs/Labs-Guides/wiki/Final-Screens-Gen3-RNG) page.<br>

In order to obtain better results, you should also familiarize yourself first with the [Gen 3 Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md) guide, as well as the [Pandora's Box](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md#pandoras-box) method, with the former being particularly important!<br>

Lastly, you should prepare your save by saving in front of your Static target, or Gift NPC.<br>

Below you will find the steps required to successfully perform this RNG.

## Step 1: Searching for Spreads & Initial Seed

Open [PokéFinder](https://github.com/Admiral-Fish/PokeFinder) and in the Gen 3 tab select the `Static` option. In the new window, select the appropriate profile and then open the 'Searcher' tab; in it configure the options as follows:
- RNG Info: Select `Method 1`. In normal gameplay, Statics & Gifts are always generated with this [Method](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods)
- Settings: Select the appropriate Category and the specific Pokémon
- Filters: Set the IV and other filters as you wish

Once you've configured all the necessary fields, click and run a 'Search'; PokéFinder should give you some results almost instantly.<br>
In our examples today, we will be aiming for both a Shiny Jolly 5IV -SpA Rayquaza and Beldum, both in Ruby as our Static & Gift targets, respectively, with a `PID` of `505C1B54` and Seed of `69A1BFEA` as shown below:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3StaticRNG1.png" width=1000 height=450/></p><br>
<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3GiftRNG1.png" width=1000 height=450/></p><br><br>


Once you have found a desired target, there's 2 different ways you should proceed, depending on which game you're RNGing on:
- For RS it is recommended that you use the [Live Battery RS](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#live-battery-rs) Initial Seed RNG method. Right-click the obtained 32bit (8-digit) Seed of your target, and select 'Generate times for seed'. This will open up the `Gen 3 Seed to Time` window; select your desired year and click 'Find' - Your target Seed should now ´convert´ to a suitable `Initial Seed`, and you'll have several combinations of Date & Time you can use to obtain said Initial Seed, as well as the target RNG `Advances` you will aim for. Below you can see this for our example:

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3StaticRNG2.png"</p><br><br>

- For FRLGE it is recommended that you use the [Emerald Painting / FRLG Initial Seed Bot](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#emerald-painting--frlg-initial-seed-bot) method. Copy the obtained 32bit (8-digit) Seed of your target over to [Lego's 'Painting-Seed' Tool](https://legofigure11.github.io/tools/painting-seed/), and find some suitable `Initial Seeds`. Use the Initial Seed Bot of the lua script to obtain one of these to perform your RNG:

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3StaticRNG2a.png"</p><br><br>

Once you have your target Initial Seed, it's time to move over to the 'Generator' tab of PokéFinder. Configure all the Settings and Filters as appropriate once more; in the 'RNG Info' part select/input the following:
- Method: Select Method 1 once more
- Seed: Input the Initial Seed you obtained previously
- Initial Advances: Can leave as 0. Alternatively input the `Advances` you're starting at with once you're ready for the RNG in-game and paused.
- Max Advances: Leave the default or increase to a value that allows for your target to be displayed
- Offset: Input the [Offset](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#offset) value for your target. Specific baseline values can be found on [this page](https://github.com/Wi-Fi-Labs/Labs-Guides/wiki/Final-Screens-Gen3-RNG) of Gen 3 Final Screens

Once the above is done click 'Generate' to have your target be displayed with the `Advances` you will aim for, accounting for the `Offset`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3StaticRNG3.png" width=1000 height=450/></p><br>
<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3GiftRNG3.png" width=1000 height=450/></p>

## Step 2: RNGing your target

Load up your game with the accompanying lua script, navigating to the `Capture` tab of the script for Statics, or `Pokémon Info / Mode: Gift` tab for Gifts, then position yourself at the [Final Screen](https://github.com/Wi-Fi-Labs/Labs-Guides/wiki/Final-Screens-Gen3-RNG) for your relevant target.<br>
Make a Save State at that point, and let the RNG advance until you're a few hundred `Advances` or so before your target, then pause the emulator. Manually advance what remains until you're at your target:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3StaticRNG4.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3GiftRNG4.png" width=480 height=320/></p><br>

Once you're at your target, hold the A button (or take a step) and un-pause the emulator. If you did everything correctly, you should see the desired attributes of your target appear in the lua script:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3StaticRNG5.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3GiftRNG5.png" width=480 height=320/></p><br>

Afterwards all that remains is catching your obtained Pokémon in the Poke Ball of your choice (for Statics), and checking your party:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3StaticRNG6.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3GiftRNG6.png" width=480 height=320/></p><br>

_Note: There is a tab of the lua script named `100% Catch` that allows you to RNG the catching sequence to guarantee a capture with whatever Ball you decide to use. This is quite useful if you're not using a Master Ball, so be sure to check it's instructions and give it a try!_

## Troubleshooting

If when holding A and un-pausing you don't obtain your expected `PID` and IV spread, it's likely that your `Offset` is slightly different than the standard one. This can happen depending on your emulator of choice or specific setup, but is usually never more than one or two off.<br>
To find out what your Offset actually is, configure the filters in the 'Generator' so that you can find the Pokémon you _actually_ got and compare it's `Advances` with the value you aimed for; then simply add or subtract the difference to your Offset value in the Offset box, and re-calculate your new target `Advances`.<br>
If you **overshot** your target (ie you hit something afterwards), you add the difference; if you **undershot** (ie you hit something earlier), you subtract the difference!<br>

If your `PID` was correct but your IV spread was only half correct, you probably fell victim to [VBlank interference](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#vblank) and got instead a [Method 4](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods) spread. While this is extremely rare during normal gameplay for Static & Gift Pokémon, it's not completely impossible.<br>
If you run into this issue, try a few of the solutions presented in the VBlank explanation page until you manage to obtain your target.

***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_