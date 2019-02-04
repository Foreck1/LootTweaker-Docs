<p align="center"> [[&lt;&lt;Previous|Getting Started]] <b>Standard Script Structure</b> [[Next&gt;&gt;|Removing Loot]] </p>

----

In CraftTweaker and most of its add-ons/plugins, a single operation (e.g adding a recipe, removing a recipe) is performed by calling a single method. Most of these methods are also static. LootTweaker does not follow this pattern because it is not ideal for interacting with the loot table system.
In LootTweaker the general pattern is one or two methods to get the object you want to modify, followed by a single method to perform the modification. Almost all LootTweaker methods are instance methods.

**Instance vs static**  
ZenScript (The language all MineTweaker/CraftTweaker scripts are written in) supports a particular way of programming called OOP (Object Oriented Programming). In OOP the concepts of *objects* and *classes* are very important. A *class* is like a blueprint, it defines how something is made and how it works. An *object* is the result of using a *class* as a blueprint to create something, the resulting thing is called an *instance*.
To use a static field or method you only need to know the *class*. `LootTables.getTable()` is an example of a static method.  When talking about them, static methods will be referred to using the notation `class.method()` (e.g `LootTable.getPool()`, `LootPool.removeEntry()`).  
To use an instance field or method you need an *instance* of the *class*. `LootPool.removeEntry()` is an example of an instance method, an *instance* of `LootPool` is required in order to call it. When talking about them, instance methods will be referred to using the notation `class#method()` (e.g `LootTable#getPool()`, `LootPool#removeEntry()`). Note that this is notation, **not** how they are used in code.


Let's have a look at an example snippet. You won't know the methods used yet, but that's not important.
```
//Get the cow loot table and store it for later use
val cow = LootTables.getTable("minecraft:entities/cow");

//Get the pool named "main" from the cow loot table and store it for later use
val cow_main = cow.getPool("main");

//Remove leather from "main"
cow_main.removeEntry("minecraft:leather");
```
This snippet prevents cows dropping leather. It's fairly simple:
* The cow loot table is retrieved and stored
* The pool called "main" is retrieved from the table and stored
* The entry called "minecraft:leather" is removed from the pool

Two of the methods in the snippet, `getPool()` & `removeEntry()` are instance methods. They must be called on an instance of `LootTable` & `LootPool` respectively. In the case of `getPool()` the instance used is the one returned earlier by `LootTable.getTable()`. In the case of `removeEntry()` the instance used is the one returned earlier by `getPool()`. `LootTable.getTable()` is the only static method.

You are now ready to move on to the next tutorial.
