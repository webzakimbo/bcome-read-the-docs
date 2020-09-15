.. meta::
   :description lang=en: Bcome usage: Navigation using the Command Line Interface (CLI) or from your terminal using Keyed-Access.

.. include:: ../urls.rst

**********
Navigation
**********

Bcome is used by navigating to a namespace, and invoking the method of your choice.  

That method may either be a built-in function (see: :doc:`command-menu`), or a custom function you've added yourself as part of your installation, and available via the Registry (see :doc:`../registry/overview`).

You may either traverse your namespaces via :ref:`THE_CONSOLE` before invoking your method, or you may invoke it directly from your terminal using :ref:`KEYED_ACCESS`.

Let's imagine you have :doc:`../core-concepts/namespaces` laid out in the following parent-child relationship:

.. code-block:: bash

   .
   └── parent
       └── child
           └── grandchild

.. _THE_CONSOLE:

The Console
-----------

Bcome exposes a REPL (read-eval-print loop) shell, built on top of Ruby's IRB (interactive Ruby) shell.

Each namespace is loaded into a distinct shell session, which you may then interact with directly.

Basic navigation
^^^^^^^^^^^^^^^^

Enter the Console at the root namespace:

.. code-block:: bash

   > bcome


List your namespaces:

.. code-block:: bash

   > ls

Traverse to the 'child' namespace, and onward to 'grandchild':

.. code-block:: bash

  > cd child
  > cd grandchild


Go back up a level:

.. code-block:: bash

  > back 

Exit back to you terminal:

.. code-block:: bash

  > exit!

.. hint::

   For a full list of in-built commands see :doc:`menu`. 

   For accessing your custom commands, see the Registry (:doc:`../registry/overview`).

.. _KEYED_ACCESS:

Keyed-Access
------------

Bcome provides a shortcut to any namespace, referred to as Keyed-Access, where the namespace breadcrumb is included as a parameter to ``bcome``.

Enter the Console using Keyed-Access.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To enter the CLI directly at our 'grandchild' namespace, you would enter the following command:

.. code-block:: bash

  > bcome child:grandchild

This allows you to start a Console session directly at the namespace you require, without having to traverse your tree.

.. hint::

   Invoking 'ls' on any namespace will list its direct children, whilst invoking 'tree' on any namespace will list the Bcome tree structure beneath. 

See :doc:`executing-commands` for how to execute commands in Keyed-access or Console mode.
