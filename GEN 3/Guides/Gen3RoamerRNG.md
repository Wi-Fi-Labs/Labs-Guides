# Gen 3 Roamer RNG

This guide is meant to explain & teach you how to RNG Roamer Pokémon in the Gen 3 games, namely the Lati twins in RSE & the three Legendary Beasts in FRLG.<br>
The process is presented here as done on, and with examples in `BizHawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to the latter noted where relevant.

## Getting Started

Required tools:
- [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [BizHawk 2.8-rc1](https://github.com/TASEmulators/BizHawk/releases/tag/2.8-rc1); [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) or [mGBA](https://mgba.io/downloads.html) emulator
- A copy of any of the Gen 3 games

## Preparation & Basic Info

Roamer RNG consists of manipulating the attributes of a generated Roaming Pokémon (such as IVs, Nature, Ability, etc) which are 'released' at specific moment in the game, usually in the post-game.<br>
The Roamers available in the Gen 3 games are:

|   Game   |        Roamer       |                        Notes                      |
| :------: | :-----------------: | :-----------------------------------------------: |
|   Ruby   |        Latios       |                          -                        |
| Sapphire |        Latias       |                          -                        |
| Emerald  |  Latios or Latias   |                 _Player's choice_                 |
|   FRLG   | One Legendary Beast | _Decided by the type advantage over your Starter_ |

In **RS & FRLG**, an unfortunate bug is present, that prevents the Roamer Pokémon from being able to have perfect, or even adequate IV spreads. This bug is known as the [Roaming Pokémon IV bug](https://bulbapedia.bulbagarden.net/wiki/List_of_battle_glitches_in_Generation_III#Roaming_Pok%C3%A9mon_IV_bug).<br>

Another bug [that is present](https://bulbapedia.bulbagarden.net/wiki/Roaming_Pok%C3%A9mon#Generation_III) in **FRLG & Emerald** specifically, is that if a Roaming Pokémon uses Roar or Whirlwind, the game considers the Pokémon to have been defeated, and as such it cannot be re-battled. In practice this only affects Raikou & Entei in FRLG specifically, as the others cannot learn either of these moves by level up. Still precautions should be taken to avoid losing these altogether.<br>

Unlike what you'd usually do for both [Wild](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3WildRNG.md) and [Static/Gift](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3StaticGiftRNG.md) RNG, for the purpose of Roamer RNG, whether you did [TID/SID RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md) for your save with the [Pandora's Box](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md#pandoras-box) method or not is somewhat irrelevant due to the aforementioned IV bug. The only exception is for Emerald, where you _can_ get good IV spreads, but these come at a **very high cost** in terms of time, due to the inability to manipulate the `Initial Seed` on Emerald in this specific scenario (and as such you are stuck with `Initial Seed: 0000`).<br>
While not strictly necessary to perform this RNG, it is also recommended that you read up on and learn [Gen 3 Initial Seed RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md) if you haven't yet.<br>

Lastly, you should prepare your save by saving immediately before the moment the Roamer is released. This is when in your bedroom immediately after you first defeated the E4 and entered the Hall of Fame (RSE), or immediately before you enter the Pokémon Network Center at One Island, to give Ceilo the Sapphire for his machine (FRLG).<br>

Below you will find the steps required to successfully perform this RNG. Ensure you are already saved in game at the absolute last position before the Roamer is generated before proceeding.

## Step 1: Searching for Spreads & Initial Seed

Open [PokéFinder](https://github.com/Admiral-Fish/PokeFinder) and in the Gen 3 tab select the `Static` option. In the new window, select the appropriate profile and then open the 'Searcher' tab; in it configure the options as follows:
- RNG Info: Select `Method 1`. In normal gameplay, Statics (of which Roamers are a sub-type) are always generated with this [Method](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods)
- Settings: Category `Roamers` and the applicable Pokémon
- Filters: Set the IV and other filters as you wish, keeping in mind the limitations of the IV bug mentioned previously for RSFRLG

Once you've configured all the necessary fields, click and run a 'Search'; PokéFinder should give you some results almost instantly.<br>
In our example today, we will be aiming for a Shiny all 0IV Serious Latios in Ruby, with a `PID` of `C76C9D62` and Seed of `749D57B2` as shown below:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3RoamerRNG1.png"</p><br><br>

Once you have found a desired target, there's 3 different ways you should proceed, depending on which game you're RNGing on:
- For RS it is recommended that you use the [Live Battery RS](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#live-battery-rs) Initial Seed RNG method. Right-click the obtained 32bit (8-digit) Seed of your target, and select 'Generate times for seed'. This will open up the `Gen 3 Seed to Time` window; select your desired year and click 'Find' - Your target Seed should now ´convert´ to a suitable `Initial Seed`, and you'll have several combinations of Date & Time you can use to obtain said Initial Seed, as well as the target RNG `Advances` you will aim for. Below you can see this for our example:

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3RoamerRNG2.png"</p><br><br>

- For FRLG it is recommended that you use the [FRLG Initial Seed Bot](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#emerald-painting--frlg-initial-seed-bot) method. Copy the obtained 32bit (8-digit) Seed of your target over to [Lego's 'Painting-Seed' Tool](https://legofigure11.github.io/tools/painting-seed/), and find some suitable `Initial Seeds`. Use the Initial Seed Bot of the lua script to obtain one of these to perform your RNG:

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3RoamerRNG2a.png"</p><br><br>

- For Emerald there is nothing to do at this stage, since we won't be able to manipulate the `Initial Seed` before or during this RNG, as none of the methods used to do so are available.<br><br>

Once you have your target Initial Seed, it's time to move over to the 'Generator' tab of PokéFinder. Configure all the Settings and Filters as appropriate once more; in the 'RNG Info' part select/input the following:
- Method: Select Method 1 once more
- Seed: Input the Initial Seed you obtained previously
- Initial Advances: Can leave as 0. Alternatively input the `Advances` you're starting at with once you're ready for the RNG in-game and paused.
- Max Advances: Leave the default or increase to a value that allows for your target to be displayed
- Offset: Input the [Offset](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#offset) value for your Roamer RNG. Specific baseline values can be found on [this page](https://github.com/Wi-Fi-Labs/Labs-Guides/wiki/Final-Screens-Gen3-RNG) of Gen 3 Final Screens

Once the above is done click 'Generate' to have your target be displayed with the `Advances` you will aim for, accounting for the `Offset`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3RoamerRNG3.png"</p>

## Step 2: RNGing the Roamer

Load up your game with the accompanying lua script, navigating to the `Capture` tab of the script, and pressing 3 to open the Roamer Info, then position yourself at the [Final Screen](https://github.com/Wi-Fi-Labs/Labs-Guides/wiki/Final-Screens-Gen3-RNG) for your relevant Roamer/Game.<br>
Make a Save State at that point, and let the RNG advance until you're a few hundred `Advances` or so before your target, then pause the emulator. Manually advance what remains until you're at your target.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3RoamerRNG4.png" width=480 height=320/></p><br>


Once you're at your target, hold the A button and un-pause the emulator. If you did everything correctly, you should see your Roamer, with the desired attributes appear in the `Roamer Info` box of the lua script:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3RoamerRNG5.png" width=480 height=320/></p>

## Step 3: Hunting down and catching your Roamer

Now that your Roamer is wandering the Region, you need to hunt it down in order to catch it! Luckily the lua script includes a function that displays where the Roamer is located at any given moment, making cornering it a much easier task.<br>
Our recommendation is to fly to Mauville City and keep moving back and forth between the City and the 4 adjacent Routes, until it moves into the same Route as you. Once this happens, the Roamer's position will be coloured green in the script:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3RoamerRNG6.png" width=480 height=320/></p><br>

Once you have it in the same Route as you, make a Save State (so that you don't have to hunt it down again), and walk into the tall grass/surf around until you encounter it.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3RoamerRNG7.png" width=480 height=320/></p><br>

Finally all that's left now is catching your Roamer:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3RoamerRNG8.png" width=480 height=320/></p>

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