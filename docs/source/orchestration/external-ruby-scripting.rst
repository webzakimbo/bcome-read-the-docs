.. meta::
   :description lang=en: Bcome orchestration: How to write standalone - "external" - scripts, that make use of your Bcome installation. 

.. include:: ../urls.rst

****************
External Scripts
****************

Overview
--------

Ruby scripts that run outside the context of your installation are referred to as *external* scripts.  These may be run standalone, or integrated into your installation with an external method hook (see: :doc:`../registry/registry-examples`).

The most basic example of an external script can be seen below:

.. code-block:: bash

   require 'bcome'

   # Define an orchestrator
   orchestrator = ::Bcome::Orchestrator.instance

   # Load in a node
   node = orchestrator.get("some:node:breadcrumb")   

   # Work with your node
   ...

All nodes retrieved by the orchestrator are instances of :doc:`../core-concepts/node`.

.. note::

  To return the root node using the orchestrator, pass a null breadcrumb i.e. ``orchestrator.get()`` 

See :doc:`../usage/executing-commands` for invoking commands and :doc:`../usage/command-menu` for a list of commands.

See also :doc:`../usage/node-methods` for a list of public instance methods.

.. hint::

   Any command available to you in the Console, using Keyed-Access or via the Registry is available to you within your Ruby scripts.

.. include:: additional-scripting-functions.rst
