.. meta::
   :description lang=en: Executing commands in Bcome

.. include:: ../urls.rst

******************
Executing Commands
******************

Let's imagine you have :doc:`../core-concepts/nodes` laid out in the following parent-child relationship:

.. code-block:: bash

   .
   └── parent
       └── child
           └── grandchild


Invoking a command when in the console
--------------------------------------

Given command 'foo' available to node parent:child:grandchild, how would you invoke it?

.. code-block:: bash

   > bcome child:grandchild
   > foo

OR

.. code-block:: bash

  > bcome
  > cd child:grandchild
  > foo

OR 

.. code-block:: bash

  > bcome
  > cd child
  > cd grandchild
  > foo

OR, using dot-notation

.. code-block:: bash

  > bcome
  > child.granchild.foo

OR, a dot-notation example passing in parameters, for e.g. ``run``:

.. code-block:: bash

  > bcome
  > child.grandchild.run "ls -al"


.. note::

   When you an enter an IRB session, you are in the scope of an instance of a Ruby object (see: :doc:`../core-concepts/node`).

   Bcome's Console assigns an instance of your node as this session object.

Invoking a command in the console using dot notation
----------------------------------------------------






Invoking commands with Keyed-access
-----------------------------------

To invoke command 'foo' available to node parent:child:grandchild, you would enter the following command in your terminal:

.. code-block:: bash

   > bcome child:grandchild:foo

Invoking commands from orchestration scripts
-------------------------------------------

If you have a node instance, for example :doc:`../core-concepts/node`, then any available command may be invoked directly on it.

For example, given a node in an instance var @node, and a command, :foo, you would:

.. code-block:: bash

   @node.foo

.. hint::

   Any command, be they in-built menu commands (see :doc:`command-menu`), public-methods on a given node object, or a custom-command you've defined yourself in the Registry (see :doc:`../registry/overview`), is accessible in this way.
