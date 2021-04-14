Example Script
==============

.. code-block:: none 

    import loottweaker.LootTweaker;
    import loottweaker.vanilla.loot.LootTable;
    import loottweaker.vanilla.loot.LootPool;
    import loottweaker.vanilla.loot.Conditions;
    import loottweaker.vanilla.loot.Functions;

    //Get the sheep loot table and store it for later use
    val sheep = LootTweaker.getTable("minecraft:entities/sheep");

    //Get main from the sheep loot table and store it for later use
    val main = sheep.getPool("main");

    //Add a new pool called "sweetLoot" and store it for later use
    val sweetLoot = sheep.addPool("sweetLoot", 1, 1, 1, 1);

    //Remove the entry named "minecraft:mutton" from "main"
    main.removeEntry("minecraft:mutton");
    //Set the rolls property to a minimum of 3 and a maximum of 6
    main.setRolls(3, 6);
    //Set the bonusRolls property to a minimum of 0 and a maximum of 2
    main.setBonusRolls(0, 2);

    //Drop 3 apples when killed by a player
    sweetLoot.addItemEntryHelper(<minecraft:apple> * 3, 20, 1, [], [Conditions.killedByPlayer()]);
    //Drop 4 sticks when killed by a player
    sweetLoot.addItemEntryJson(<minecraft:stick> * 4, 20, 1, [], [{"condition": "killed_by_player"}]);
    //Drop 1 potato when killed by a player while on fire
    sweetLoot.addItemEntryHelper(<minecraft:potato>, 20, 1, [], [Conditions.parse({"condition": "entity_properties", "entity": "this", "properties": {"on_fire": true}}), Conditions.killedByPlayer()]);
    //Drop 2-5 carrots
    sweetLoot.addItemEntryHelper(<minecraft:carrot>, 20, 1, [Functions.setCount(2, 5)], []);
    //Drop 3-9 redstone
    sweetLoot.addItemEntryJson(<minecraft:redstone>, 20, 1, [{"count": {"min": 3.0, "max": 9.0}, "function": "minecraft:set_count"}], []);
    //Drop 1-3 iron swords with 10-15% damage
    sweetLoot.addItemEntryHelper(<minecraft:iron_sword>, 20, 1, [Functions.parse({"count": {"min": 1.0, "max": 3.0}, "function": "minecraft:set_count"}), Functions.setDamage(0.10, 0.15)], []);

    //Add a new pool called "pigLoot" and store it for later use
    val pigLoot = sheep.addPool("pigLoot", 1, 1, 1, 1);
    //Add the pig loot table to "pigLoot"
    pigLoot.addLootTableEntry("minecraft:entities/pig", 40);
    //Add an inverse killed_by_player condition to "pigLoot"
    pigLoot.addConditionsHelper([Conditions.killedByNonPlayer()]);
