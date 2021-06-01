Deprecations
============
What does deprecated mean?
--------------------------
Sometimes I discover better ways of doing things that require me to change how the methods and types I expose to ZenScript are used.
To avoid breaking scripts, I leave the old methods in and add new methods that do things the new, better way.
However the use of the old methods is discouraged, they are undocumented, unsupported, and LootTweaker will warn you if you use them.
Eventually the old methods will be removed, but until then there is a period where both work, allowing you to transition when you want to.
This is called deprecation.

.. note:: Deprecation warnings can be disabled in LootTweaker's config. The config option will reset if you change the installed version of LootTweaker.

Below is a list of all the deprecated methods & classes. It explains why they were deprecated, what their replacement is, when they were deprecated,
and when they were be removed. The most recent deprecations are at the top

Methods with the Json or Helper suffix
--------------------------------------
    :Reason: As of 0.2.1 JSON format maps are automatically converted to 
     LootConditions/LootFunctions as needed.
    :Replacement: Method with the same name minus the suffix, e.g:

        * addItemEntryHelper => addItemEntry
        * addItemEntryJson => addItemEntry

    :Deprecated: 0.2.1
    :Removed: Future version

``Functions.parse(DataMap json)``
---------------------------------
    :Reason: As of 0.2.1 JSON format maps are automatically converted to 
     LootConditions/LootFunctions as needed.
    :Replacement: Passing the DataMap directly, or casting to LootFunction 
     using ``someMap as LootFunction``.
    :Deprecated: 0.2.1
    :Removed: Future version

``Conditions.parse(DataMap json)``
----------------------------------
    :Reason: As of 0.2.1 JSON format maps are automatically converted to 
     LootConditions/LootFunctions as needed.
    :Replacement: Passing the DataMap directly, or casting to LootCondition 
     using ``someMap as LootCondition``.
    :Deprecated: 0.2.1
    :Removed: Future version

``loottweaker.vanilla.loot.LootTables``
---------------------------------------
    :Reason: The ``loottweaker.vanilla.loot.LootTables`` class was replaced by ``loottweaker.LootTweaker`` to fix confusion between it and ``loottweaker.vanilla.loot.LootTable``.
    :Replacement: ``loottweaker.LootTweaker``
    :Deprecated: 0.2.0
    :Removed: Future version

``loottweaker.vanilla.loot.LootTables.getTable(String tableName)``
------------------------------------------------------------------
    :Reason: The ``loottweaker.vanilla.loot.LootTables`` class was replaced by ``loottweaker.LootTweaker`` to fix confusion between it and ``loottweaker.vanilla.loot.LootTable``.
    :Replacement: ``loottweaker.LootTweaker.getTable(String tableName)``
    :Deprecated: 0.2.0
    :Removed: Future version

``loottweaker.vanilla.loot.LootTables.getTableUnchecked(String tableName)``
---------------------------------------------------------------------------
    :Reason: Improvements in how ``loottweaker.vanilla.loot.LootTables.getTable(String tableName)`` validates table ids made this method obsolete. `getTable()` can now get any table.
    :Replacement: ``loottweaker.vanilla.loot.LootTables.getTable(String tableName)``
    :Deprecated: 0.1.0
    :Removed: Future version

``Functions.parse(String json)``
--------------------------------
    :Reason: Using strings to take JSON input has issues with nested quotes. Using DataMap avoids this problem.
    :Replacement: ``Functions.parse(DataMap json)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``Functions.setNBT(String json)``
---------------------------------
    :Reason: Using strings to take JSON input has issues with nested quotes. Using DataMap avoids this problem.
    :Replacement: ``Functions.setNBT(DataMap json)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``Conditions.parse(String json)``
---------------------------------
    :Reason: Using strings to take JSON input has issues with nested quotes. Using DataMap avoids this problem.
    :Replacement: ``Conditions.parse(DataMap json)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``LootPool#addConditionsJSON(String[] conditions)``
---------------------------------------------------
    :Reason: Using strings to take JSON input has issues with nested quotes. Using DataMap avoids this problem.
    :Replacement: ``LootPool#addConditionsJson(DataMap[] conditions)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``LootPool#removeItemEntry(IItemStack stack)``
----------------------------------------------
    :Reason: Has no benefits over ``LootPool#removeEntry(String name)``. ``removeEntry("minecraft:potato")`` is equivalent to ``removeItemEntry(<minecraft:potato>)``. I messed up the description badly too, confusing people.
    :Replacement: ``LootPool#removeEntry(String name)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``LootPool#removeLootTableEntry(String tableName)``
---------------------------------------------------
    :Reason: Has no benefits over ``LootPool#removeEntry(String name)``. ``removeEntry("minecraft:chests/simple_dungeon")`` is equivalent to ``removeLootTableEntry("minecraft:chests/simple_dungeon")``. I messed up the description badly too, confusing people.
    :Replacement: ``LootPool#removeEntry(String name)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``LootPool#addItemEntryJSON(IItemStack iStack, int weight, int quality, String[] functions, String[] conditions, @Optional String name)``
-----------------------------------------------------------------------------------------------------------------------------------------
    :Reason: Using strings to take JSON input has issues with nested quotes. Using DataMap avoids this problem.
    :Replacement: ``LootPool#addItemEntryJson(IItemStack iStack, int weight, int quality, DataMap[] functions, DataMap[] conditions, @Optional DataMap name)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``LootPool#addLootTableEntryJSON(String tableName, int weightIn, int qualityIn, String[] conditions, @Optional String name)``
-----------------------------------------------------------------------------------------------------------------------------
    :Reason: Using strings to take JSON input has issues with nested quotes. Using DataMap avoids this problem.
    :Replacement: ``LootPool#addLootTableEntryJson(DataMap tableName, int weightIn, int qualityIn, DataMap[] conditions, @Optional DataMap name)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``LootPool#addEmptyEntryJSON(int weight, int quality, String[] conditions, @Optional String name)``
---------------------------------------------------------------------------------------------------
    :Reason: Using strings to take JSON input has issues with nested quotes. Using DataMap avoids this problem.
    :Replacement: ``LootPool#addEmptyEntryJson(int weight, int quality, DataMap[] conditions, @Optional DataMap name)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8
