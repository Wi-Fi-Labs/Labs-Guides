# Gen 3 RNG Miscellaneous Definitions

In this page you will find various in-depth explanations and definitions about some miscellaneous topics and other resources that are relevant for RNG in the Generation 3 games:

- [VBlank](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#vblank)
- [Methods](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods)


## VBlank

VBlank stands for 'vertical blanking'. It is a feature of the GBA that is responsible for clearing the screen to draw the next frame. While originally unintended and unforeseen by the game developers, this feature can affect the RNG and change the way Pokémon are generated in-game.<br>

VBlank can occur at any moment since it is what ensures the smooth running of the game, visually speaking. It relies on a 'vcount' (which goes up to the hex value of 0x9F) to fire the interrupt that clears the screen. When it occurs, it consumes an RNG call, which if it happens while a Pokémon is being generated, it can make so called 'Method' 2 & 4 (as well as 3 in theory) IV spreads occur - this is what's commonly referred to as ``VBlank interference``.<br>

VBlank happens more frequently in Pokémon Emerald vs RSFRLG, which is why Method W-2 is more common in this game for Wild encounters, whereas the latter games have the standard Method W-1 as their most common (more on that in the section below).<br>

Because ``VBlank interference`` can _interfere_ with our ability to obtain our desired IV spread when RNGing an encounter, how can one then try to minimize or bypass said interference by having the game use the 'correct' [Method](https://github.com/Wi-Fi-Labs/Labs-Guides/blob/main/GEN%203/Guides/Gen3MiscRNG.md#methods)? Several tricks can be attempted, to try and reset the VBlank timing or avoid its interference entirely, such as:

1. Aiming for the next RNg `Advances` where that your target repeats (if applicable)
2. Do some Trainer Card flips as late as possible, before initiating the encounter
3. Trigger the encounter without Sweet Scent (easy to do on FRLG, hard on RSE)
4. Check/uncheck GBA lag reduction on ``VBA`` (having this checked might cause emulation inaccuracy and some consider it a Legality grey area)
5. Try aiming for your target using another Initial Seed
6. Use Pokémon BOX to help RNG that Pokémon (with BOX Adventure Mode)
7. A combo of one or more of the optiins in 1-6.

## Methods

In all five games, there exist multiple sets of PIDs and IVs for a given Egg or encounter on any given frame. Even though the effects of this are mostly innocuous and potentially beneficial to the player, they happen due to a programming oversight.<br>

The GBA's VBlank routine runs roughly once every 16.743 milliseconds. Stat generation is generally much faster than this (roughly 11.749 ms), making four calls to the RNG, each returning half of the PID and IV spread, respectively.<br>
These can be predicted for any given current seed by running the LCG on each result manually, noting the upper 16 bits of each value. However, VBlank is an interrupt and the LCG advances by one sequential state every time it occurs, so to generate the needed four values, an additional RNG call needs to be made.<br>
When one of these extra calls is made, the IVs of the Pokémon will be 'shifted'. These possible (but originally unintended by the developers) combinations are commonly referred to as ``Methods``.

### Encounter Methods

These are the more commonly discussed and encountered Methods during Gen 3 gameplay and RNG. They are named 1 through 5 (or Wild 1 through Wild 5 for Wild encounters), and they occur as follows:

- `Method 1`: No VBlank interference within the encounter generation happens, which means that the entire process could be completed within a VBlank interval.
- `Method 2`: An extra RNG call caused by VBlank interference happens just before the IV generation.
- `Method 4`: An extra RNG call caused by VBlank interference happens in between the first and second half of the IV generation.
- `Method 3`: An extra RNG call caused by VBlank interference happens in between the first and second half of the PID generation, and the newly generated PID matches the predetermined nature (very unlikely to happen).
- `Method 5`: An extra RNG call caused by VBlank interference happens in between the first and second half of the PID generation, and the newly generated PID does **not** match the predetermined nature (a PID reroll occurs and restarts the process).

Of these, 1, 2 and 4 are the ones that have been observed and documented to occur on both actual hardware, and emulators. Method 1 is the 'standard' and originally intended method of stat generation by the developers, where no interference occurs. Methods 2 & 4 however, happen when the IV generation is interfered with.<br>
Methods 3 & 5 on the other hand, _theoretically_ happen when the PID generation is interfered with. While Method 3 has been successfully experienced on actual hardware after extensive testing by RNG researchers, it is so statistically improbable, that no single emulator available today has been able to replicate this behaviour yet. Method 5 is, due to it's nature, theoretical only, and can never actually be attained when generating a Pokémon through normal gameplay.<br>
Below you can find a table exemplifying the sequential RNG calls that happen for each Method that is usually experienced:

| Method  | PID 1 | PID 2 | IV 1 | IV 2 |
| :-----: | :---: | :---: | :--: | :--: |
| 1 / W-1 | 1     | 2     | 3    | 4    |
| 2 / W-2 | 1     | 2     | 4    | 5    |
| 4 / W-4 | 1     | 2     | 3    | 5    |

You can find more in-depth explanations and interesting statics regarding Methods in [this document](https://docs.google.com/spreadsheets/d/1hCZznFa4cez3l2qx1DmYPbuB_dNGTqqCoaksZf-Q44s/edit?usp=sharing).<br>

So what does this mean in practice for our Gen 3 games? Due to slight differences in programming (and in VBlank frequency), some are more common than others in certain games and settings, as listed below:

- For Static & Event Pokémon (equal across all games)
  - M1: Standard Static & Event Pokémon
  - M2: Some Event Pokémon like Wish Egg Events.
  - M4: Static Pokémon when playing through Pokémon BOX Adventure Mode. Alternatively can also happen rarely if playing on ``VBA`` due to poor emulation fidelity.

- For Wild Pokémon (all Wild Pokémon can be found with any Method)
  - W-1: Most common Method in RS & FRLG
  - W-2: Most common Method in Emerald
  - W-4: Uncommon but can happen across all 5 games

### Egg Methods

In regards to Egg generation, because a different process than the one encounters is used, PID and IVs are generated in a very different manner. Here VBlank interference is not so much an issue, but rather the stats and attributes of the parents are what can influence the way an Egg's IVs are generated.<br>
Because of this, Egg Methods have different names:
- Common to all 5 games: `Normal`, `Split` & `Alternate`
- RSFRLG exclusive: `Mixed`

These Methods, and when they occur are influenced by attributes of the parents, such as:
- The PIDs of the parents
- The 'Mother Species'
- Number of level up moves the Egg species learns at level 5

How exactly each Egg Method is influenced by said attributes however, is still not fully well understood. As such no suitable way of controlling or avoiding a given Method for our target has been found yet.<br>
The solution when you encounter a different Egg Method than the one you originally desired or intended then, is to aim for a target with the Egg Method you're currently experiencing.

***
_The contents of this guide were all written by SexyMalasada and partially based on several RNG source websites, forums and discord servers._<br><br>
_[< Back to the Gen 3 Guides page](https://github.com/Wi-Fi-Labs/Labs-Guides/tree/main/GEN%203)_