Getting Started
===============
Out of the suite of CraftTweaker Add-Ons, LootTweaker tends to be one of the most complicated to get a handle on.
This is due, in large part, to the complexity of Minecraft’s loot system and the difficulty of creating a clean way of interacting with it.

We have attempted to minimize the barrier of entry to using LootTweaker.
However, there are a few concepts you’ll need to understand to make the most of it.
You’ll find information about these concepts in the links found in the Valuable Reading section, and in the Tutorials.

Useful Concepts
---------------
This documentation will include examples allow you to make immediate and basic changes to your ModPacks Loot Tables. 
Moving beyond the basics is going to require a more thorough understanding of the systems that drive loot tables in Minecraft, and ZenScript, 
the language that the Tweaker suite runs on. The more you know about these topics, the more effective your use of LootTweaker will be.

* **Zenscript**: ZenScript is a language developed for use with CraftTweaker implemented by all of its add-ons. A basic understanding of ZenScript can be gained on the CraftTweaker documentation page `here <https://docs.blamejared.com/1.12/en/#Getting_Started/>`_. A good place to get some experience using this language is writing `crafting recipes <https://docs.blamejared.com/1.12/en/#Vanilla/Recipes/Crafting/Recipes_Crafting_Table/>`_ with CraftTweaker.
* **Minecraft LootTable Concepts**: The MC Wiki's `entry on loot tables <https://minecraft.gamepedia.com/Loot_table>`_ will help you understand how the system works and give you some idea of the scope of things that are possible to accomplish with it.


Coming Up Next
--------------
In the next section, we’re going to cover some of the basics involved in using LootTweaker. 
This will include an introduction to Object-Oriented Programming Basics, Variables, 
and the breakdown of a LootTweaker script applying these concepts.

Valuable Reading
----------------

* `The basics of variables <http://crafttweaker.readthedocs.io/en/latest/#Vanilla/Variable_Types/Variable_Types/>`_
* `More on Variables <http://minetweaker3.powerofbytes.com/wiki/Tutorial:Basic_Recipes#Using_variables>`_
* :doc:`Various useful LootTweaker tips and tricks <tips-and-tricks>`
* `The MC Wiki Article on Loot Tables <https://minecraft.gamepedia.com/Loot_table>`_
* :doc:`LootTweaker Tutorials <tutorials/tutorial-index>`

Video Tutorials
---------------
If text tutorials aren't your thing, there are 3rd party video tutorials around.
Below are some we've watched and judged to be of good quality.
They don't necessarily cover everything however.

* | `How to make a Minecraft Modpack | Adding and Removing Loot from Entities(mobs) <https://youtu.be/Gam65KJ4RDM?t=479>`_ by IterationFunk
  | Note that the first part of the video covers CraftTweaker's drop functions, LootTweaker content starts at 7:59.
  | As of LootTweaker 0.2.0, some of the methods used in this video are :doc:`deprecated <reference/deprecations>`.
  | If he's writing stuff like ``<entity:minecraft:spider>.removeDrop(<minecraft:string>);`` you're watching the wrong part of the video.
