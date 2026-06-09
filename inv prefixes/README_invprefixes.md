The series of bytes within a prefix should be pasted into the front of the file. You can probably use a text editor like Notepad for this, but a hex editor will give you more precision for making adjustments and catching mistakes.

These prefixes are modular: if you would like to apply more than one, simply paste both. You can stack as many or as few as you'd like.

inv_prefix_vanilla: Contains every card marked with a letter in the "RCU" column of this page: https://plantsvszombies.wiki.gg/wiki/User_blog:Unbroken10990/PvZH:_Full_Card_Index.
inv_prefix_700-799: Contains every GUID from 700-799.
inv_prefix_800-899: Contains every GUID from 800-899.
inv_prefix_900-999: Contains every GUID from 900-999.

If a GUID is included that isn't present in your cards.json, the game will fail to launch. Each entry is 7 bytes and can be removed in a hex editor if necessary. For example, if your cards.json only contains GUIDs 800-997, paste in the 800-899 file as-is, and remove the last 14 bytes from the 900-999 file to remove the last two entries.
Entries for GUIDs of 0-127 are only 6 bytes.

If you need to reset the file to an unmodded state and remove these prefixed bytes, simply connect to the internet and relaunch the game. This should purge any illegal entries. Useful for resetting delta file.
