# Managing PokeFinder Profiles

While the latest [PokeFinder](https://github.com/Admiral-Fish/PokeFinder) release has almost everything you would require for RNGing on Gens 3 to 5 and BDSP, there are still some functions that are yet to be implemented, or that the developer has expressed no intent in including themselves.<br>
Some of these functions can be found in older official builds or forks by other developers, some of which are based on a version of PF that is still `3.x.x` and not the latest `4.x.x`.<br>
This means that you may find yourself in need of running several different PF versions or forks, but unfortunately PF v4 `profile.json` files are ***not*** backwards compatible with PF v3 versions. This means you will have to create separate `profile.json` files for separate versions and change between them.<br>
We'll show you how to manage this in the quick guide below!

## Creating a new profile.json file

For the purpose of this guide let's say you have the need to run Lincoln-LM's [Finder-Toolbox](https://github.com/Lincoln-LM/Finder-ToolBox) for a given RNG, which has some extra features and is a PF `3.x.x` fork from a few years ago.<br>
Start by opening FinderToolbox (or whatever other PF v3 build/fork you have). Navigate to `Tools>Settings>Profiles Path` and click `change`; you can now create a new `profiles.json` file that you can name whatever you wish (example: `profiles_toolbox.json`).<br>
You can reference the image below for better visualization.<br><br>
<p align="center"><img src="https://raw.githubusercontent.com/Wi-Fi-Labs/Labs-Guides/main/MISC/Images/PokeFinderProfiles1.png"/></p>
After you've done the above, you can now add specific profiles for your PF v3 build/fork!<br>

## Changing between profile.json files
To restore your PF v4 `profiles.json` file to use with a PF v4 build again, simply open up PokeFinder (the newer version) and navigate to `Tools>Settings>Profiles Path`, click `change`, and simply select your v4 `profiles.json` file.<br>
To change back to a PF v3 `profiles.json` file for use with an older build, simply repeat this last process, **but** do so in the older build's settings!

***
_The contents of this guide were all written by SexyMalasada._<br><br>
_[< Back to the Miscellaneous Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/MISC)_