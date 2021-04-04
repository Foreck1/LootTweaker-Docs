LootTable
=========

:full name: ``loottweaker.vanilla.loot.LootTable``

Methods
-------

See :doc:`here <method-documentation-format>` for an explanation of the method documentation format used on this page.

void clear()
++++++++++++

    Removes all loot from the loot table. This includes any loot added by a script before this method was run.

LootPool addPool(String poolName, float minRolls, float maxRolls, float minBonusRolls, float maxBonusRolls)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new pool to the table, and returns it.

    :parameters:

    * poolName - a name for the table. Must be unique within the table.
    * minRolls - the minimum rolls of the new pool.
    * maxRolls - the maximum rolls of the new pool.
    * minBonusRolls-  the minimum bonus rolls of the new pool.
    * maxBonusRolls - the maximum bonus rolls of the new pool.

    :errors: if a pool with the same name already exists in the table
    :returns: the new pool

void removePool(String poolName)
++++++++++++++++++++++++++++++++

    Removes the pool with the name `poolName`.

    :parameters:

    * poolName - the table-unique name of the pool

    :errors: if no loot pool with the specified name exists.

LootPool getPool(String poolName)
+++++++++++++++++++++++++++++++++

    Gets a LootPool by name.

    :parameters:

    * poolName - the table-unique name of the pool

    :errors: if no loot pool with the specified name exists.
    :returns: the loot pool with the specified name.

Pool Names
----------
Pools you add have whatever name you give them.
The first default pool in a table is named main. Successive pools are named in the format poolN,
where N is a number that starts at 1 and increments for each pool.