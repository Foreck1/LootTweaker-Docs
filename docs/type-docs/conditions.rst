Conditions
==========

:full name: ``loottweaker.vanilla.loot.Conditions``

JSON can be verbose and difficult to write. This type can help.
It provides methods for creating simple loot conditions, but if you wish to use complex loot conditions you still have to write them in JSON.

All methods on this page, except ``parse()`` create a vanilla loot condition, so their parameters are equivalent to the parameters of the equivalent loot condition.
All vanilla loot conditions are listed and documented `here <https://minecraft.gamepedia.com/Loot_table#Conditions>`_.

The corresponding type for loot functions is :doc:`functions`.

Methods
-------

See :doc:`here <method-documentation-format>` for an explanation of the method documentation format used on this page.

.. java:method:: static LootCondition randomChance(float chance)
    :outertype: Conditions

    :equivalent to: ``minecraft:random_chance``

.. java:method:: static LootCondition randomChanceWithLooting(float chance, float lootingMult)
    :outertype: Conditions

    :equivalent to: ``minecraft:random_chance_with_looting``

.. java:method:: static LootCondition killedByPlayer()
    :outertype: Conditions

    :equivalent to: ``minecraft:killed_by_player``

.. java:method:: static LootCondition killedByNonPlayer()
    :outertype: Conditions

    :equivalent to: ``minecraft:killed_by_player`` with the ``inverse`` tag set to true

.. java:method:: static LootCondition parse(DataMap json)
    :outertype: Conditions

    Parses a `DataMap <https://docs.blamejared.com/1.12/en/Vanilla/Data/DataMap/>`_ into a ``LootCondition``.

    :param json: an instance of ``DataMap`` representing a LootCondition in JSON form. It is recommended that the keys are enclosed in quotes to avoid conflicts between JSON key names and ZenScript keywords.
    :return: ``json`` as a LootCondition
    :errors: if ``json`` does not parse successfully.

``minecraft:entity_properties`` and ``minecraft:entity_scores`` do not have helper methods as they are too complex.
