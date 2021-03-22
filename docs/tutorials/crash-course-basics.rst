Crash Course in the Basics
==========================

LootTweaker makes use of some features of CraftTweaker that you may not be familiar with, even if you have used CraftTweaker before.
This tutorial provides a quick crash course in those features.

Crash Course in Object Oriented Programming
-------------------------------------------
| ZenScript (The language all MineTweaker/CraftTweaker scripts are written in) supports a particular way of programming called Object Oriented Programming (OOP).
| The following OOP terms are used in this documentation

type
    a definition of a particular kind of thing and how it behaves.

instance
    a representation of particular kind of thing. Created from a type.

As an example, consider the type ``loottweaker.vanilla.loot.LootPool``, which represents a loot pool.
There is only one type called ``loottweaker.vanilla.loot.LootPool``, but there are many instances of it,
one for each loot pool.

method
    a named section of runnable code

call
    to make a method run its code

parameter
    data that must be supplied to call a method

return
    a method is said to 'return' when it stops running its code. Some methods output an instance when they return.

static method
    a method that can be used *without* an instance of the type it is defined by.

instance method
    a method or field that can only be used *with* an instance of the type it is defined by.

| An example of a static method is the method ``getTable`` of the type ``loottweaker.LootTweaker``.
| Calling it looks something like this ``loottweaker.LootTweaker.getTable("minecraft:entities/pig")``.
| Common notation for a static method is ``type_name.method_name()``, e.g. ``LootTweaker.getTable()``. Parameters are not included in the notation.

| An example of an instance method is the method ``getPool`` of the type ``loottweaker.vanilla.loot.LootTable``.
| Calling it looks something like this ``pigTable.getPool("main")``, where ``pigTable`` is an instance of ``loottweaker.vanilla.loot.LootTable``.
| Common notation (not syntax, so not valid code!) for an instance method is ``type_name#method_name()``, e.g. ``LootTable#getPool()``. Parameters are not included in the notation.

Crash Course in Local Variables
-------------------------------
ZenScript allows you to store a particular piece of data for later under a particular name.
This is done using the **var** & **val** keywords,
the difference is that **var** allows you to change the piece of data the name refers to, while **val** does not.
They allow you to replace this::

    LootTweaker.getTable("foo").getPool("bar").removeEntry("baz");
    LootTweaker.getTable("foo").getPool("bar").removeEntry("qux");

with this::

    val fooBar = LootTweaker.getTable("foo").getPool("bar");
    fooBar.removeEntry("baz");
    fooBar.removeEntry("qux");

Much easier to read isn't it? Note that they store the value returned by the call on the right side of the =,
they do not execute that code when referenced.
More information about `local variables <http://crafttweaker.readthedocs.io/en/latest/#Vanilla/Variable_Types/Variable_Types/>`_.

Explanation of an Example Snippet
---------------------------------
Let's have a look at an example snippet. You won't know the methods used yet, but that's not important.::

    //Get the cow loot table and store it for later use
    val cow = LootTweaker.getTable("minecraft:entities/cow");

    //Get the pool named "main" from the cow loot table and store it for later use
    val cow_main = cow.getPool("main");

    //Remove leather from "main"
    cow_main.removeEntry("minecraft:leather");

This snippet prevents cows dropping leather.

1. The cow loot table is retrieved and stored
2. The pool called "main" is retrieved from the table and stored
3. The entry called "minecraft:leather" is removed from the pool

Two of the methods in the snippet, `getPool()` & `removeEntry()` are instance methods. They must be called on an instance of `LootTable` & `LootPool` respectively. In the case of `getPool()` the instance used is the one returned earlier by `LootTable.getTable()`. In the case of `removeEntry()` the instance used is the one returned earlier by `getPool()`. `LootTable.getTable()` is the only static method.

You are now ready to move on to the next tutorial.
