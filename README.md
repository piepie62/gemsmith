# Gemsmith

## Description
Gemsmith is a game modification for GCFW.

Same as in the previous game, combining a gem with itself is not always the best way to upgrade it. Thanks to the work done at https://github.com/gemforce-team/gemforce, certain recipes - specific orders of duplicating\combining operations - have been discovered that result in a stronger gem than you'd get by U-upgrading, for the same cost. The catch is that it might take upwards of hundreds of operations to perform some of the better recipes.

Gemsmith allows you to skip performing these operations manually, instead it performs the combine on your gem automatically, spending mana accordingly. Unlike wGemCombiner this is done ingame, completely bypassing UI interactions and using no extra inventory slots. 

This is merely a time saving and QOL mod, exactly the same results can be achieved without it, albeit much slower and with more effort. Mana expenditure stats and achievements should be tracked appropriately, [submit an issue](https://github.com/gemforce-team/gemsmith/issues) if you find that something's off!


## Changelog
https://github.com/gemforce-team/gemsmith/blob/master/Changelog.txt


# Mod files
Gemsmith keeps all its files in the game's Local Store folder. It's located in `%AppData%/Roaming/com.giab.games.gcfw.steam/Local Store/Gemsmith` and it's generated on first launch.

That folder is referred to as **Gemsmith folder** in this readme.


## Features
* A combine can be performed on a gem anywhere: in your inventory, in towers, lanterns, traps, amplifiers and in the enrage slot.

* The recipes are loaded from a `recipes` folder in your Gemsmith folder, you can have as many as you need and switch between them with hotkeys. These recipes are defined in a certain format, devised for [gemforce](https://github.com/gemforce-team/gemforce). An example recipe is generated on startup. Keep in mind that at the moment only "combine" recipes are supported - explanation below.

* Gemsmith also includes a configuration file that allows you to rebind hotkeys. This includes both Gemsmith's own functions and base game's hotkeys.

* Press Alt + "Perform combine" hotkey to **reload your config and recipes**.

* Gemsmith keeps a log of the last session in your Gemsmith folder. If you see a floating message saying that an error has occured, there might be more information in there.

* **Gemsmith automatically checks if an update is available by comparing the latest release tag with its own version.** You can opt-out by changing the appropriate setting in the configuration.


## Installing the mod
The modification consists of two parts: a patch applied to the game and the mod's .swf that the patched game loads. The patch is a diff created with Courgette.

**To install the mod** grab a release (links below) for your game version. Copy `applyDiff.bat`, `courgette64.exe`, `Gemsmith-x.x-for-y.y.y.diff` and `Gemsmith.swf` from the archive into the game's folder (To navigate to the game's folder: rightclick the game in steam -> Manage -> Browse local files).

After that launch `applyDiff.bat`, your game will be patched and all unnecessary files deleted. Then launch the game normally through steam.

[More about Courgette](https://blog.chromium.org/2009/07/smaller-is-faster-and-safer-too.html)

[Courgette repo](https://chromium.googlesource.com/chromium/src/courgette/+/master)


# Uninstalling the mod
There are two ways to restore your original .swf
1) Delete "GemCraft Frostborn Wrath.swf" and rename "GemCraft Frostborn Wrath Backup.swf" to "GemCraft Frostborn Wrath.swf"
2) Run steam's "Verify integrity of game files" and it'll be redownloaded.


## Releases
[Link to the latest release](https://github.com/gemforce-team/gemsmith/releases/latest)

Release history: [Releases](https://github.com/gemforce-team/gemsmith/releases)


# Detailed features
## Recipes
Gemsmith supports two formats of recipes: short and full. An example of short format recipes is generated on first launch in the `recipes` folder in your Gemsmith folder. Example below:
```
o
0+0
1+0
2+0
3+0
4+0
5+1
```
Long format recipes are generated by [gemforce](https://github.com/gemforce-team/gemforce). Example below:
```
(val = 1)	 0 = g1 o
(val = 2)	 1 =  0 +  0
(val = 3)	 2 =  1 +  0
(val = 4)	 3 =  2 +  0
(val = 5)	 4 =  3 +  0
(val = 6)	 5 =  4 +  0
(val = 8)	 6 =  5 +  1
```
Recipes for GCFW are a WIP, https://github.com/gemforce-team/gemforce/tree/master/results/leech-combine contains recipes for pure orange gems (the mechanics are the same for those between GCCS and GCFW). Look around the repo for more recipes, but remember that **only combine recipes are supported.** Combine recipes have only one line containing a letter in the beginning of the recipe. If there are more than one lines with letters, like
```
(val = 1)	 0 = g1 b
(val = 1)	 1 = g1 r
(val = 1)	 2 = g1 y
(val = 2)	 3 =  2 +  1
(val = 3)	 4 =  3 +  0
(val = 4)	 5 =  4 +  0
(val = 2)	 6 =  0 +  0
(val = 3)	 7 =  6 +  0
(val = 4)	 8 =  7 +  0
(val = 8)	 9 =  8 +  5
```
, that is not a combine recipe.
You need to copy the equations under "Equations:" from a file in that repo, then paste them into a **separate** `.txt` file in your recipes folder. Name it however you want, that name will be shown ingame.

Alternatively, you can write your own recipes. Keep in mind that Gemsmith expects that the result will be a single gem obtained on the last step.


## Hotkeys
By default Gemsmith's hotkeys are:
```
PageUp - previous recipe
PageDown - next recipe
Home - perform combine
```
Those can be changed in Gemsmith_config.json located in your Gemsmith folder. Buttons are represented by KeyCodes, a reference is included in each release's archive: `Hotkey KeyCodes reference.txt`

After saving your changes, press Alt + `perform combine` ingame to reload your recipes and config.


# Bug reports and feedback
Please submit an issue to [The issue tracker](https://github.com/gemforce-team/gemsmith/issues) if you encounter a bug and there isn't already an open issue about it.

You can find me on GemCraft's Discord server: https://discord.gg/ftyaJhx - Hellrage#5076


# Disclaimer
This is not an official modification.

GemCraft - Frostborn Wrath is developed and owned by [gameinabottle](http://gameinabottle.com/)


# Credits
Gemsmith is developed by Hellrage

**Special thanks to**

12345ieee for helping with testing, ideas, advice on using gemforce and combine logic

piotrj3 for help with decompilation and testing

wGemCombiner team for creating the predecessor

gemforce team for working out the combine recipes
