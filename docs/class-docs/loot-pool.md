**Methods**
There are several methods that can be called on a LootPool. They are listed and briefly explained below. The documentation format is explained [here](method-documentation-format.md).

`addConditionsJson(IData[] conditions)`
Parses the condition string array and adds the conditions to the pool. Only supports JSON format conditions.

`addConditionsHelper(LootCondition[] conditions)`
Parses the condition string array and adds the conditions to the pool. Only supports conditions created using the Conditions helper class. JSON conditions can be parsed into LootConditions using Conditions.parse().

`removeEntry(String entryName)`
Removes the specified entry from the pool

`addItemEntryJson(IItemStack iStack, int weight, int quality, IData[] functions, IData[] conditions)`
Adds the specified stack to the pool with the specified weight, quality, functions and conditions.
Only supports JSON format conditions and functions.
weight, quality, functions and conditions are explained on the MC Wiki page linked in [Getting Started](..\getting-started.md)

`addItemEntryHelper(IItemStack iStack, int weight, int quality, LootFunction[] functions, LootCondition[] conditions)`
Adds the specified stack to the pool with the specified weight, quality, functions and conditions.
Only supports conditions & functions created using the Conditions & Functions helper classes, respectively.
JSON conditions can be parsed into LootConditions using Conditions.parse(). JSON functions can be parsed into LootFunctions using Functions.parse().

`addItemEntry(IItemStack stack, int weightIn, int qualityIn, @Optional String name)`
Equivalent to `addItemEntryJson(stack, weightIn, qualityIn, "", "");`

`addItemEntry(IItemStack stack, int weightIn, @Optional String name)`
Equivalent to `addItemEntry(stack, weightIn, 1);`

`addLootTableEntryJson(String tableName, int weightIn, int qualityIn, IData[] conditions, @Optional String name)`
Adds the specified loot table to the pool as an entry, with the specified weight, quality, functions, conditions and name.
weight, quality, functions and conditions are explained on the MC Wiki page linked  in [Getting Started](..\getting-started.md). Only supports JSON format conditions.

`addLootTableEntryHelper(String tableName, int weightIn, int qualityIn, LootCondition[] conditions, @Optional String name)`
Adds the specified loot table to the pool as an entry, with the specified weight, quality, functions, conditions and name. Only supports conditions created using the Conditions helper class. JSON conditions can be parsed into LootConditions using Conditions.parse().

`addLootTableEntry(String tableName, int weightIn, int qualityIn, @Optional String name)`
Equivalent to `addLootTableEntry(tableName, weightIn, qualityIn, []);`

`addLootTableEntry(String tableName, int weightIn, @Optional String name)`
Equivalent to `addLootTableEntry(tableName, weightIn, 1);`

`addEmptyEntry(int weight, @Optional String name)`
Equivalent to `addEmptyEntry(weightIn, 1);`

`addEmptyEntry(int weight, int quality, @Optional String name)`
Equivalent to `addEmptyEntryJson(weightIn, 1, [], []);`

`addEmptyEntryJson(int weight, int quality, IData[] conditions, @Optional String name)`
Adds an empty entry to the pool, with the specified weight, quality, functions, conditions and name.
weight, quality, functions and conditions are explained on the MC Wiki page linked  in [Getting Started](..\getting-started.md). Only supports JSON format conditions. Empty entries generate no loot when picked.

`addEmptyEntryHelper(int weight, int quality, ZenLootConditionWrapper[] conditions, @Optional String name)`
Adds an empty entry to the pool with the specified weight, quality, functions and conditions.
Only supports conditions & functions created using the Conditions & Functions helper classes, respectively.
JSON conditions can be parsed into LootConditions using Conditions.parse(). Empty entries generate no loot when picked.

`setRolls(float min, float max)`
Sets the rolls property of the pool to the specified value

`setBonusRolls(float min, float max)`
Sets the bonusRolls property of the pool to the specified value

**Condition and function formatting**
Conditions and functions should be supplied to methods as IData arrays or [helper class methods](). Do not supply the conditions as part of a parent tag. When using IData to supply conditions or functions, it is recommended that you surround the keys with double quotes("), as otherwise any keys which are zenscript keywords(e.g function) will cause issues.
Recommended:
```json
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
```
Not Recommended:
```json
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
```
