JSON can be verbose and difficult to write. This class can help.
It provides methods for creating simple loot conditions.
However if you wish to use complex loot conditions, you still have to write them in JSON.
The method documentation format is explained [here](method-documentation-format.md).
The corresponding class for loot functions is [Functions](functions.md)

# **Conditions**
`LootCondition randomChance(float chance)`
Returns a *random_chance* condition with the specified chance.

`LootCondition randomChanceWithLooting(float chance, float lootingMult)`
Returns a *random_chance_with_looting* condition with the specified chance and looting multiplier.

`LootCondition killedByPlayer()`
Returns a *killed_by_player* condition that is true if the entity was killed by a player

`LootCondition killedByNonPlayer()`
Returns a *killed_by_player* condition that is true if the entity was killed by a non-player

`LootCondition parse(IData json)`
Returns the passed JSON as a LootCondition.

*entity_properties* and *entity_scores* do not have helper methods as they are too complex.
