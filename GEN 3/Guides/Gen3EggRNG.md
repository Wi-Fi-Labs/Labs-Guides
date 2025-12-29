# Gen 3 Egg RNG

This guide is meant to explain & teach you how to RNG Pokémon from Eggs in the Gen 3 games.<br>
The process is presented here as done on, and with examples in `BizHawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to the latter noted where relevant.

## Getting Started

Required tools:
- [PokéFinder](https://github.com/Admiral-Fish/PokeFinder)
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [BizHawk](https://github.com/TASEmulators/BizHawk/releases); [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) or [mGBA](https://mgba.io/downloads.html) emulator
- A copy of any of the Gen 3 games

## Preparation & Basic Info

Egg RNG in Gen 3 consists of manipulating the attributes of a generated Egg (such as IVs, Nature, Ability, etc), obtained by breeding with two suitable parents.<br>

Here we will learn to use PokéFinder (PF) to calculate, search for and predict results of all Egg attributes, which combined with certain actions performed in-game, at the right moment, will allow you to obtain your desired Pokémon.<br>

The way you perform this RNG differs considerably between RSFRLG and Emerald due to programming differences between these games, each using their own exclusive method respectively.<br>

Below you will find a section for each of these two processes, fully explaining them:
- [RSFRLG Egg RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3EggRNG.md#rsfrlg-egg-rng)
- [Emerald Egg RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3EggRNG.md#emerald-egg-rng)

# RSFRLG Egg RNG

In RS & FRLG the [Personality Value](https://bulbapedia.bulbagarden.net/wiki/Personality_value#Shininess), or `PID` for short, of an Egg is determined at 2 different stages; the second half of the `PID` (called `Low PID`) is determined when the Egg is generated in the Day Care, while the first half (called `High PID`) is determined when you receive it from the Day-Care Man. The IVs of the Egg are also determined when you receive the Egg.<br>
Unlike in Emerald or later Generations, in these games held items don't have any effect on the breeding process, so you can't increase your odds of, for example passing down Nature, by having a parent hold an Everstone (as is the case in later Generations).<br>

Due to the `PID` being determined in 2 separate steps, this RNG involves targeting 2 different RNG `Advances` values, commonly referred to as `Held Advances` & `Pickup Advances`, which will be your target for when the Egg is generated, and redeemed, respectively.<br>

To perform this RNG more efficiently in Ruby & Sapphire specifically, it's recommended that you use the [Live Battery RS](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#live-battery-rs) method for the `Initial Seed` generation, or that you simply set your emulator to use your computer's RTC. For FireRed & LeafGreen no Initial Seed RNG is required.

## Step 1: Setting up in the Day-Care

Make your way to the Day-Care if you're not already in there, which is located in Route 117 (RS) / Four Island (FRLG), and deposit both Pokémon that will be the Parents for your desired Pokémon with the Day-Care Lady. It is recommended that you have Parents with as high compatibility as possible; you can check what determines compatibility in [this Bublapedia article](https://bulbapedia.bulbagarden.net/wiki/Pok%C3%A9mon_breeding#Breeding_rate).<br>
If you're aiming for perfect IVs or otherwise competitive IV spreads, both your parent Pokémon should also have perfect IVs or as close as possible to them, as this makes it easier to find desirable IV spreads.<br>
Lastly, if you're wanting to transfer some Egg Moves to the offspring, make sure the Male parent is the one who knows them, as in Gen 3 only Males pass down Egg Moves! In our example here, we will be using a Salamence with 4 Egg Moves as the Male parent, and a Ditto as the 'Female' parent, both with perfect IVs (ie 6IV) and from different OT & TID.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG1.png" width=320 height=213/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG2.png" width=320 height=213/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG3.png" width=320 height=213/></p><br>

Once you've deposited both your Parents, save your game while inside the Day-Care.<br>

Restart your game, this time loading the `RS_RNG_BizHawk_SM` script, and cycle to its `Breeding` tab. You'll notice there's a line that reads `Steps Counter: xx`, which is a counter that tells you how many steps need to be taken in-game in order to have a chance of an Egg being generated (this chance is based on the compatibility of your Parents, as mentioned above).<br>
Once this counter reaches 0, an Egg will be generated (or not!), with the counter resetting back to 255 steps, and the cycle begins anew. This 255 step cycle is what's commonly referred to as an [Egg Cycle](https://bulbapedia.bulbagarden.net/wiki/Egg_cycle), which is also what determines if a given Egg will hatch when walking with it in your party.<br>

For this RNG, you want to walk inside the house until the `Steps Counter` reads 1. Once it does, stop moving, save the game once more while inside the Day-Care and restart your game with the lua script loaded in the Breeding tab again. Once you're loaded back in your game like the screen below, pause the emulator.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG4.png" width=480 height=320/></p>

## Step 2: Searching for a target PID & IV spread

Open [PokéFinder](https://github.com/Admiral-Fish/PokeFinder) and select the `Egg` option from the Gen 3 tab. In the new window, select the `RS/FRLG` tab and make sure to select the respective profile for your game and specific save.<br>
Now fill in or specify all the relevant fields in the `RNG Info`, `Settings` & `Filters` sections:
- **RNG Info**:
  - **Seed (Held / Pickup)**: Fill both these boxes with whatever `Initial Seed` you got after reloading your game above.
  - **Held Advances**: Enter the starting `Advances` value in the first box, and the maximum number of advances you're willing to wait for the Egg generation (usually 10000 is enough).
  - **Pickup Advances**: Enter whatever value you input in the second box above in the first box here, and the maximum number of advances you're willing to wait for the Egg pickup (usually 500000 is enough).
  - **Offset (Held / Pickup)**: These boxes are to account for the delay (Offset) between the moment you take a step/hold A and the Egg is generated/redeemed, respectively. The default values for `BizHawk` are 17 / 3, whereas for `VBA` & `mGBA` they are 17 / 4.
  - **Method**: Select `Normal` by default. More information on the other options will be provided in the `Troubleshooting` step below.
  - **Compatibility**: Select the Compatibility of your Parents.
- **Settings**: 
  - Specify the IVs & Gender of both `Parent A` and `Parent B`.
  - Specify what `Egg Species` you intend to obtain.
- **Filters**: Specify all the details you'd like for your desired Egg to have.

Once you've finished setting up all the fields above, click `Generate`. PokéFinder will now search for a few minutes and try to find a suitable Egg within a combination of `Advances` values for both generating the Egg & receiving the Egg. There is no progress bar on this window and it will be frozen until the search is complete, so you just have to be patient.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG5.png"</p><br>

With an Initial Seed of `3BEE` and the specified search ranges, PokéFinder was able to find us a suitable Egg with the `PID: 144C09CB`, and `Held` & `Pickup` Advances values of 8055 & 312902 respectively. These are the values you will be targeting when generating and receiving the Egg respectively, in the last step below.<br>

_Note: If PokéFinder doesn't find any results, you have 2 options: reset the emulator so that you can get a new `Initial Seed` and perform a new search, or increase the `Pickup Advances` search range. The former is advised as it's the more efficient method, although the latter is perfectly valid for FRLG in particular due to the availability of a method to advance RNG advances much quicker, which we will get into detail in the next step._

## Step 3: RNGing the Egg

Now that you have your target values you can proceed to perform the RNG proper! During the whole process it is advised that you make use of save states as much as possible at every key step, so as to safeguard any mistake or missing target RNG `Advances`, and avoid having to restart the game and redo all of it.<br>

Un-pause your emulator and let the RNG advance until you're at your target `Held Advances`. You should pause a few `Advances` before your target and advance the RNG manually to avoid overshooting it. Once at the target, hold the D-Pad arrow of the direction your character is facing, and un-pause your emulator to take a step forward.<br>
If you did it correctly, your Egg `Low-PID` should now be displayed in the script. Below you can see the key moments, at target and immediately afterwards for our example:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG6.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG7.png" width=480 height=320/></p><br>

After the above, you will now let the RNG advance until you are around ~2000 `Advances` before your `Pickup Advances` target, while still inside the Day-Care, which should give you more than enough time to interact with the Day-Care Man.<br>

_Note 1: This is where doing this RNG in FRLG has an advantage over RS if your target is several hundred thousands or millions of `Advances` away, as you can open the Key Item [Teachy TV](https://bulbapedia.bulbagarden.net/wiki/Teachy_TV) in order to make the RNG advance 313x faster. Combine this with turbo-ing up your emulator, and millions of `Advances` will go by in seconds!_<br>

As you reach 2000 or thereabouts `Advances` before your target, head outside and interact with the Day-Care Man until you're at his last dialogue "Take good care of it.". Just like in the step before, you should pause a few `Advances` before your target and advance the RNG manually to avoid overshooting it. Once at the target, hold the A button, and un-pause your emulator to redeem the Egg.<br>
If you did it correctly, the redeemed Egg's attributes should now be listed in the script. Below you can see the key moments, at target and immediately after Egg redemption for our example:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG8.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG9.png" width=480 height=320/></p><br>

If you followed this guide properly, the Egg you obtained should match exactly what you aimed for in PokéFinder, and now all you have to do is to speed around in your Bike for it to hatch!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggRSFRLG10.png" width=480 height=320/></p><br>

_Note 2: If either the PID or IVs of the generated Egg, or both, do not match what was expected, please read the `Troubleshooting` step below._

### Troubleshooting

If you followed the guide above properly but an Egg was not generated when taking the final step, or it was generated with the wrong `Low-PID`, it is likely because your `Offset Held` is slightly different than the standard value listed above, which may happen depending on your specific setup.<br>
To calibrate your own `Offset Held` value, simply restore a save state from before you took that last step and try doing so at plus or minus 1 `Advances` from your previously calculated target; if you do get your expected `Low-PID` then, you will have found your actual `Offset Held` value!<br>
While unlikely that you would be off by more or less than 1, repeat this procedure for plus or minus 2, then 3 etc, until you find the correct `Offset Held` value for your setup.<br>

If you followed the guide above properly but still your Egg's IVs were not what you wanted and expected, you likely encountered a different [Egg Method](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#egg-methods) than the one you were targeting (which PokeFinder assumes as the `Normal` one by default).<br>
The first thing you must know, if this happens to you, is that there is no way to change the Method your game is using to generate the Egg's IVs, without changing one or both of the parents; and even if you do so, there's no way to control or predict which Method you'll be getting still!<br>
So what should you do? To figure out what method is actually being used, you should redo the search in PokéFinder by narrowing the search range to include the RNG `Advance` you redeemed the Egg at, while selecting a different Method from the corresponding dropdown one by one, with the IV filters changed to the IV spread you _actually_ obtained, until said IV spread appears as a result on your target `Pickup Advances`. Whatever Method makes that IV spread appear is the Method your game is currently using due to your Egg's parents!<br>
You'll notice that in our example for the guide above, we used the `Mixed` method for our search - this is precisely because we weren't getting our desired IV spread with the `Normal` method, so after performing the searching above, we determined our Egg was being generated with the `Mixed` method.<br>

Once you've pinpointed what method your game is using, you can now try and search for your desired spread with it selected on the same `Initial Seed`. If you don't find any results, even after extending the `Pickup Advances` search range, then unfortunately your only choice is to try a different seed and restarting the RNG process again from **Step 2** in the guide.

# Emerald Egg RNG

In Emerald the [Personality Value](https://bulbapedia.bulbagarden.net/wiki/Personality_value#Shininess), or `PID` for short, of an Egg is determined when the Egg is generated in the Day Care, while the IVs of the Egg are determined when you receive the Egg.<br>
As you probably already know, starting with Emerald held items can have effects on the breeding process, the most commonly known and used in this game being the Everstone, which can increase your odds of passing down the Nature of the Parent holding it; however, and counter-intuitively, this is actually detrimental when we're trying to RNG an Egg as it exponentially increases the [VBlank interference](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#vblank), so **refrain** from making either of the Parents hold the Everstone.<br>

Due to the `PID` and the IVs being determined in 2 separate steps, this RNG involves targeting 2 different RNG `Advances` values, commonly referred to as `Held Advances` & `Pickup Advances`, which will be your target for when the Egg is generated, and redeemed, respectively. The `Held Advances` are also targeted on another value that the lua script tracks, other than the standard RNG `Advances`, which is called the `Timer`.<br>
For this RNG in Emerald there is also another aspect to consider, which is the `Redraws` value. This is essentially the amount of times you will have to open and close your PokéDex before reaching your target values.<br>

Also worth mentioning, is the fact that as Emerald has the known programming bug of always loading with the `Initial Seed: 0000`, and PokéFinder currently only supports this, no Initial Seed manipulation is required or supported for this RNG.

## Step 1: Setting up in the Day-Care

Make your way to the Day-Care if you're not already in there, which is located in Route 117, and deposit both Pokémon that will be the Parents for your desired Pokémon with the Day-Care Lady. It is recommended that you have Parents with as high compatibility as possible; you can check what determines compatibility in [this Bublapedia article](https://bulbapedia.bulbagarden.net/wiki/Pok%C3%A9mon_breeding#Breeding_rate).<br>
If you're aiming for perfect IVs or otherwise competitive IV spreads, both your parent Pokémon should also have perfect IVs or as close as possible to them, as this makes it easier to find desirable IV spreads.<br>
Lastly, if you're wanting to transfer some Egg Moves to the offspring, make sure the Male parent is the one who knows them, as in Gen 3 only Males pass down Egg Moves! In our example here, we will be using a Salamence with 4 Egg Moves as the Male parent, and a Ditto as the 'Female' parent, both with perfect IVs (ie 6IV) and from different OT & TID.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE1.png" width=320 height=213/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE2.png" width=320 height=213/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE3.png" width=320 height=213/></p><br>

Once you've deposited both your Parents, save your game while inside the Day-Care.<br>

Restart your game, this time loading the `E_RNG_BizHawk_SM` script, and cycle to its `Breeding` tab. You'll notice there's a line that reads `Steps Counter: xx`, which is a counter that tells you how many steps need to be taken in-game in order to have a chance of an Egg being generated (this chance is based on the compatibility of your Parents, as mentioned above).<br>
Once this counter reaches 0, an Egg will be generated (or not!), with the counter resetting back to 255 steps, and the cycle begins anew. This 255 step cycle is what's commonly referred to as an [Egg Cycle](https://bulbapedia.bulbagarden.net/wiki/Egg_cycle), which is also what determines if a given Egg will hatch when walking with it in your party.<br>
Below the `Steps Counter`, you will also see two other important lines, `Timer` and `Calibration`; you'll make use of these in the steps below.<br>

For this RNG, you want to walk inside the house until the `Steps Counter` reads 1. Once it does, stop moving, save the game once more while inside the Day-Care and restart your game with the lua script loaded in the Breeding tab again. Once you're loaded back in your game like the screen below, pause the emulator.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE4.png" width=480 height=320/></p>

## Step 2: Searching for a target PID & IV spread

Open [PokéFinder](https://github.com/Admiral-Fish/PokeFinder) and select the `Egg` option from the Gen 3 tab. In the new window, select the `Emerald` tab and make sure to select the respective profile for your game and specific save.<br>
Now you need to fill in or specify all the relevant fields in the `RNG Info`, `Settings` & `Filters` sections. For Emerald in PokéFinder, it is **much** faster to search for the PID and IVs separately instead of all in one, so that's the option we'll present here.<br>
We shall start with the `PID` search first, so configure the window as such:
- **RNG Info**:
  - **Held Advances**: Enter the starting `Advances` value in the first box, and the maximum number of advances you're willing to wait for the Egg generation (usually 50000 is more than enough).
  - **Pickup Advances**: We won't be searching for IVs now so enter the starting `Advances` value in the first box, and 0 in the second box.
  - **Offset (Held / Pickup)**: These boxes are to account for the delay (Offset) between the moment you take a step/hold A and the Egg is generated/redeemed, respectively. The default values for `BizHawk` are 16 / 3, whereas for `VBA` & `mGBA` they are 17 / 4.
  - **Calibration**: Enter the value displayed after `Calibration` in the lua script here.
  - **Redraws**: Enter a range of Redraws to make here. Usually 0-10 is more than enough.
  - **Method**: Also unused for `PID` searching. Leave on the default for now.
  - **Compatibility**: Select the Compatibility of your Parents.
- **Settings**: 
  - Specify the IVs & Gender of both `Parent A` and `Parent B`.
  - Specify what `Egg Species` you intend to obtain.
- **Filters**: Specify all the details you'd like for your desired Egg to have **except** IVs - leave these on default.

Once you've finished setting up all the fields above, click `Generate`. PokéFinder should give you some results almost instantly and find a suitable `PID` for your specifications:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE5.png"</p><br>

In our example we will be going with the `PID: FAFC3076` which gives us a Shiny Adamant Bagon. Make note of the `Held Advances` & `Redraw` values; in our example these are 14586 and 7 respectively, which means we will be targeting a `Timer` value of 14586, while opening and closing the PokéDex 7 times beforehand.<br>

Now we move onto the IV spread search, so configure the window as such:
- **RNG Info**:
  - **Held Advances**: We've already found a suitable `PID`, so this time we enter the starting `Advances` value in the first box, and 0 in the second box.
  - **Pickup Advances**: Enter a value at least 2000 `Advances` above the `Held Advances` target you got in the step before in the first box, and the maximum number of advances you're willing to wait for redeeming the Egg (usually 100000 is more than enough).
  - **Offset (Held / Pickup)**: Leave the value entered for the previous search here unchanged (16 / 3 or 17 / 4 respectively).
  - **Calibration**: Leave the value entered for the previous search here unchanged.
  - **Redraws**: Enter the number of Redraws you got in the `PID` search above here in both boxes.
  - **Method**: Select `Normal` by default. More information on the other options will be provided in the `Troubleshooting` step below.
  - **Compatibility**: Select the Compatibility of your Parents.
- **Settings**: Leave these unchanged from the previous search.
- **Filters**: Reset all the details you entered previously back to `Any` here, and instead specify the IV filters you'd like for your Egg.

Once you've finished setting up all the fields above, click `Generate`. PokéFinder should give you some results almost instantly and find a suitable IV spread for your specifications:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE6.png"</p><br>

After the tool finds the spread you wanted, make note of the `Pickup Advances` value; in our example this is XYZ, which means we will be targeting an `Advances` value of XYZ, when redeeming our Egg.<br>

_Note: If PokéFinder doesn't find any suitable results in one or both of the searches, you'll need to increase the `Held Advances` and `Pickup Advances` search range, respectively, until you obtain a result that satisfies your desired Egg attributes._<br>

## Step 3: RNGing the Egg

Now that you have your target values you can proceed to perform the RNG proper! During the whole process it is advised that you make use of save states as much as possible at every key step, so as to safeguard any mistake or missing target values, and avoid having to restart the game and redo all of it.<br>

Un-pause your emulator and immediately start opening and closing the PokéDex, an amount of times correspondent with the Redraw value you got in your search above, while letting the RNG advance until you're at your target `Held Advances`. You'll notice that the `Calibration` value in the lua script increases by 3 every time you open the PokéDex.<br>
You should pause a few `Timer` Advances before your target and advance the RNG manually to avoid overshooting it. Once at the target, hold the D-Pad arrow of the direction your character is facing, and un-pause your emulator to take a step forward.<br>
If you did it correctly, your Egg `PID` should now be displayed in the script. Below you can see the key moments, at target and immediately afterwards for our example:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE7.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE8.png" width=480 height=320/></p><br>

After the above, you will now let the RNG advance until you are around ~2000 `Advances` before your `Pickup Advances` target, while still inside the Day-Care, which should give you more than enough time to interact with the Day-Care Man.<br>

As you reach 2000 or thereabouts `Advances` before your target, head outside and interact with the Day-Care Man until you're at his last dialogue "Take good care of it.". Just like in the step before, you should pause a few `Advances` before your target and advance the RNG manually to avoid overshooting it. Once at the target, hold the A button, and un-pause your emulator to redeem the Egg.<br>
If you did it correctly, the redeemed Egg's attributes should now be listed in the script. Below you can see the key moments, at target and immediately after Egg redemption for our example:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE9.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE10.png" width=480 height=320/></p><br>

If you followed this guide properly, the Egg you obtained should match exactly what you aimed for in PokéFinder, and now all you have to do is to speed around in your Bike for it to hatch!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3EggE11.png" width=480 height=320/></p><br>

_Note: If either the PID or IVs of the generated Egg, or both, do not match what was expected, please read the `Troubleshooting` step below._

### Troubleshooting

If you followed the guide above properly but an Egg was not generated when taking the final step, or it was generated with the wrong `PID`, it is likely because your `Offset Held` is slightly different than the standard value listed above, which may happen depending on your specific setup.<br>
To calibrate your own `Offset Held` value, simply restore a save state from before you took that last step and try doing so at plus or minus 1 `Advances` from your previously calculated target; if you do get your expected `PID` then, you will have found your actual `Offset Held` value!<br>
While unlikely that you would be off by more or less than 1, repeat this procedure for plus or minus 2, then 3 etc, until you find the correct `Offset Held` value for your setup.<br>

If you followed the guide above properly but still your Egg's IVs were not what you wanted and expected, you likely encountered a different [Egg Method](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#egg-methods) than the one you were targeting (which PokeFinder assumes as the `Normal` one by default).<br>
The first thing you must know, if this happens to you, is that there is no way to change the Method your game is using to generate the Egg's IVs, without changing one or both of the parents; and even if you do so, there's no way to control or predict which Method you'll be getting still!<br>
So what should you do? To figure out what method is actually being used, you should redo the search in PokéFinder by narrowing the search range to include the RNG `Advance` you redeemed the Egg at, while selecting a different Method from the corresponding dropdown one by one, with the IV filters changed to the IV spread you _actually_ obtained, until said IV spread appears as a result on your target `Pickup Advances`. Whatever Method makes that IV spread appear is the Method your game is currently using due to your Egg's parents!<br>
You'll notice that in our example for the guide above, we used the `Split` method for our search - this is precisely because we weren't getting our desired IV spread with the `Normal` method, so after performing the searching above, we determined our Egg was being generated with the `Split` method.<br>

Once you've pinpointed what method your game is using, you must now try and search for your desired spread with it selected. If you don't find any results, you'll have to increase your `Pickup Advances` search range until you do.<br>
You can also alternatively save the game mid-way Step 3 after generating the Egg with your desired `PID`, restart your game, and attempt to find an IV spread starting with a low `Pickup Advances` value; this is possible because the Egg and it's `PID` remain set until you redeem it, even after saving and closing the game.

***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_