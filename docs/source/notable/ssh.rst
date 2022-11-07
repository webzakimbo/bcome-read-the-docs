.. meta::
   :description lang=en: Bcome usage: Initiating an SSH terminal connection to a server.

.. include:: ../urls.rst

***************
SSH to a server
***************

You may SSH to a server either using Keyed-Access, or directly from the Bcome console (see: :doc:`../usage/navigation`).

Let's imagine you have :doc:`../core-concepts/nodes` laid out in the following parent-child relationship:

.. code-block:: bash

   .
   └── parent
       └── child
           └── server

SSH with Keyed Access
^^^^^^^^^^^^^^^^^^^^^

.. code-block:: bash

   bcome child:server:ssh

From the Console
^^^^^^^^^^^^^^^^

From the child inventory node:

.. code-block:: bash

   bcome child
   ssh server


From the server node:

.. code-block:: bash

   bcome child
   cd server
   ssh


.. hint::

  Use the 'tree' function or invoke 'ls' on any node to see which child nodes are available beneath it. See: :doc:`../usage/command-menu`.
