.. meta::
   :description lang=en: The Bcome network configuration file - element inheritance and overrides. networks.yml

.. include:: ../urls.rst

***********************
Inheritance & overrides
***********************

Network and Ssh Configuration (see :doc:`network-configuration-attributes`) are inherited by all of a namespace's children, at which point they may be overidden to customise the attributes at that namespace level. 

For example:

.. code-block:: yaml

  ---
  "estate":
    type: collection
    description: My Estate
    network:
      foo: value
      bar: other value

  "parent:child": 
    type: inventory
    description My Inventory

The 'child' element's network attributes looks as follows:

.. code-block:: yaml

   --
   network:
     foo: value
     bar: other value

Then consider:

.. code-block:: yaml

  ---
  "estate":
    type: collection
    description: My Estate
    network:
      foo: value
      bar: other value

  "parent:child":
    type: inventory
    description My Inventory
    network:
      bar: overriden value

The child element's network Element has been partially overriden resulting in the following:

.. code-block:: yaml

   --
   network:
     foo: value
     bar: overriden value
