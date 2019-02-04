<p align="center"> [[&lt;&lt;Previous|Standard Script Structure]] <b>Removing Loot</b> [[Next&gt;&gt;|Adding Loot (Basic)]] </p>

----
In this tutorial you will learn how to remove loot from a loot table. I will be removing porkchops from the pig loot table as an example. To do this we need to know 3 things, the name of the pig's loot table, the name of the pool with the porkchop entry, and the name of the porkchop entry. To obtain that information follow these steps:
1. Launch Minecraft
2. Open the instance folder for the instance of Minecraft you launched. If you don't know where this is a simple way to find it is Options->Resource Packs->Open Resource Pack Folder, this opens the resourepacks folder which is inside the instance folder.
3. **Finding the loot table name**
 If the loot table you want to modify is added by a mod, try looking at the documentation for that mod to find its name. If it's a vanilla loot table, a list of vanilla tables can be found [here](https://minecraft.gamepedia.com/Loot_table#List_of_loot_tables).
If one of those options worked goto 3a. If neither of those options worked goto 3b.
3a. Run the command `/ct loottables byName <insert loot table name here>`
3b. If the table is for an entity, spawn the entity ingame. If it's for a loot chest, find a loot container that you think has the right loot table and **do not** open it. Now look at the entity/chest and run the command `/ct loottables target`.
4. **Finding the pool name & entry name**
Go to the instance folder and open the subfolder called dumps. You'll find the loot table in here as json with the path `dumps/loot_tables/<domain>/<path>.json`, so a loottable named `awesomemod:chests/awesomechest` would have the path `dumps/loot_tables/awesomemod/chests/awesomechest.json`. If you don't know the name of the loot table you'll just have to rummage around in the dumps folder until you find it. In the case of the pig loot table, it is called `minecraft:entities/pig`
5. Open the loot table JSON. In the case of the pig, the JSON looks like this:
```json
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
```
6. The first thing to do, is to find the entry. We're looking for the entry with a `name` tag that is the same as the registry name of porkchops, which is `minecraft:porkchop`. The item you're looking for may have NBT and/or metadata, in that case you'll need to check the `functions` tag, and look at the `set_nbt` and `set_data` functions, respectively.  
7. Look for the `entryName` tag for the entry you just found. It will often have the same value as the `name` tag, but not always. Remember or note down the value of `entryName`. In this case the value is `minecraft:porkchop`.
8. Find the pool the entry is in and remember or note down the value of `name`. In this case it's in the pool called `main`.
9. Now comes the simple part. In your script import `loottweaker.vanilla.loot.LootTables`, `loottweaker.vanilla.loot.LootTable`, `loottweaker.vanilla.loot.LootPool`. Then combine `LootTables.getTable()`, `LootTable#getPool()` & `LootPool#removeEntry()` with the table, pool and entry names you found earlier.
10. The resulting script for removing porkchops from the pig loot table looks like this. Yours should look similar.  

```javascript
//Import necessary classes
import loottweaker.vanilla.loot.LootTables;  
import loottweaker.vanilla.loot.LootTable;  
import loottweaker.vanilla.loot.LootPool;

//Get the loot table named "minecraft:entities/pig" and store it for later use
val pig = LootTables.getTable("minecraft:entities/pig");
//Get the pool named "main" from the loot table and store it for later use
val pigMain = pig.getPool("main");
//Remove the entry named "minecraft:porkchop" from the loot pool
pigMain.removeEntry("minecraft:porkchop");
```
The key thing here is not the arrangement of the methods, but the methods used, the parameters passed to them and the objects they are called on. The below script does exactly the same thing as the above script and is also valid. I recommend the above style when modifying a table or pool more than once, as it is more concise and readable.
```javascript  
import loottweaker.vanilla.loot.LootTables;  
import loottweaker.vanilla.loot.LootTable;  
import loottweaker.vanilla.loot.LootPool;

 LootTables.getTable("minecraft:entities/pig").getPool("main").removeEntry("minecraft:porkchop");
```
You are now ready to move onto the next tutorial.
