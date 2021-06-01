LootContext
===========

:full name: ``loottweaker.LootContext``

Context object for loot generation

Methods
----------

See :doc:`here <method-documentation-format>` for an explanation of the method documentation format used on this page.

IEntity_ lootedEntity()
+++++++++++++++++++++++
:returns: the entity generating loot, may be null_.

IPlayer_ killerPlayer()
+++++++++++++++++++++++
:returns: the player who triggered loot generation, may be null_.

IEntity_ killer()
+++++++++++++++++
:returns: the entity that triggered loot generation, may be null_.

float luck()
++++++++++++
:returns: the luck_ level of this loot generation

IWorld_ world()
+++++++++++++++
:returns: the world loot is being generated in

int lootingModifier()
+++++++++++++++++++++
:returns: the Looting enchantment level of this loot generation

.. _IEntity: https://docs.blamejared.com/1.12/en/Vanilla/Entities/IEntity/
.. _IPlayer: https://docs.blamejared.com/1.12/en/Vanilla/Players/IPlayer/
.. _IWorld: https://docs.blamejared.com/1.12/en/Vanilla/World/IWorld/
.. _luck: https://minecraft.fandom.com/wiki/Luck
.. _null: https://docs.blamejared.com/1.12/en/Vanilla/Global_Functions/#isnull