.. meta::
   :description lang=en: Metadata framework commands

Metadata Commands
=================

To return a list of all configured metadata:

.. code-block:: bash

   meta # @node.meta

To return a Hash of all configured metadata:

.. code-block:: bash

   metadata.all  # or @node.metadata...

To fetch a specific metadata value by key

.. code-block:: bash

   metadata.fetch(:key) # or @node.metadata...

To fetch a specific metadata value by key, providing a default value should the key not be found:

.. code-block:: bash

   metadata.fetch(:key, { key: "default value }) # or @node.metadata...

To return an Array of all configured metadata keys:

.. code-block:: bash

   metadata.keys # or @node.keys 
