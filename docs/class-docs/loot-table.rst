LootTable
=========

:full name: ``loottweaker.vanilla.loot.LootTable``

Methods
-------
.. java:method:: void clear()
    :outertype: LootTable

    Removes all loot from the loot table. This includes any loot added by a script before this method was run.

.. java:method:: LootPool addPool(String poolName, int minRolls, int maxRolls, int minBonusRolls, int maxBonusRolls)
    :outertype: LootTable

    Adds a new pool to the table, and returns it.

    :param poolName: a name for the table. Must be unique within the table.
    :param minRolls: the minimum rolls of the new pool.
    :param maxRolls: the maximum rolls of the new pool.
    :param minBonusRolls: the minimum bonus rolls of the new pool.
    :param maxBonusRolls: the maximum bonus rolls of the new pool.
    :errors: if a pool with the same name already exists in the table
    :return: the new pool

.. java:method:: void removePool(String poolName)
    :outertype: LootTable

    Removes the pool with the name `poolName`.

    :param poolName: the table-unique name of the pool
    :errors: if no loot pool with the specified name exists.

.. java:method:: LootPool getPool(String poolName)
    :outertype: LootTable

    Gets a LootPool by name.

    :param poolName: the table-unique name of the pool
    :errors: if no loot pool with the specified name exists.
    :return: the loot pool with the specified name.

Pool Names
----------
Pools you add have whatever name you give them.
The first default pool in a table is named main. Successive pools are named in the format poolN, where N is a number that starts at 1 and increments for each pool.