.. meta::
   :description lang=en: Bcome usage: Local port forwarding with the tunnel command.

.. include:: ../urls.rst

******
Tunnel
******

As Bcome handles your SSH configuration for you via your :doc:`../core-concepts/network-configuration`, setting up a tunnel to access a remote service - even one behind any number of proxies - becomes simple.

Let's imagine you want to open up access on local port 9200 to an Elastic Search service running remotely on port 9200, and that your :doc:`../core-concepts/namespaces` are setup as follows:

.. code-block:: bash

   .
   └── estate
       └── production
           ├── elastic_data_nodes
           │   ├── data_node_1
           │   ├── data_node_2
           │   └── data_node_3
           └── management
               └── jump_host

From the Console
^^^^^^^^^^^^^^^^

  .. code-block:: bash

   bcome production:elastic_data_nodes:data_node_1
   the_tunnel = tunnel 9200, 9200
   
The tunnel connection is kept open until the Console session is terminated, or until the tunnel is manually closed, as follows:

   .. code-block:: bash

    the_tunnel.close!

.. note:: 

   You may open as many SSH tunnels as you require during a Console session.

Using Keyed Access
^^^^^^^^^^^^^^^^^^

.. code-block:: bash

   bcome production:elastic_data_nodes:data_node_1:tunnel 9200 9200

The tunnel connection is kept open until you Control+C to close the session, or until a SIGINT is received by the Bcome process.

From an orchestration script
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Where :doc:`../core-concepts/node` is an instance of your server namespace:

.. code-block:: ruby

   # Open a tunnel
   tunnel = @node.tunnel(9200, 9200)

   # Close the tunnel
   tunnel.close!

.. note::

  You may open as many SSH tunnels as you require from an Orchestration script.

For more information on orchestration scripts see :doc:`../orchestration/external-ruby-scripting` and :doc:`../orchestration/internal-ruby-scripting`.

