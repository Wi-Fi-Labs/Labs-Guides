# Gen 3 Initial Seed RNG

This guide is meant to explain & teach you how to RNG Initial Seeds in the Gen 3 games, which is something essential and usually the first practical step of any RNG you'll likely want to do.<br>
The process is presented here as done on, and with examples in `BizHawk` (which runs an mGBA core); but it can be followed in `mGBA` and `VBA` just as well, with specifics to the latter noted where relevant.

## Getting Started

Required tools:
- [Gen 3 RNG Lua Scripts](https://github.com/Wi-Fi-Labs/PokeRNG-LuaScripts/tree/main)
- [Lego's 'Painting-Seed' Tool](https://legofigure11.github.io/tools/painting-seed/)
- [BizHawk 2.8-rc1](https://github.com/TASEmulators/BizHawk/releases/tag/2.8-rc1); [VBA rr 23.6](https://github.com/TASEmulators/vba-rerecording/releases) or [mGBA](https://mgba.io/downloads.html) emulator
- [RunAsDate](https://www.nirsoft.net/utils/run_as_date.html) (if using VBA)
- A copy of any of the Gen 3 games

## Preparation & Basic Info

When you load a game, a combination of values are used to determine the `Initial Seed`. This value serves as the starting point from which the game's algorithm generates subsequent hexadecimal values, which in turn determine the features of any encountered Pokémon (or any game event really).<br>

[PokéFinder](https://github.com/Admiral-Fish/PokeFinder) (PF) is an RNG tool that allows you to calculate, search for and predict results of these values for a given RNG `Advance` (also previously and still commonly named 'frame'), which combined with certain actions performed in-game, at the right moment, allow you to obtain perfect IV & Shiny Pokémon.<br>
When reading up on other RNG guides such as [Gen 3 TID/SID](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md), [Gen 3 Wild / Static / Gift](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3WildStaticGiftRNG.md) or [Gen 3 Roamer](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3RoamerRNG.md), you'll learn how to use PF to first find a desired target and Initial Seed.<br>

In the Generation 3 games, there are several methods by which Initial seeds can be RNGd: 
- [Live Battery RS](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#live-battery-rs)
- [Dead Battery RS](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#dead-battery-rs)
- [Emerald Painting & FRLG Initial Seed Bot](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#emerald-painting--frlg-initial-seed-bot)
- [Emerald Battle Video](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#emerald-battle-video)
- [FRLG/E TID Re-seed](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3InitialSeedRNG.md#frlge-tid-re-seed)

Below you will find a section for each of these methods, fully explaining how to RNG Initial Seeds with each of them.

# Live Battery RS

This method is applicable to and usable in __Ruby & Sapphire only__, consisting of loading the game at a specific Date & Time, and is a method that provides you a lot more options for RNG in these games. On an actual cartridge it is the method used when the battery in it is still running and keeping the in-game time - which in an emulator means using the RTC functions of BizHawk, or use RunAsDate with VBA.<br>

For this example we will be using a target Initial Seed of `92B8`, which can be obtained by setting the date & time as `31/12/2023 00:00:00`.<br>
Below you can learn how to configure both emulators to use this method.<br>

### BizHawk

Open BizHawk, load your game, and go to `GBA>Settings>Sync Settings`.<br>
In this tab you can see several configurable RTC options; you'll want to set these as follows:
- RTC Use Real Time: `False`
- RTC initial Time: The target seed's Date & Time in the format `DD/MM/YYYY HH:MM:SS`
- RTC: `True`<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedLBBH1.png"/></p><br><br>

After configuring the above, load the `RS_RNG_BizHawk_SM` script, reboot core, and BizHawk will launch the game with your specified Date & Time, giving you your desired Initial Seed!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedLBBH2.png" width=480 height=320/></p>

### VBA

Open VBA, navigate to `Options>Emulation>Real Time Clock` and :white_check_mark: it:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedLBVBA1.png"/></p><br><br>

After doing the above, open RunAsDate and configure it as follows:
- Select the path of your target application (in this case where your `VBA.exe` is located)
- Date/Time: `Absolute date/time`
  - The target seed's Date & Time in the format `DD/MM/YYYY HH:MM:SS`
- :white_check_mark: `Immediate Mode`<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedLBVBA2.png"/></p><br><br>

After configuring the above press `Run`, and VBA will launch with your specified Date & Time, keeping it static. All you need to do afterwards is launch your game, load the `RS_RNG_2.0` VBA script, and you'll get your desired Initial Seed!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedLBVBA3.png" width=480 height=320/></p><br><br>

_Note: Depending on the architecture of the app you're using (32bit or 64bit), you need to download and use the corresponding RunAsDate version to launch it! The recommended VBA version in this guide is 32bit.<br>
Depending on how your computer's permissions are set, you may also need to use the `Run As Administrator` option in RunAsDate._

# Dead Battery RS

This method is applicable to and usable in __Ruby & Sapphire only__. On an actual cartridge it is the method used when the battery has run dry and is no longer keeping the in-game time - which in an emulator means _not_ using the RTC functions of BizHawk, or have _Real-Time Clock_ un-checked in VBA.<br>
With a dead battery, these games always load with an Initial Seed of `05A0`, which in practice means _a lot_ less desirable options, so this method is usually only used for TID/SID RNG and **strongly** advised against for anything else!

Below you can learn how to configure both emulators to use this method.<br>

### BizHawk

Open BizHawk, load your game, and go to `GBA>Settings>Sync Settings`.<br>
In this tab you can see several configurable RTC options; for this method you only need to set one of them, as follows:
- RTC: `False`<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedDBBH1.png"/></p><br><br>

After configuring the above, load the `RS_RNG_BizHawk_SM` script, reboot core, and BizHawk will launch the game disregarding any Date & Time settings, giving you the expected Initial Seed of `05A0`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedDBBH2.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedDBBH3.png" width=480 height=320/></p>

### VBA

Open VBA, navigate to `Options>Emulation>Real Time Clock` and un-check it:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedDBVBA1.png"/></p><br><br>

After configuring the above, launch your game, load the `RS_RNG_2.0` VBA script, and you'll get the expected Initial Seed of `05A0`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedDBVBA2.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedDBVBA3.png" width=480 height=320/></p>

# Emerald Painting & FRLG Initial Seed Bot

These two methods for these games are grouped together because the first part of the process is common to both.
For this section we will be using an example target seed of `7EC88A66`. You'll notice that unlike in `Live Battery RS`, this seed is 32-bit or 8 digits - that is because it is the seed of our target spread, as in the actual RNG advance/state at which our desired target Pokémon appears.<br>

To obtain a desired Initial Seed from this target seed, we now have to plug it in `Lego's Painting-Seed Tool`. This is a simple tool that calculates a given number of Initial Seeds that contain your target seed within a certain number of RNG advances, starting with the one that requires fewer advances and listing them in increasing order.<br>
Open the tool, paste your target seed, type in a number of max results (we specified 10 results) and hit 'Calculate'. You now have various Initial Seeds that will give you your target after the specified number of advances to pick from!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedPainting.png"/></p><br>

_**Important Note EMERALD**: Since the Painting Re-seed RNG process in Emerald always starts in Lilycove City, it is advisable to pick an Initial Seed where the target is far enough, advances-wise, that it allows you time to reach the target's location._<br>

_**Important Note FRLG**: Due to the nature of how the RNG process works in FRLG, it's advisable to have a large pool of Initial Seeds to pick from (15+), even if it means placing our target in the region of millions or billions of advances away. Further explanation will be provided in the FRLG Initial Seeds Bot section._<br>

Now that we have our desired Initial Seed(s), let's proceed to the section below relevant to the game you're RNGing on!

## Emerald Painting Re-seed

This method, commonly referred to as "Painting Re-seed" or "Painting method", is the method used in __Emerald__. Because this game has a programming error that makes the Initial Seed always be `0000` on game start-up, regardless of the cartridge's battery status, this method allows you to bypass this issue by taking advantage of an exploit, where the game's RNG state has it's Initial Seed replaced by an hexadecimal value that's close to the elapsed (decimal) RNG advances at that point.<br>
In practical terms, this means that if we trigger the exploit after say, 4000 advances have passed since the game was loaded for example, we would get an Initial seed of `0FA0` or thereabouts.<br>
The way in which this exploit, or re-seeding, is done is by observing one of the paintings in Lilycove's Contest Hall, or in Lilycove Museum's 2F - the moment the A button is pressed to observe a painting, the Initial Seed gets re-seeded!<br>
From the example in the previous section, we selected the Initial Seed `0C98` as the suitable one to obtain our target, so let's get to it.<br>

Load up Emerald in your emulator. If you're not already saved in front of one, quickly travel to, and position yourself in front of one of the paintings on either of the two locations mentioned above.<br>
Once you've saved there, reboot your game and load up the `E_RNG_BizHawk_SM` or `E_RNG_2.0_Painting` script. This script is very similar to the RS one, with just some extra or different features for Emerald specifically. An important value for this process will be the `Painting Timer`, which is a line that displays the Initial Seed that would be re-seeded in the game at a given RNG Advance.<br>
After you're back in the overworld facing the painting, let the RNG advance until the `Painting Timer` shows a seed that is close to your desired Initial Seed (-100 advances or thereabouts should suffice). At this point, pause the emulator and make a Save State.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedE1.png" width=480 height=320/></p><br><br>

Although one would expect to press A on the painting as the `Painting Timer` displays our target Initial Seed, there is a delay between the moment you press A to view the painting, and the moment the actual re-seeding occurs. This delay is somewhere around 29-30 advances (or 1D-1E in hexadecimal), but you should do some practice runs in order to calibrate this delay for your setup by doing the following:
- Hold A and un-pause on a given RNG Advance, taking note of the seed the `Painting timer` displays as expected.
- Once you're looking at the painting take note of the _actual_ obtained Initial Seed.
- Subtract the expected seed from the actual one obtained with an [hexadecimal calculator](https://www.calculator.net/hex-calculator.html) and take note of the difference - this is your delay in hexadecimal value.
- Restore your previous Save State and repeat until you're confident you have properly calibrated your delay.<br>

After you've done the above, subtract your delay from your desired Initial Seed - this will give you the seed you must aim for when displayed in the `Painting Timer` (in my case `0C98` - `1D` = `0C7B`).<br>
Manually advance the RNG until you see the previously calculated seed displayed in the `Painting Timer`. Once you reach it, Hold A and un-pause the emulator to trigger the viewing of the painting. If you did everything correctly, you should now have your desired Initial Seed!<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedE2.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedE3.png" width=480 height=320/></p><br>

_Note: This method can also be used in Ruby & Sapphire, but the methods available for those games specifically are much better and simpler to do._

## FRLG Initial Seed Bot

This method is used in __FireRed & LeafGreen__ exclusively. Because these two games lack a battery to begin with, the Initial Seed is instead generated upon pressing A or Start at the Title screen. The way it's generated is based on a parameter that changes very quickly, making it very hard to RNG and instead simpler and easier to just Soft-Reset over and over until you get a desired result with a Bot. Such a Bot is provided as one of the features of the `FRLG_RNG_BizHawk_SM` or `FRLG_RNG_2.0` lua script, which performs a series of rapid Save State and Save Restores to accomplish this.<br>
From the example in the main section above, we will be using the bot to search for _any_ of the ten Initial Seeds we obtained with `Lego's Painting-Seed Tool`. To do this, you first must specify these as your targets for the Initial Seed Bot in the lua script. This is done by opening the `FRLG_RNG_BizHawk_SM` or `FRLG_RNG_2.0` script in a text editor like Notepad, navigating to the following line, and pasting the target Initial Seeds between the brackets, as shown below (don't forget to save the file when done):<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedFRLG1.png"/></p><br>

Once you've done the above, we can now proceed to the actual 'Botting' to find one of the given Initial Seeds.<br>
Open your emulator, load your game and the `FRLG_RNG_BizHawk_SM` or `FRLG_RNG_2.0` script. The way the bot is activated differs slightly between `BizHawk` and `VBA`; you can find the instructions for each within the script itself, as shown below (BizHawk = left / VBA = right):<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedFRLGBH.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedFRLGVBA.png" width=480 height=320/></p><br>

After you un-pause at the end of the instructions above, the Bot should start resetting the Title screen over and over, flashing the screen in the process. It's advisable to _turbo_ your emulator, so as to speed up the process as much as you can, and reduce the overall time spent waiting for the Bot to find a seed.<br>
As previously mentioned in the main section, it is advisable to have a large pool of seeds for the Bot to search, as this also greatly helps reducing the time it spends resetting to find one.<br>

Once the bot finds a result, it pauses the emulator immediately. As soon as you un-pause, you'll see the script display a `Found!` message as shown below, listing what Initial Seed from your list it found. In my example here it found `F95C`, which was the 2nd seed on my list.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedFRLG2.png" width=480 height=320/></p>

# Emerald Battle Video & FRLG/E TID Re-seed

Both of the methods described below are nowadays **considered obsolete**, way less efficient, or only really relevant for niche cases.<br>
Whenever suitable, the Painting Re-seed & Initial Seed Bot methods described above are **_always_** recommended for Emerald & FRLG Initial Seed RNG, respectively, over the methods described below.

## Emerald Battle Video

This method is less efficient than the Painting Re-seed one, but it was the most commonly used and best method available back in the day, before the Painting method was discovered. The latter is **strongly** advised over this method, as it is much simpler to perform and way more versatile.<br>
When you watch a recorded battle in your Frontier Pass, the Battle Video's RNG state (32-bit `Current Seed`) get's re-seeded as your Initial State from that point on. This means that you can 'store' a given Current Seed for constant re-use, by saving a battle where the RNG state was a given value when it started.<br>
You can also do this by connecting with a second game to battle via link cable or wireless adapter, as the Current Seed in the game of `Player 1` will be saved as the recorded battle's `Battle Video Seed`. Below you can see an example of an Emerald save having it's Initial Seed re-seeded to the one that was saved with a Battle Video facing Palace Maven Spenser:<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedBV1.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedBV2.png" width=480 height=320/></p><br>

_Note: You can combine this method with the `FRLG/E TID Re-seed` one described below, in order to store a desirable and specific Current Seed in your Battle Frontier Pass; by recording a link battle with a save that has performed a TID re-seeding, playing as `Player 1`._

## FRLG/E TID Re-seed

This method is the least versatile and less useful of all the methods available to FRLG & Emerald. Because FRLG lack a battery, and Emerald has the Initial Seed `0000` programming error, this is a method that allows you to Re-seed your Initial Seed as you start a New Game.<br>
The way this works is that once you press `END` on your character's name selection, your Initial Seed becomes the same as your TID value, in hexadecimal. This can then be combined with [Gen 3 TID/SID RNG](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3TIDSIDRNG.md) methods to obtain a desirable Initial Seed that will give you good target IV spreads.<br>
Unfortunately this method doesn't have any practical applications in FRLG, and only serves a purpose for some niche cases in Emerald, such as for obtaining the Starters with good IV spreads; as once you reload your game (which will eventually happen if you get as far as beating the Pokémon League) your seed will be reset. In the example below you can see the end result, where `0xFB09 = 64265`.<br>

<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedTID1.png" width=480 height=320/> <img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/GEN%203/Images/G3InitialSeedTID2.png" width=480 height=320/></p>

***
_The contents of this guide were all written by SexyMalasada and partially based on guides written by [DevonStudios](https://devonstudios.it/)._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_