Commands
========

LootTweaker adds a single command, /ct loottables. 
    
Subcommands
-----------
.. option:: all 

    | Dumps all built-in loot tables.
    | Example:
    | ``/ct loottables all``

.. option:: target

    | Dumps the loot table associated with the object the player is looking at. 
    | Example:
    | ``/ct loottables target``
    
    .. note::
    
        Loot containers lose their loot table data after they are first opened, and some entities don't have a loot table (e.g The Wither).

.. option:: byName <tableID>

    | Dumps the loot table with the specified ID.
    | Example:
    | ``/ct loottables byName minecraft:chests/simple_dungeon``

.. option:: list

    | Lists all built-in loot tables.  
    | Example:
    | ``/ct loottables list``

Dump location
-------------
Dumped loot tables can be found at *minecraftRootFolder*/dumps. The folder structure is the same one used in resourcepacks, so the loot table ``minecraft:chests/simple_dungeon`` would be found at *minecraftRootFolder*/dumps/minecraft/chests/simple_dungeon.json.
