.. meta::
   :description lang=en: Monkey Patching Bcome is easy 

.. include:: ../urls.rst

**************
Monkey Patches
**************

The Bcome framework may be extended by applying a |MONKEY_PATCH|_.

To create a patch ensure you have a 'patches' directory, as follows:

.. code-block:: bash

   .
   └── project_directory
       └── bcome
           └── patches

Any Ruby file placed into 'patches' with a .rb extension will be loaded into the framework.

As an example, to add a method named 'foo' that returns 'bar' onto a GCP server, create a file called my_patch.rb and place it into the patches directory:

.. code-block:: bash

   .
   └── project
       └── bcome
           └── patches
               └── my_patch.rb


Within it add the following code:

.. code-block:: ruby

   class Bcome::Node::Server::Dynamic::Gcp
     def foo
       puts "bar"
     end
   end

All GCP server instances would now be patched with the new 'foo' method.

See here for Bcome's |BCOME_SOURCE|_.
