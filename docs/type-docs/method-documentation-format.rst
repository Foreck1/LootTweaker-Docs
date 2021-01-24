:orphan:

.. |2^31| replace:: 2\ :sup:`31`\

Method Documentation Format
===========================

Methods on the documentation pages follow the following format

Specification
-------------
| ``<modifiers>? <return_type> <name>(<parameters>?)``
| <modifiers> = static
| <return_type> = <a ZenScript type> | void
| <name> = <a valid ZenScript variable name>
| <parameters> = <parameter>, ...
| <parameter> = @Optional? <param_type> <param_name>
| <param_type> = <a ZenScript type>
| <param_name> = <a valid ZenScript variable name>

Where an ? means the element is not included in all examples.

Explanation
-----------
| The format has modifiers, then the return type, the method name, and the arguments in parentheses.
| The only valid modifier is ``static``, which means the method is a :doc:`static method </tutorials/crash-course-basics>`.
  No modifiers means the method is an instance method.
| The return type is either the name of a ZenScript type, which means the method returns an instance of that type; or it is the keyword ``void``, which means the method returns nothing.
| The name is a valid ZenScript variable name.
| A method has zero or more parameters, which are enclosed in parentheses and separated by commas.
| A parameter consists of a ZenScript type name followed by the name of the parameter, which is a valid ZenScript variable name. If it is preceded by ``@Optional`` it is an optional parameter, so you do not have to specify it when calling the method. Optional parameters always come last in the parameter list.


Common Types
--------------
========== =================================================================================================== ============================================================================
Type Name  Description                                  Examples
========== =================================================================================================== ============================================================================
IItemStack An item stack with metadata, size & NBT data.                                                       | ``<minecraft:apple>``
           `More info <https://crafttweaker.readthedocs.io/en/latest/#Vanilla/Items/IItemStack/#iitemstack>`__  | ``<minecraft:potato> * 3``
                                                                                                               | ``<minecraft:dye:3>``

DataMap    A representation of map-like formats,                                                               | ``{"function": "minecraft:set_count", "count": {"min": 1.0, "max": 3.0}}``
           such as JSON and NBT.                                                                               | ``{"condition": "killed_by_player"}``
           `More info <https://docs.blamejared.com/1.12/en/Vanilla/Data/DataMap/#datamap>`__

String     A sequence of characters.                                                                           | ``"Alice"``
                                                                                                               | ``"cat@example.com"``
                                                                                                               | ``"123ABCxyz789"``

int        A whole number from -|2^31| to |2^31| - 1.                                                          | ``1``
                                                                                                               | ``-52``

float      A floating point number from -|2^31| to |2^31| - 1.                                                 | ``3.141``
                                                                                                               | ``-2.05``
========== =================================================================================================== ============================================================================

Array Types
-----------
Arrays hold multiple objects of the same type. An array type name is the name of the type it holds followed by '[]', so the type name of an array of Strings would be 'String[]'.
Arrays are created by surrounding the elements in square brackets and separating them with commas, like so::

    ["Alice", "Bob", "Charlie"]
    [1, 2, 3, 4, 5]

More info `here <https://crafttweaker.readthedocs.io/en/latest/#AdvancedFunctions/Arrays_and_Loops/#arrays>`__.

Optional arguments
------------------
If an argument has @Optional before it (e.g @Optional String name), it's optional. If you do not specify a value, LootTweaker will generate one.
For example, ``LootPool#addItemEntry(IItemStack stack, int weightIn, @Optional String name)`` can be called in 2 ways::

    pool.addItemEntry(<minecraft:apple>, 5, "not_an_orange");

or ::

    pool.addItemEntry(<minecraft:apple>, 5);

The second call will make LootTweaker pick an appropriate value for the ``name`` parameter.
