.. meta::
   :description lang=en: Bcome orchestration: Basic bash scripting in Bcome.

.. include:: ../urls.rst

**************
Bash scripting
**************

You may execute a local bash script against servers in your collection using the ``execute_script`` command.

Let's image you have the following :doc:`../core-concepts/nodes` setup:

.. code-block:: bash

   .
   └── project
       ├── inventory_one
       │   ├── server_a
       │   ├── server_b
       │   └── server_c
       └── inventory_two
           ├── server_d
           ├── server_e
           └── server_f

And the following bash script, saved to your local system at /path/to/script.sh:

.. code-block:: bash

   #!/bin/bash

   echo "hello world"

   exit 0


In order to execute the script against a single server, for example 'server_a' in 'inventory_one', you would invoke the following:

.. code-block:: bash

   bcome inventory_one:server_a:execute_script /path/to/script.sh

To execute the script against all servers in 'inventory_two', you would:

.. code-block:: bash

   bcome inventory_two:execute_script /path/to/script.sh

Likewise, for all servers in your project:

.. code-block:: bash

   bcome execute_script /path/to/script.sh

.. note::

   The examples above illustrate how bash scripts may run using Keyed Access (see: :doc:`../usage/navigation`).

.. hint::

   The Console allows for greater flexibility in working with selections of nodes. See 'Selection Commands' in :doc:`../usage/command-menu`.
