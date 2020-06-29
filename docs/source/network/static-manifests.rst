.. meta::
   :description lang=en: Bcome static manifests on-site on-premise infrastructure hybrid cloud

****************
Static manifests
****************

If you have infrastructure on-site, or in any other provider for which Bcome does not yet provide a driver, you may utilise a Static Manifest.

A Static Manifest is a list of manually configured servers that can be used to populate a specified Inventory.

For example, consider the following simple Network configuration:

.. code-block:: yaml

   ---
   estate:
     type: collection
     description: My Collection

   estate:onsite:
     type: inventory
     description: My onsite inventory


Above we have defined a Collection housing a single Inventory (see :doc:`../core-concepts/namespaces`).  There is no Network defined (see: :doc:`network-configuration-attributes`), and therefore no configured cloud provider to populate the Inventory.

Now create a file called ``static-cache.yml`` and save it to your Bcome configuration directory as follows:

.. code-block:: bash

   .
   ├── Gemfile
   └── bcome
       └── networks.yml
       └── static-cache.yml

Here's a simple example of a Static Manifest entry within our static-cache.yml file that would populate our Inventory with two servers:

.. code-block:: yaml

   ---
   estate:onsite:
   - identifier: file_server_one
     public_ip_address: 123.123.123.12
     description: My server
   - identifier: some_other_server
     public_ip_address: 678.678.678.67
     description: My other server

