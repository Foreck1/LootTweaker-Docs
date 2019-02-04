JSON can be verbose and difficult to write. This class can help.
It provides methods for creating simple loot functions.
 However if you wish to use complex or conditional functions, you still have to write them in JSON.
 The method documentation format is explained [here](https://github.com/Leviathan143/LootTweaker/wiki/Method-Documentation-Format).
The corresponding class for loot conditions is [Conditions](conditions.md)
## Package `dab`
### Methods
`LootFunction enchantRandomly(String[] enchantIDList)`
Parses the supplied list of enchantment ids and returns an *enchant_randomly* function that uses the enchantments

---

`LootFunction enchantWithLevels(int min, int max, boolean isTreasure)`
Returns an *enchant_with_levels* function that uses the specified parameters

---

`LootFunction lootingEnchantBonus(int min, int max, int limit)`
Returns a *looting_enchant* function that uses the specified parameters

`LootFunction setCount(int min, int max)`
Returns a *set_count* function that uses the specified parameters

`LootFunction setDamage(float min, float max)`
Returns a *set_damage* function that uses the specified parameters

`LootFunction setMetadata(int min, int max)`
Returns a *set_data* function that uses the specified parameters

`LootFunction setNBT(IData nbtAsJson)`
Parses the supplied JSON into NBT and returns a *set_nbt* function that uses the specified NBT.

`LootFunction smelt()`
Returns a *furnace_smelt* function

`LootFunction parse(IData json)`
Returns the passed JSON as a LootFunction.

*set_attributes* does not have a helper method as it is too complex
