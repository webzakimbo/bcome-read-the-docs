.. meta::
   :description lang=en: Bcome usage: testing SSH connection with Ping.

.. include:: ../urls.rst

****
Ping
****

Overview
--------

SSH Connections may be tested with Bcome's ``ping`` command.

For each server in scope the connection will be tested and a status (containing the server's connection configuration) returned.

The returned status will look like this:

.. code-block:: bash

   "your_estate:an_inventory:some_server" => {
     "connection" => "success",
     "ssh_config" => {
         :user    => "guillaume",
         :timeout => 1,
         :proxy   => [
           [0] {
             :host_lookup => "by_bcome_namespace",
             :namespace   => "your_inventory:a_jump_host",
             :proxy_host  => "12.345.678.90",
             :user        => "guillaume"
           }
         ]
       }
     }
   }


.. note::

   Failed connections will be coloured red, and successful ones green.  Each is marked with a connection status of "failed" or "success" respectively.

Usage
-----

Let's imagine you have :doc:`../core-concepts/namespaces` laid out in the following parent-child relationship:

.. code-block:: bash

   .
   └── parent
       └── child1
       └── child2

And let's assume that 'child1' and 'child2' are inventories containing servers.

Ping all the servers within your Estate
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: bash

   bcome ping

Ping all the servers within a given inventory
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: bash

   bcome child1:ping

Ping an individual server within a given inventory
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


.. code-block:: bash

   bcome child2:your_server:ping

Ping from the Bcome Console
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: bash

   bcome child1
   ping


.. note::

   Bcome caches all SSH connections, with the exception of those made during a Ping.
