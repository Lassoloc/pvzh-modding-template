# PvZH Modding Template

-WORK IN PROGRESS-

## /bundles/card_data

Contains a formatted (and otherwise unmodified) version of the vanilla `cards.json` file, as well as a subfolder containing every card in its own `.json` file.

Thank you to [bbb908](https://github.com/bbb908) for making the card splitter tool used to split and reassemble these, at my request. (A link will be added here if it is publicly released)

## /bundles/data_assets

work in progress

planned to include omniclass hero files

## /bundles/loc

work in progress

## /inv prefixes 

**-WARNING: UNSAFE AND CURRENTLY DOES NOT WORK, BRICKS YOUR INVENTORY INSTEAD. NEEDS MORE TESTING-**

**This has been tested with one or two cards at a time to successful results, but using the entire thing causes your inventory to be completely wiped. Currently doing more testing to fix this**

This folder contains binary files which can be inserted into the start of the `PlayerInventory` and `PlayerInventoryDelta` files to add unobtainable or new modded cards to your inventory.

Back up both inventory files before attempting.

<details>

<summary>Instructions for use</summary>

The series of bytes within a prefix should be pasted into the front of both `PlayerInventory` and `PlayerInventoryDelta`. You can probably use a text editor like Notepad for this, but a hex editor will give you more precision for making adjustments and catching mistakes. For optimal conditions the Delta file should be in its base state (14 bytes: precisely `20 00 28 00 30 00 38 00 40 00 50 00 60 00`), but it should theoretically work with any Inventory and Delta as long as it doesn't already have any overlap with the prefix you're adding.<br/>
<br/>
These prefixes are modular and stackable: if you would like to apply more than one, simply paste both.<br/>
 - `inv_prefix_vanilla` (581 bytes): Contains every card marked with a S, T, or C in the "RCU" column of [this page](https://plantsvszombies.wiki.gg/wiki/User_blog:Unbroken10990/PvZH:_Full_Card_Index).<br/>
 -- *This includes every unobtainable card except for BoardAbilities and GrantedTriggeredAbilities.*
 - `inv_prefix_vanilla_factionless`: Contains every card marked with a B or G in the "RCU" column of the aforementioned page.<br/>
 -- *This includes every BoardAbility and every GrantedTriggeredAbility.*
 - `inv_prefix_700-799`: Contains every GUID from 700-799.<br/>
 - `inv_prefix_800-899`: Contains every GUID from 800-899.<br/>
 - `inv_prefix_900-999`: Contains every GUID from 900-999.<br/>
<br/>
If a GUID is included that isn't present in your `cards.json`, the game will fail to launch. Each entry is 7 bytes and can be removed in a hex editor if necessary. For example, if your `cards.json` only contains GUIDs 800-997, paste in the 800-899 file as-is, and remove the last 14 bytes from the 900-999 file to remove the last two entries.<br/>
Entries for GUIDs of 0-127 are only 6 bytes.<br/>
<br/>
If you need to reset the file to an unmodded state and remove these prefixed bytes, simply connect to the internet and relaunch the game. This should purge any illegal entries, as well as reset the `PlayerInventoryDelta` to its base state.<br/>
<br/>
The associated `.hexbm` files are bookmark files for ImHex, which can be imported to see labeled annotations for the files. (unfinished)
</details>

These files were all built by hand in a hex editor. Thank you to h3x4n1um and the other contributors for their documentation of the `PlayerInventory` byte structure, as provided in [h3x4n1um/PI-Cards-Helper](https://github.com/h3x4n1um/PI-Cards-Helper/blob/master/README.md).

Thank you to [bbb908](https://github.com/bbb908) for making the [RTON binary converter tool](https://bbb908.github.io/RTON-Decimal-To-Num/) used to create these, also at my request.