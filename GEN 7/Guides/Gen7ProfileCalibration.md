# Gen 7 Profile Calibration in 3DSTimeFinder

For the purpose of Initial Seed RNG manipulation in the Generation 7 games, a `Profile` for each of your save files must be created and calibrated properly, to ensure you get accurate & usable results.

The values required for a save `Profile` are:
- Game Version
- TID (the 5 digit one, not the G7TID that is displayed in-game)
- SID (the 5 digit one, not the 4 digit one that is counterpart to the G7TID)
- Shiny Charm: Yes or No
- Tick
- Offset

If you're using the latest or a post v0.5.0 version of [PokeReader](https://github.com/zaksabeast/PokeReader), then Tick & Offset Values can be obtained directly from the `Citra` tab on the plugin.<br>
This way you can easily manually fill in all the information for a `Profile`.<br><br>

If however you're using an older PokeReader version or [CitraRNG](https://github.com/Admiral-Fish/CitraRNG), you'll need to search for your save file's Tick & Offset values (what we call 'calibrating your profile').<br>
To calibrate your `Profile`, open the `Gen 7 calibrator` under Tools in [3DSTimeFinder](https://github.com/Admiral-Fish/3DSTimeFinder), and use the following Base Tick & Offset Values:

```
CitraRNG
SM: 36ec43b / 55
USUM: 43b1cf3 / 56

PokeReader
SM: 14a7a512 / 1133
USUM: 1573b78e / 1134

Search Ranges (increase these if you don't find results initially):
- 5 million Tick Range
- 50 Tick Offset
```


***
_The contents of this guide were all written by SexyMalasada._<br><br>
_[< Back to the Gen 7 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%207)_