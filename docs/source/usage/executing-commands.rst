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


Now let's say you want to invoke a command on the `grandchild` node. This command may be available from the standard menu for this node type, it may be a method available from the Ruby language (each node being a Ruby object at its core), or your method may be a custom task you've added to your Bcome Registry (See :doc:`../registry/overview`) and associated with the `grandchild` node.  

What are the options for invoking this command?

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

OR, a dot-notation example passing in parameters:

.. code-block:: bash

  > bcome
  > child.grandchild.run "parameter"

.. hint::

   When you a enter a Bcome session you are in the scope of an instance of a Ruby object (see: :doc:`../core-concepts/node`), representing the current node.

   Each node within your Bcome instance will be represented by a different Ruby object.

Invoking commands with Keyed-access
-----------------------------------

To invoke command 'foo' available to node parent:child:grandchild, you would enter the following command in your terminal:

.. code-block:: bash

   > bcome child:grandchild:foo

OR, to pass in parameters

.. code-block:: bash

  > bcome child:grandchild:run "/some/command parameter"

Invoking commands from orchestration scripts
-------------------------------------------

An orchestration script is just a Ruby script configured to be attached, and executed in the context, of a specific Bcome node.

If you have a node instance, for example :doc:`../core-concepts/node`, then any available command may be invoked directly on it.

For example, given a node in an instance var @node, and a command, :foo, you would:

.. code-block:: bash

   @node.foo

.. hint::

   Any command, be they in-built menu commands (see :doc:`command-menu`), public-methods on a given node object, or a custom-command you've defined yourself in the Registry (see :doc:`../registry/overview`), is accessible in this way.

For more information on writing orchestration scripts see :doc:`../orchestration/external-ruby-scripting` and :doc:`../orchestration/internal-ruby-scripting`.

For information on how to integrate custom scripts into your installation, see :doc:`../registry/overview`




