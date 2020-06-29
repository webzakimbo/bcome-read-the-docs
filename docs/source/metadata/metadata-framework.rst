.. meta::
   :description lang=en: The metadata framework

The Metadata Framework
======================

When scripting or otherwise interacting with the Bcome Console, the framework will let you access used-defined metadata.  

This is useful when writing orchestration scripts.

As with all other Bcome configuration, Metadata is configured using YAML, and may be encrypted (see :doc:`metadata-encryption`).

Metadata YAML
-------------

To enable metadata you'll need a 'metadata' directory under your 'bcome' configuration directory, as follows:

.. code-block:: bash

   .
   └── project
       └── bcome
           └── metadata

Any .yml file you place in this directory will be loaded into the framework.

Your Metadata is then defined by declaring attributes onto a namespace breadcrumb.

For example, given a namespace with a breadcrumb of "foo:bar", to assign it Metadata, you would create a .yml file within your 'metadata' directory with the following contents:

.. code-block:: yaml

   ---
   foo:bar:
     key: value
     other_key: other_value  

Metadata Inheritance
--------------------

Metadata is inherited within child namespaces, where it may be overidden.

For example, given two namespace "parent" and "parent:child", with the following Metadata YAML defined:

.. code-block:: yaml

   ---
   parent:
     key: value
     other_key: other_value

   parent:child:
     key: overidden_value


The "parent:child" namespace overrides, i.e. re-defines, the 'key' attribute, whilst inheriting 'other_key'.  Its Metadata looks like this:

.. code-block:: yaml

   ---
   key: overidden_value
   other_key: other_value


Accessing Metadata
------------------

See :doc:`metadata-commands` for accessing metadata.
