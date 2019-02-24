Conditions
==========
JSON can be verbose and difficult to write. This class can help.
It provides methods for creating simple loot conditions, but if you wish to use complex loot conditions you still have to write them in JSON.

The corresponding class for loot functions is :doc:`functions`.

Methods
-------

.. java:method:: LootCondition randomChance(float chance)

    :param chance: a percentage chance in decimal form
    :return: a *random_chance* condition with the specified chance.

.. java:method:: LootCondition randomChanceWithLooting(float chance, float lootingMult)

    :param chance: a percentage chance in decimal form
    :param lootingMult: a percentage chance in decimal form
    :return: a *random_chance_with_looting* condition with the specified chance and looting multiplier

.. java:method:: LootCondition killedByPlayer()

    :return: a *killed_by_player* condition that is true if the entity was killed by a player

.. java:method:: LootCondition killedByNonPlayer()

    :return: a *killed_by_player* condition that is true if the entity was killed by a non-player

.. java:method:: LootCondition parse(IData json)

    :param json: Valid JSON for a LootCondition
    :return: the passed JSON as a LootCondition.

*entity_properties* and *entity_scores* do not have helper methods as they are too complex.