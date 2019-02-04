LootTweaker adds the command `/mt loottables`. This page details how to use that command.

**Format:**  
<>=optional parameter  
[]=required parameter  
`/mt loottables [option] [option parameters]`

**Options:**  
* `all` - dumps all loot tables  
    *Parameters:* None  
    *Example:* `/mt loottables all`
* `target` - dumps the loot table associated with the targeted object. If it's a loot container, note that they lose their loot table data after they are first opened. Some entities don't have a loot table(e.g The Wither).  
    *Parameters:* None  
    *Example:* `/mt loottables target`
* `byName` - dumps the loot table at the specified location  
    *Parameters:* [tableLocation]  
    *Example:* `/mt loottables byName minecraft:chests/simple_dungeon`
* `list` - lists all loot tables.  
    *Parameters:* None  
    *Example:* `/mt loottables list`

**Dump location:**  
Dumped loot tables can be found at *minecraftRootFolder*/dumps. The folder structure is the same one used in resourcepacks, so the loot table `minecraft:chests/simple_dungeon` would be found at *minecraftRootFolder*/dumps/minecraft/chests/simple_dungeon.json.
