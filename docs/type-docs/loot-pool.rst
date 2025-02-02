LootPool
========

:full name: ``loottweaker.vanilla.loot.LootPool``

Each instance of this type represents a specific pool of a loot table.

Condition and function formatting
---------------------------------
Conditions and functions should be supplied to methods as JSON format maps_/ or 
:doc:`conditions`/:doc:`functions`. 
Do not supply the conditions/functions as part of a parent tag.
When using a `map`_ to supply conditions or functions, it is recommended that you 
surround the keys with double quotes("), as otherwise any keys which are 
ZenScript keywords(e.g function) will cause issues.

Recommended

.. code-block:: json

    [
       {
        "count":
        {
        "min": 0.0,
        "max": 2.0
        },
        "function": "minecraft:set_count"
       }
    ]

Not Recommended

.. code-block:: none

    [
       {
        count:
        {
        min: 0.0,
        max: 2.0
        },
        function: "minecraft:set_count"
       }
    ]

.. _autoconverted:

Converting JSON format maps to LootCondition/LootFunction
---------------------------------------------------------
As of 0.2.1 JSON format maps are automatically converted to 
:doc:`conditions`/:doc:`functions` as needed, so any LootFunction/LootCondition
parameter will accept a JSON format map.

Methods
-------

See :doc:`here <method-documentation-format>` for an explanation of the method documentation format used on this page.

void addConditions(LootCondition[] conditions)
++++++++++++++++++++++++++++++++++++++++++++++

    Adds conditions to the pool.

    :parameters:

    * conditions - an array of instances of :doc:`LootCondition <conditions>` to add.
      Maps are :ref:`automatically converted <autoconverted>`.

void removeEntry(String entryName)
++++++++++++++++++++++++++++++++++

    Removes the entry with a matching ``entryName`` tag from the pool

    :parameters:
    
    * entryName - the unique name of the target entry

    :errors: if no entry with the specified name exists in the pool

void addItemEntry(IItemStack iStack, int weight, int quality, LootFunction[] functions, LootCondition[] conditions, @Optional String name)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new ``item`` type entry to the pool.

    :parameters: 
    
    * iStack - the item stack the entry should produce. LootTweaker will autogenerate *set_nbt*, *set_damage*/*set_data* and *set_count* functions based on this stack, unless ``functions`` contains a function of the same type.
    * weight - the main component that determines the generation chance. Higher weights make entries generate more often.
    * quality - determines how much the Luck attribute affects the generation chance. Higher qualities make the luck attribute affect the generation chance more.
    * functions - :doc:`functions <functions>` that affect the stack(s) generated by the entry.
      Maps are :ref:`automatically converted <autoconverted>`.
    * conditions - :doc:`conditions <conditions>` for the generation of the entry.
      Maps are :ref:`automatically converted <autoconverted>`.
    * name - (Optional) a name for the entry. Must be unique within the pool.

    :errors: if the pool already contains an entry with the same name.

void addItemEntry(IItemStack stack, int weightIn, int qualityIn, @Optional String name)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new ``item`` type entry to the pool, with no conditions or functions.

    :parameters:
    
    * iStack - the item stack the entry should produce. LootTweaker will autogenerate *set_nbt*, *set_damage*/*set_data* and *set_count* functions based on this stack, unless ``functions`` contains a function of the same type.
    * weight - the main component that determines the generation chance. Higher weights make entries generate more often.
    * name - (Optional) a name for the entry. Must be unique within the pool.

    :errors: if the pool already contains an entry with the same name.

void addItemEntry(IItemStack stack, int weightIn, @Optional String name)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new ``item`` type entry to the pool, with no conditions or functions, and a quality of 0.

    :parameters:

    * iStack - the item stack the entry should produce. LootTweaker will autogenerate *set_nbt*, *set_damage*/*set_data* and *set_count* functions based on this stack, unless ``functions`` contains a function of the same type.
    * weight - the main component that determines the generation chance. Higher weights make entries generate more often.
    * name - (Optional) a name for the entry. Must be unique within the pool.

    :errors: if the pool already contains an entry with the same name.

void addLootTableEntry(String tableName, int weightIn, int qualityIn, LootCondition[] conditions, @Optional String name)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new ``loot_table`` type entry to the pool.

    :parameters:

    * tableName - the identifier for the table the entry should generate loot from.
    * weight - the main component that determines the generation chance. Higher weights make entries generate more often.
    * quality-  determines how much the Luck attribute affects the generation chance. Higher qualities make the luck attribute affect the generation chance more.
    * conditions - :doc:`conditions <conditions>` for the generation of the entry.
      Maps are :ref:`automatically converted <autoconverted>`.
    * name - (Optional) a name for the entry. Must be unique within the pool.

    :errors: if the pool already contains an entry with the same name.

void addLootTableEntry(String tableName, int weightIn, int qualityIn, @Optional String name)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new ``loot_table`` type entry to the pool with no conditions.

    :parameters: 
    
    * tableName - the identifier for the table the entry should generate loot from.
    * weight - the main component that determines the generation chance. Higher weights make entries generate more often.
    * quality - determines how much the Luck attribute affects the generation chance. Higher qualities make the luck attribute affect the generation chance more.
    * conditions - conditions for the generation of the entry.
    * name - (Optional) a name for the entry. Must be unique within the pool.

    :errors: if the pool already contains an entry with the same name.

void addLootTableEntry(String tableName, int weightIn, @Optional String name)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new ``loot_table`` type entry to the pool with no conditions, and a quality of 0.

    :parameters:

    * tableName - the identifier for the table the entry should generate loot from.
    * weight - the main component that determines the generation chance. Higher weights make entries generate more often.
    * quality - determines how much the Luck attribute affects the generation chance. Higher qualities make the luck attribute affect the generation chance more.
    * conditions - conditions for the generation of the entry.
    * name - (Optional) a name for the entry. Must be unique within the pool.

    :errors: if the pool already contains an entry with the same name.

void addEmptyEntry(int weight, int quality, LootCondition[] conditions, @Optional String name)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new ``empty`` type entry to the pool.

    :parameters:

    * weight - the main component that determines the generation chance. Higher weights make entries generate more often.
    * quality - determines how much the Luck attribute affects the generation chance. Higher qualities make the luck attribute affect the generation chance more.
    * conditions - :doc:`conditions <conditions>` for the generation of the entry.
      Maps are :ref:`automatically converted <autoconverted>`.
    * name - (Optional) a name for the entry. Must be unique within the pool.

    :errors: if the pool already contains an entry with the same name.

void addEmptyEntry(int weight, int quality, @Optional String name)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new ``empty`` type entry to the pool with no conditions.

    :parameters:

    * weight - the main component that determines the generation chance. Higher weights make entries generate more often.
    * quality - determines how much the Luck attribute affects the generation chance. Higher qualities make the luck attribute affect the generation chance more.
    * name - (Optional) a name for the entry. Must be unique within the pool.

    :errors: if the pool already contains an entry with the same name.

void addEmptyEntry(int weight, @Optional String name)
+++++++++++++++++++++++++++++++++++++++++++++++++++++

    Adds a new ``empty`` type entry to the pool with no conditions, and a quality of 0.

    :parameters: 
    
    * weight - the main component that determines the generation chance. Higher weights make entries generate more often.
    * quality - determines how much the Luck attribute affects the generation chance. Higher qualities make the luck attribute affect the generation chance more.
    * name - (Optional) a name for the entry. Must be unique within the pool.

    :errors: if the pool already contains an entry with the same name.

void setRolls(float min, float max)
+++++++++++++++++++++++++++++++++++

    Sets the minimum and maximum rolls of the pool to the specified values.

    :parameters:
    
    * min - the new minimum rolls value
    * max - the new maximum rolls value

void setBonusRolls(float min, float max)
++++++++++++++++++++++++++++++++++++++++

    Sets the minimum and maximum bonus rolls of the pool to the specified values.

    :parameters:

    * min - the new minimum bonus rolls value.
    * max - the new maximum bonus rolls value.
    
void clearConditions()
++++++++++++++++++++++

    Removes all loot conditions attached to this loot pool. Loot conditions and loot functions attached to child entries are unaffected.
    
void clearEntries()
+++++++++++++++++++
    
    Removes all entries from this loot pool.

.. _DataMap: https://docs.blamejared.com/1.12/en/Vanilla/Data/DataMap/
.. _map: https://docs.blamejared.com/1.12/en/AdvancedFunctions/Associative_Arrays/
.. _maps: https://docs.blamejared.com/1.12/en/AdvancedFunctions/Associative_Arrays/