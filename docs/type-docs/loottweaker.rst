LootTweaker
===========

:full name: ``loottweaker.LootTweaker``

Methods
-------

See :doc:`here <method-documentation-format>` for an explanation of the method documentation format used on this page.

.. java:method:: static LootTable getTable(String tableName)
    :outertype: LootTweaker
    
    Gets a loot table by name.

    :param tableName: the unique name of the table.
    :errors: if no loot table exists with the specified name.
    :return: the table with the specified name.

.. java:method:: static LootTable newTable(String tableName)
    :outertype: LootTweaker
    
    Creates a new table with a given name. LootTweaker created tables behave exactly like mod created tables, with one
    exception. They cannot be dumped by ``/ct loottables byName`` or ``/ct loottables all`` at this time. 
    To view the JSON form, load a save, then check its data/loot_tables folder.

    :param tableName: the unique name of the table.
    :warns: if the table name implicitly or explicitly uses the minecraft namespace.
    :errors: if a loot table with the specified name already exists.
    :return: an empty table with the specified name.

