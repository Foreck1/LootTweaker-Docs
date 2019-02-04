The Forge loot table format is fully compatible with vanilla and almost identical to the vanilla loot table format. The only difference is that Forge requires pools and entries to have names.  

 Pool names must be unique within their parent table, and entry names must be unique within their parent pool.  

When adding entries using LootTweaker, you do not need to ensure the names of entries are unique. LootTweaker will handle this itself, and autogenerate a name if you do not provide one. You **do** however, need to ensure that the names of any pools you add using LootTweaker are unique.  

**Default names**  
If no name is supplied, Forge defaults to using the following:  
* Item/block entries - the registry name of the item/block   
* Loot table entries\* - the name of the referenced table  
* Empty loot entries - the string 'empty'  
* Loot pools - the first unnamed pool in a table is named 'main', any other unnamed pools are named in the format 'pool*n*', where *n* is a number that starts at 1 and is incremented for every unnamed pool. So the first unnamed pool would be called 'main', the second unnamed pool 'pool1', the third unnamed pool 'pool2', etc.

\*These are entries that reference another loot table, **not** a generic term for all types of entries that can go in a loot pool  

**Finding names**  
* To find the name of an existing entry or pool:  
* Use one of [[these commands|Commands]] to dump the table as a .json file  
* Find and open the dumped .json file  
* If you want to know the name of a pool, look for the `name` property. If you want to know the name of an entry, look for the `entryName` property.
