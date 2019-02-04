### Getting an instance

### Methods
**clear**()
Removes all loot from the loot table*a*. This includes any loot added by a script before this method was run.

**addPool**(String *poolName*, int *minRolls*, int *maxRolls*, int *minBonusRolls*, int *maxBonusRolls*)
Adds a new pool with the name `poolName`. The rest of the parameters are explained on the MC Wiki page I linked in [Getting Started](..\getting-started.md). Returns the created pool.


**removePool**(**String** *poolName*)
Removes the pool with the name `poolName`

**getPool**(String *poolName*)
Returns the LootPool with the name `poolName`

Refer to [LootPool](loot-pool.md) to see what you can do with a LootPool.

##Pool Names
Pools you add have whatever name you give them.
The The first default pool in a table is named main. Successive pools are named in the format poolN, where N is a number that starts at 1 and increments for each pool.
