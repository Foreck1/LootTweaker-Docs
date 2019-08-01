Adding Loot (Basic)
===================

In this tutorial you will learn the basics of adding loot to a loot table. This tutorial covers quality, weight, luck, the different types of loot entries, the basics of loot generation, and basic loot addition. Conditions and functions are covered in the next tutorial.

A basic overview of loot generation
-----------------------------------
To generate loot from a loot table, each pool in the table is asked to generate loot.
Each pool then checks that all the conditions attached to it output true. If they do,
it calculates a number **t** based on the `rolls` & `bonus_rolls` parameters of that pool and the player's luck.
The pool then generates a list of all the entries it contains with conditions that all output true.
**t** entries are picked from this list and their loot generated, which entries are picked is
influenced by the `weight` & `quality` parameters of each entry and the player's luck.

Weight, quality & luck
++++++++++++++++++++++
All loot entries have a `weight` & a `quality`. These are combined with the player's luck to get an entry's "effective weight", using the formula `floor(weight + quality * luck)`. As you can see `weight` is the base value, and `quality` affects how much luck affects the effective weight. It is important to note that the weight system is relative. If you have 5 items, giving them the weights (10, 20, 30, 40, 50) will result in exactly the same generation chances as the weights (1, 2, 3, 4, 5) or (5, 10, 15, 20, 25) . Entries that are "heavier" than other entries are more likely to generate, the chance of a loot entry generating is the effective weight of the entry divided by the total effective weight of all entries in the pool.
The player's luck defaults to 0. In vanilla, it can be increased by the Luck status effect, or by the Luck of the Sea enchantment (only increases luck for fishing); it can be decreased by the Unluck status effect.

Types of loot entries
---------------------
In vanilla, there are 3 types of loot entries:
* Item entry - Generates an item. Takes functions as well as conditions.
* Loot table entry - Generates loot from another loot table.
* Empty entry - Generates nothing.

Adding loot
-----------
To add loot, you'll need to know the name of the loot table and the name of the pool you want to add it to (Unless you want to create your own pool), plus some other stuff that depends on the type of loot entry you want to add. The first two things can be found using the methods detailed in the previous tutorial.

| As an example, I'll add an apple to a new pool called "steve" in the cow loot table.
| First I get the cow loot table.
| ``val cow = LootTables.getTable("minecraft:entities/cow");``
| Then I create a pool called "steve" and store it. The last 4 parameters are minimum rolls, maximum rolls, minimum bonus rolls, and maximum bonus rolls, respectively.
| ``val steve = cow.addPool("steve", 1, 1, 0, 0);``
| If you want to add to an existing pool, call `LootTable#getPool()` on the table and pass it the name of the pool.

| Finally, I add an apple to steve.
| ``steve.addItemEntry(<minecraft:apple>, 5);``
| The last parameter is the weight.

The Complete Script
-------------------
Here's the script in one block, for easier reading ::

    // Get the cow loot table and store it for later use
    val cow = LootTables.getTable("minecraft:entities/cow");
    // Add a pool called steve to the cow loot table, then store it for later use
    val steve = cow.addPool("steve", 1, 1, 0, 0);
    // Add an apple to "steve"
    steve.addItemEntry(<minecraft:apple>, 5);


.. note::

    Since weight is relative, there are no other entries in this pool, and the minimum number of rolls is one, this entry will always be generated.  If the minimum number of rolls was less than one, the pool might pick a non-positive value for **t** and not generate anything.
    You may also remember that Forge requires loot entries to be named. Notice that I do not need to specify a name, this is because LootTweaker generates a unique name automatically if one is not specified. If I wanted to name the entry "stevelikesapples", I would add it like this. Note that if you specify a name you must ensure that it is unique.
    ``steve.addItemEntry(<minecraft:apple>, 5, "stevelikesapples");``
