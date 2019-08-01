Forge Loot Table Format
=======================

The Forge loot table format is fully compatible with vanilla and almost identical to the vanilla loot table format.
The only difference is that Forge requires pools and entries to have names.

.. note:: Pool names must be unique within their parent table, and entry names must be unique within their parent pool.

When adding entries using LootTweaker, you do not need to ensure the names of entries are unique.
LootTweaker will handle this itself, and autogenerate a name if you do not provide one. You **do** however,
need to ensure that the names of any pools you add using LootTweaker are unique.

Default names
-------------
If no name is supplied, Forge defaults to using:

Item/block entries
    The registry name of the item/block

Loot table entries
    The name of the referenced table

Empty loot entries
    The string 'empty'

Loot pools
    The first unnamed pool in a table is named 'main', any other unnamed pools are named in the format 'pool*n*',
    where *n* is a number that starts at 1 and is incremented for every unnamed pool.

    So the first unnamed pool would be called 'main', the second unnamed pool 'pool1', the third unnamed pool 'pool2', etc.

.. note:: Loot table entries are entries that reference another loot table, **not** a generic term for all types of entries that can go in a loot pool.

Finding names
-------------
To find the name of an existing entry or pool:
    1. Use one of :doc:`these commands <commands>` to dump the table as a .json file
    2. Find and open the dumped .json file
    3. If you want to know the name of a pool, look for the ``name`` property. If you want to know the name of an entry, look for the ``entryName`` property.
