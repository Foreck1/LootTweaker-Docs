Functions
=========

:full name: ``loottweaker.vanilla.loot.Functions``

JSON can be verbose and difficult to write. This type can help.
It provides methods for creating simple loot functions, but if you wish to use complex loot functions you still have to write them in JSON.
``minecraft:set_attributes`` does not have a helper method as it is too complex.

All methods on this page, except ``parse()`` create a vanilla loot function, so their parameters are equivalent to the parameters of the equivalent loot function.
All vanilla loot functions are listed and documented `here <https://minecraft.gamepedia.com/Loot_table#Functions>`_.

The corresponding type for loot conditions is :doc:`conditions`.

Methods
-------

See :doc:`here <method-documentation-format>` for an explanation of the method documentation format used on this page.

static LootFunction enchantRandomly(String[] enchantIDList)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    :equivalent to: ``minecraft:enchant_randomly``
    :errors: if any enchantment ID does not resolve to an enchantment

static LootFunction enchantWithLevels(int min, int max, boolean isTreasure)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    :equivalent to: ``minecraft:enchant_with_levels``

static LootFunction lootingEnchantBonus(int min, int max, int limit)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    :equivalent to: ``minecraft:looting_enchant``

static LootFunction setCount(int min, int max)
++++++++++++++++++++++++++++++++++++++++++++++

    :equivalent to: ``minecraft:set_count``

static LootFunction setDamage(float min, float max)
+++++++++++++++++++++++++++++++++++++++++++++++++++

    :equivalent to: ``minecraft:set_damage``
    :errors: if ``max`` is greater than 1.0

static LootFunction setMetadata(int min, int max)
+++++++++++++++++++++++++++++++++++++++++++++++++

    :equivalent to: ``minecraft:set_data``

static LootFunction setNBT(DataMap nbtData)
+++++++++++++++++++++++++++++++++++++++++++

    :equivalent to: ``minecraft:set_nbt``
    :errors: if ``nbtData`` is not a compound tag

static LootFunction smelt()
+++++++++++++++++++++++++++

    :equivalent to: ``minecraft:furnace_smelt``

static LootFunction parse(DataMap json)
+++++++++++++++++++++++++++++++++++++++

    Parses a `DataMap <https://docs.blamejared.com/1.12/en/Vanilla/Data/DataMap/>`_ into a ``LootFunction``.

    :parameters: 
        * json - an instance of ``DataMap`` representing a LootCondition in JSON form. It is recommended that the keys are enclosed in quotes to avoid conflicts between JSON key names and ZenScript keywords.
    :returns: ``json`` as a LootFunction.
    :errors: if ``json`` does not parse successfully.
