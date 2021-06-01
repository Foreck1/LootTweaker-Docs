:orphan:

.. |2^31| replace:: 2\ :sup:`31`\

Documentation Format
====================

Method Format
+++++++++++++
Static Method  

.. code-block:: java

    static ReturnType methodName(Parameter1Type parameter1, Parameter2Type parameter2)

Instance Method

.. code-block:: java

    ReturnType methodName(Parameter1Type parameter1, Parameter2Type parameter2)


``ReturnType`` is either the name of a ZenScript type, which means the method 
returns an instance of that type; or it is the keyword ``void``, 
which means the method returns nothing.
``methodName`` is the name to use when calling the method. There may be multiple 
methods with the same name, but different parameters.
After the method name is the parameter list, which is enclosed in (). There 
may be any number of parameters, including none.
Each parameter has a type and a name. The parameter type is the type of data to 
pass as that parameter when calling the method.

Remember that static methods are called on their type, i.e. ``Foo.staticMethod()``;
but instance methods are called on an instance of their type, i.e. ``someFoo.instanceMethod()``

Common Types
++++++++++++
========== =================================================================================================== ============================================================================
Type Name  Description                                                                                         Examples
========== =================================================================================================== ============================================================================
IItemStack An item stack with metadata, size & NBT data.                                                       | ``<minecraft:apple>``
           `More info <https://crafttweaker.readthedocs.io/en/latest/#Vanilla/Items/IItemStack/#iitemstack>`__ | ``<minecraft:potato> * 3``
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
