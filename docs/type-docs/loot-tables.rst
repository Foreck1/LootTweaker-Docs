LootTables
==========

:full name: ``loottweaker.vanilla.loot.LootTables``

Methods
-------

See :doc:`here <method-documentation-format>` for an explanation of the method documentation format used on this page.

.. java:method:: static LootTable getTable(String tableName)
    :outertype: LootTables

    Gets a loot table by name.

    :param tableName: the unique name of the table.
    :errors: if no registered table exists with the specified name.
    :return: the table with the specified name.

.. java:method:: static LootTable getTableUnchecked(String tableName)
    :outertype: LootTables

    Gets a loot table by name, without checking if it is registered with the registry of built-in loot tables.
    This is intended for modifying :doc:`inject tables </tutorials/modifying-inject-tables>`. Its use for any
    other purpose is not supported.

    :param tableName: the unique name of the table.
    :return: the table with the specified name.

Registered Tables
-----------------
``getTable()`` only works for tables that exist and are registered with vanilla's registry. Most mods register their tables, but some do not.
Most loot tables should be registered, but some should not. See :doc:`this tutorial </tutorials/modifying-inject-tables>` for a complete explanation.
