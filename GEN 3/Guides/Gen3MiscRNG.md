# Gen 3 RNG Miscellaneous Definitions

In this page you will find various in-depth explanations and definitions about some miscellaneous topics and other resources that are relevant for RNG in the Generation 3 games:

- [VBlank](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#vblank)
- [Methods](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods)


## VBlank

VBlank stands for 'vertical blanking'. It is a feature of the GBA that is responsible for clearing the screen to draw the next frame. It relies on a 'vcount' (which goes up to the hex value of 0x9F) to fire the interrupt that clears the screen.<br>

VBlank can occur at any moment since it is what ensures the smooth running of the game, visually speaking. When VBlank occurs it consumes an RNG call. If this happens while a Pokémon is being generated, it can make so called 'Method' 2 & 4 (as well as 3 in theory) IV spreads occur - this is what's commonly referred to as ``VBlank interference``.<br>

VBlank happens more frequently in Pokémon Emerald vs RSFRLG, which is why Method W-2 is more common in this game for Wild encounters, whereas the latter games have the standard Method W-1 as their most common (more on that below).<br>

Because ``VBlank interference`` can _interfere_ with our ability to to obtain our desired IV spread when RNGing an encounter or Egg, how can one then try to minimize or bypass said interference by having the game use the 'correct' [Method](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods)? Several tricks can be attempted, to try and reset the VBlank timing such as:

1. Try the next frame where that encounter slot repeats
2. Do some Trainer card flips before initiating the encounter
3. Trigger the encounter without Sweet Scent
4. Check/uncheck GBA lag reduction on VBA
5. Try another initial seed
6. Use Pokémon BOX to help RNG that mon (BOX Adventure mode)
7. A combo of 1-6.

## Methods

In all five games, there exist multiple sets of PIDs and IVs for a given Egg or encounter on any given frame. Even though the effects of this are mostly innocuous and potentially beneficial to the player, they happen due to a programming oversight.<br>

The GBA's VBlank routine runs roughly once every 16.743 milliseconds. Stat generation is generally much faster than this (roughly 11.749 ms), making four calls to the RNG, each returning half of the PID and IV spread, respectively.<br>
These can be predicted for any given current seed by running the LCG on each result manually, noting the upper 16 bits of each value. However, VBlank is an interrupt and the LCG advances by one sequential state every time it occurs, so to generate the needed four values, an additional RNG call needs to be made.<br>
When one of these extra calls is made, the IVs of the Pokémon will be 'shifted'. These possible (but originally unintended) combinations are commonly referred to as ``Methods``, which are named 1 through 4 (or Wild 1 through Wild 4 for Wild encounters).<br>
All of these have been observed and documented at least _once_ on actual official hardware, although Method 3 is, due to it's nature, extremely rare and improbable, to the point where no single emulator available today has been able to replicate this behaviour yet (which itself has only been properly verified and confirmed in official hardware once).<br> 
Below you can find a table exemplifying the sequential RNG calls that happen for each Method:

| Method  | PID 1 | PID 2 | IV 1 | IV 2 |
| :-----: | :---: | :---: | :--: | :--: |
| 1 / W-1 | 1     | 2     | 3    | 4    |
| 2 / W-2 | 1     | 2     | 4    | 5    |
| 4 / W-4 | 1     | 2     | 3    | 5    |

So what does this mean in practice for our Gen 3 games? Due to slight differences in programming (and in VBlank frequency), some are more common than others in certain games and settings, as listed below:

- For Static & Event Pokémon (equal across all games)
  - M1: Standard Static & Event Pokémon
  - M2: Some Event Pokémon like Wish Egg Events.
  - M4: Static Pokémon when playing through Pokémon Box Adventure Mode. Alternatively can also happen rarely if playing on ``VBA`` due to poor emulation fidelity.

- For Wild Pokémon (all Wild Pokémon can be found with any Method)
  - W-1: Most common Method in RS & FRLG
  - W-2: Most common Method in Emerald
  - W-4: Uncommon but can happen across all 5 games



***
_The contents of this guide were all written by SexyMalasada and partially based on several RNG source websites, forums and discord servers._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_