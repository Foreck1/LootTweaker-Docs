Functions
=========

:full name: ``loottweaker.vanilla.loot.Conditions``

JSON can be verbose and difficult to write. This type can help.
It provides methods for creating simple loot functions, but if you wish to use complex loot functions you still have to write them in JSON.

All methods on this page, except ``parse()`` create a vanilla loot function, so their parameters are equivalent to the parameters of the equivalent loot function.
All vanilla loot functions are listed and documented `here <https://minecraft.gamepedia.com/Loot_table#Functions>`_.

The corresponding type for loot conditions is :doc:`conditions`.

Methods
-------

See :doc:`here <method-documentation-format>` for an explanation of the method documentation format used on this page.

.. java:method :: static LootFunction enchantRandomly(String[] enchantIDList)
    :outertype: Functions

    :equivalent to: ``minecraft:enchant_randomly``
    :errors: if any enchantment ID does not resolve to an enchantment

.. java:method :: static LootFunction enchantWithLevels(int min, int max, boolean isTreasure)
    :outertype: Functions

    :equivalent to: ``minecraft:enchant_with_levels``

.. java:method :: static LootFunction lootingEnchantBonus(int min, int max, int limit)
    :outertype: Functions

    :equivalent to: ``minecraft:looting_enchant``

.. java:method :: static LootFunction setCount(int min, int max)

    :equivalent to: ``minecraft:set_count``

.. java:method :: static LootFunction setDamage(float min, float max)
    :outertype: Functions

    :equivalent to: ``minecraft:set_damage``
    :errors: if ``max`` is greater than 1.0

.. java:method :: static LootFunction setMetadata(int min, int max)
    :outertype: Functions

    :equivalent to: ``minecraft:set_data``

.. java:method :: static LootFunction setNBT(DataMap nbtAsJson)
    :outertype: Functions

    :equivalent to: ``minecraft:set_nbt``

.. java:method :: static LootFunction smelt()
    :outertype: Functions

    :equivalent to: ``minecraft:furnace_smelt``

.. java:method :: static LootFunction parse(DataMap json)
    :outertype: Functions

    Parses a `DataMap <https://crafttweaker.readthedocs.io/en/latest/#Vanilla/Data/DataMap/>`_ into a ``LootFunction``.

    :param json: an instance of ``DataMap`` representing a LootCondition in JSON form. It is recommended that the keys are enclosed in quotes to avoid conflicts between JSON key names and ZenScript keywords.
    :return: ``json`` as a LootFunction.
    :errors: if ``json`` is not a ``DataMap``.

``minecraft:set_attributes`` does not have a helper method as it is too complex.
