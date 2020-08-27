LootTweaker
===========

:full name: ``loottweaker.LootTweaker``

An instance of this type is available to all scripts through the variable ``lootTweakerApi``.

Methods
-------

See :doc:`here <method-documentation-format>` for an explanation of the method documentation format used on this page.

.. java:method:: void tweakLootTable(String tableName, ZenFunction tweaks)
    :outertype: LootTweaker
    
    Applies ``tweaks`` to the table identified by ``tableName`` when it loads. 

    :param tableName: the unique name of the table.
    :param tweaks: a function taking a single argument of type ``loottweaker.LootTable``, and returning nothing.
    :errors: if no loot table exists with the specified name.

.. java:method:: void onLootTable(String tableName, ZenFunction tweaks)
    :outertype: LootTweaker
    
    Calls ``tweaks`` whenever any loot table loads, except tables from the ``data`` folder of a world.

    :param tableName: the unique name of the table.
    :param tweaks: a function taking a single argument of type ``loottweaker.LootTableLoadEvent``, and returning nothing.

.. java:method:: void createLootTable(String tableName, ZenFunction tweaks)
    :outertype: LootTweaker
    
    Creates a new table with a given name. LootTweaker created tables behave exactly like mod created tables, with one
    exception; they cannot be dumped by ``/ct loottables byName`` or ``/ct loottables all`` at this time. 
    To view the JSON form, load a save, then check its data/loot_tables folder.

    :param tableName: the unique name of the table.
    :param tweaks: a function taking a single argument of type ``loottweaker.LootTable``, and returning nothing.
    :warns: if the table name implicitly or explicitly uses the minecraft namespace.  
    :errors: if a loot table with the specified name already exists.

