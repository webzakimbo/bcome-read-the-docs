.. meta::
   :description lang=en: Bcome orchestration: internal ruby scripting extending Bcome

.. include:: ../urls.rst

****************
Internal Scripts
****************

Ruby scripts that run inside the context of your installation are referred to as *internal* scripts, and are loaded as extensions to the framework.

Internal scripts are always invoked in the context of a namespace and can be configured to accept arguments (for integration, see :doc:`../registry/overview`).

Getting started
---------------

Ensure that you have an 'orchestration' directory within your project's 'bcome' directory, as follows:

.. code-block:: bash

   .
   └── project
       └── bcome
           └── orchestration


Any Ruby files placed in the 'orchestration' directory will be loaded into the project.

A basic orchestration script
----------------------------

All internal scripts are ruby classes that inherit from ``Bcome::Orchestration::Base`` and have a public method named ``execute`` that takes no parameters.

.. code-block:: bash

  module ::Bcome::Orchestration
    class MyinternalScript < Bcome::Orchestration::Base

      def execute
         # @node = the namespace context
         # @arguments = An argument Hash
      end

    end
  end

The namespace context in which the internal script was called is available to you in the form of an instance variable named :doc:`../core-concepts/node`.

See :doc:`../usage/executing-commands` for invoking commands and :doc:`../usage/command-menu` for a list of commands.

If arguments have been provided, they are available as a Hash from an instance variable named ``@arguments``.

Invoking internal scripts from within another
---------------------------------------------

You can trigger an orchestration klass from within another (or in any context within Bcome).

Here's how:

.. code-block:: bash

   script = ::Bcome::Orchestration::MyOtherClass.new(node, arguments)
   script.do_execute

Where node is an instance of a namespace.  

Traversing namespaces
---------------------

An internal script is not restricted to the namespace context in which it is called - you may traverse contexts if you know the namespace breadcrumb.

For example, given a namespace referenced by 'my:other:inventory', you may load it as follows:

.. code-block:: bash

   orchestrator = ::Bcome::Orchestrator.instance
   node = orchestrator.get("my:other:inventory")

Note that the parent root namespace key is implicit.

.. include:: additional-scripting-functions.rst

