LootTables
==========

:full name: ``loottweaker.vanilla.loot.LootTables``

Methods
-------

.. java:method:: static LootTable getTable(String tableName)
    :outertype: LootTables

    Gets a loot table by name.

    :param tableName: the unique name of the table.
    :errors: if no registered table exists with the specified name.
    :return: the table with the specified name.

Registered Tables
-----------------
``getTable()`` only works for tables that exist and are registered with vanilla's registry. Most mods register their tables, but some do not. 
Most loot tables should be registered, but some should not, a feature is in the works to allow LootTweaker scripts to modify unregistered tables.