.. meta::
   :description lang=en: Executing commands in Bcome

.. include:: ../urls.rst

******************
Executing Commands
******************

Let's imagine you have :doc:`../core-concepts/namespaces` laid out in the following parent-child relationship:

.. code-block:: bash

   .
   └── parent
       └── child
           └── grandchild


Invoking a command when in the console
--------------------------------------

Given command 'foo' available to namespace parent:child:grandchild, how would you invoke it?

.. code-block:: bash

   > bcome child:grandchild
   > foo

.. note::

   When you an enter an IRB session, you are in the scope of an instance of a Ruby object (see: :doc:`../core-concepts/node`).

   Bcome's Console assigns an instance of your namespace as this session object.


Invoking commands with Keyed-access
-----------------------------------

To invoke command 'foo' available to namespace parent:child:grandchild, you would enter the following command in your terminal:

.. code-block:: bash

   > bcome child:grandchild:foo

Invoking commands from orchestration scripts
-------------------------------------------

If you have a namespace instance, for example :doc:`../core-concepts/node`, then any available command may be invoked directly on it.

For example, given a namespace in an instance var @node, and a command, :foo, you would:

.. code-block:: bash

   @node.foo

.. hint::

   Any command, be they in-built menu commands (see :doc:`command-menu`), public-methods on a given namespace object, or a custom-command you've defined yourself in the Registry (see :doc:`../registry/overview`), is accessible in this way.
