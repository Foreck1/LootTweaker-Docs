Modifying Inject Tables
=======================

What are inject tables?
-----------------------
Inject tables are my term for a loot table that is only used by `loot_table` type entries, not by any ingame feature.
An inject table is a common way for mods to add pools or entries to existing loot tables, while allowing other mods to
edit the added loot if necessary. Most alternate ways are quite difficult to implement, due to how Forge's loot table modification works.
Since they aren't really loot tables in their own right, I currently recommend that they are not registered as built-in loot tables,
as I suspect they may have unexpected effects otherwise.

Vanilla has no inject tables, though ``minecraft:entities/sheep`` is very similar to an inject table.
Its main use is to include mutton in all sheep loot tables, however
it is also used directly for sheared sheep drops, making it not an inject table.

Modifying Inject Tables
-----------------------
Modifying an inject table is almost exactly the same as modifying a regular loot table. The only difference is that you must use
``LootTables.getTableUnchecked()`` instead of ``LootTables.getTable()``, since inject tables are not registered as built-in loot tables.
Though ``LootTables.getTableUnchecked()`` cannot check the loot table exists for technical reasons beyond my control, you can still check
that the loot table was successfully found by checking crafttweaker.log. If it was found, there will be a log message "Applied tweaks
to table <table_name>". If it wasn't found, the log message will be absent.
