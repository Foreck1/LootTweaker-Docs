Removing Loot
=============

In this tutorial you will learn how to remove loot from a loot table. I will be removing
porkchops from the pig loot table as an example. To do this we need to know 3 things,
the name of the pig's loot table, the name of the pool with the porkchop entry, and
the name of the porkchop entry. To obtain that information follow these steps:

First launch Minecraft. Then open the instance folder for the instance of Minecraft you
launched. If you don't know where this is, a simple way to find it is
Options->Resource Packs->Open Resource Pack Folder, this opens the resourcepacks folder,
which is inside the instance folder.

Finding the table name
----------------------
a) If the table is for an entity, spawn the entity ingame. Now look at the entity and
   run the command ``/ct loottables target``. Not all entities have loot tables. The Wither
   is a vanilla example (`More Loot Tables <https://minecraft.curseforge.com/projects/more-loot-tables>`_ adds one).
   If a modded entity does not have a loot table, you will have to ask the author to add one.
   Until they do you can use `CraftTweaker's Drop Functions <https://crafttweaker.readthedocs.io/en/latest/#Vanilla/Entities/IEntityDefinition/#drops>`_.
b) If it's for a loot chest, find a loot container that you think has the right loot table
   and **do not** open it. Now look at the chest and run the command ``/ct loottables target``.
c) If it's neither of the above, check the the mod's documentation, or for vanilla,
   `this list <https://minecraft.gamepedia.com/Loot_table#List_of_loot_tables>`_.

If you found the name using c), run the command ``/ct loottables byName <loot table name>`` before continuing.

Finding the entry name
----------------------
Go to the instance folder and open the subfolder called dumps. You'll find the loot table
in here as json with the path ``dumps/loot_tables/<domain>/<path>.json``, so a loot table
named ``awesomemod:chests/awesomechest`` would have the path ``dumps/loot_tables/awesomemod/chests/awesomechest.json``.
In the case of the pig loot table, it is called ``minecraft:entities/pig``.
Now open the loot table dump file, in the case of the pig, the JSON looks like this::

    {
      "pools":
      [
        {
          "name": "main",
          "entries":
          [
            {
              "entryName": "minecraft:porkchop",
              "weight": 1,
              "quality": 0,
              "type": "item",
              "functions": [
                {
                  "count": {
                    "min": 1.0,
                    "max": 3.0
                  },
                  "function": "minecraft:set_count"
                },
                {
                  "function": "minecraft:furnace_smelt",
                  "conditions": [
                    {
                      "properties": {
                        "minecraft:on_fire": true
                      },
                      "entity": "this",
                      "condition": "minecraft:entity_properties"
                    }
                  ]
                },
                {
                  "count": {
                    "min": 0.0,
                    "max": 1.0
                  },
                  "function": "minecraft:looting_enchant"
                }
              ],
              "name": "minecraft:porkchop"
            }
          ],
          "rolls": 1.0
        }
      ]
    }

First, find the entry. We're looking for the entry with a ``name`` tag that is the same as
the registry name of porkchops, which is ``minecraft:porkchop``. The item you're looking
for may have NBT and/or metadata, in that case you'll need to check the ``functions`` tag,
and look at the ``set_nbt`` and ``set_data`` functions, respectively.

Next look for the ``entryName`` tag for the entry you just found.
It will often have the same value as the ``name`` tag, but not always.
Remember or note down the value of ``entryName``.
In this case the value is ``minecraft:porkchop``.

Find the pool the entry is in and remember or note down the value of ``name``.
In this case it's in the pool called ``main``.

Creating the script
-------------------
Finally, in your script import ``loottweaker.vanilla.loot.LootTables``,
``loottweaker.vanilla.loot.LootTable`` & ``loottweaker.vanilla.loot.LootPool``.
Then combine ``LootTables.getTable()``, ``LootTable#getPool()`` & ``LootPool#removeEntry()``
with the table, pool and entry names you found earlier.
The resulting script for removing porkchops from the pig loot table looks like this::

    //Import necessary types
    import loottweaker.vanilla.loot.LootTables;
    import loottweaker.vanilla.loot.LootTable;
    import loottweaker.vanilla.loot.LootPool;

    //Get the loot table named "minecraft:entities/pig" and store it for later use
    val pig = LootTables.getTable("minecraft:entities/pig");
    //Get the pool named "main" from the loot table and store it for later use
    val pigMain = pig.getPool("main");
    //Remove the entry named "minecraft:porkchop" from the loot pool
    pigMain.removeEntry("minecraft:porkchop");

The key thing here is not the arrangement of the methods, but the methods used,
the parameters passed to them and the objects they are called on.
The below script does exactly the same thing as the above script and is also valid.
I recommend the above style when modifying a table or pool more than once, as it is more
concise and readable.

::

    import loottweaker.vanilla.loot.LootTables;
    import loottweaker.vanilla.loot.LootTable;
    import loottweaker.vanilla.loot.LootPool;

    LootTables.getTable("minecraft:entities/pig").getPool("main").removeEntry("minecraft:porkchop");

You are now ready to move  onto the next tutorial.
