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

Below is a list of all the deprecated methods. It explains why they were deprecated, what their replacement is, when they were deprecated,
and when they will be removed. The most recent deprecations are at the top

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
    :Replacement: ``LootPool#addConditionsJSON(DataMap[] conditions)``
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
    :Replacement: ``LootPool#addItemEntryJSON(IItemStack iStack, int weight, int quality, DataMap[] functions, DataMap[] conditions, @Optional DataMap name)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``LootPool#addLootTableEntryJSON(String tableName, int weightIn, int qualityIn, String[] conditions, @Optional String name)``
-----------------------------------------------------------------------------------------------------------------------------
    :Reason: Using strings to take JSON input has issues with nested quotes. Using DataMap avoids this problem.
    :Replacement: ``LootPool#addLootTableEntryJSON(DataMap tableName, int weightIn, int qualityIn, DataMap[] conditions, @Optional DataMap name)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8

``LootPool#addEmptyEntryJSON(int weight, int quality, String[] conditions, @Optional String name)``
---------------------------------------------------------------------------------------------------
    :Reason: Using strings to take JSON input has issues with nested quotes. Using DataMap avoids this problem.
    :Replacement: ``LootPool#addEmptyEntryJSON(int weight, int quality, DataMap[] conditions, @Optional DataMap name)``
    :Deprecated: 0.0.7
    :Removed: 0.0.8
