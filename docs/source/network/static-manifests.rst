.. meta::
   :description lang=en: Bcome static manifests on-site on-premise infrastructure hybrid cloud

****************
Static manifests
****************

Overview
========

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
     cloud_tags:
       data:
         a_key: a_value
         another_key: another_value
   - identifier: some_other_server
     public_ip_address: 678.678.678.67
     internal_ip_address: 10.2.23.12
     description: My other server

Attribute List
==============

Below are the attribuites required in order to define a static server.

+-----------------------------+-----------------------------+----- ----------------+--------------------------------------------------------------------------------+
|                             |                             |                      |                                                                                |
|   attribute key             |  description                |  optional            |   notes                                                                        |
+=============================+=============================+======================+================================================================================+
|  identifier		      |  The server name.           |  No	           |  Bcome will automatically swap whitespace for underscores, and auto-increment  |
|			      |		                    |			   |  duplicate identifiers. 		 					    |	
|			      |  How this server is         | 			   |										    |
|			      |  identified.                |			   |										    |
+-----------------------------+-----------------------------+----------------------+--------------------------------------------------------------------------------+
|  description                |  The server description     |  No		   |  A description of the server.  This will appear in Bcome's UI.		    |
|			      |				    |			   |										    |
+-----------------------------+-----------------------------+----------------------+--------------------------------------------------------------------------------+
|  public_ip_address          |  The public interface IP    |  Yes		   |  You may use a hostname here also.						    |  
|			      |  address.     	            |                      |										    |
+-----------------------------+-----------------------------+----------------------+--------------------------------------------------------------------------------+
|  internal_ip_address	      |  The internal interface IP  |  Yes		   |  You may use a hostname here also.				                    |
|			      |  address.		    |  		           |										    |
+-----------------------------+-----------------------------+----------------------+--------------------------------------------------------------------------------+
|  cloud_tags                 |  A Hash of tags keys and    |  Yes		   |  See :ref:`TAG_ATTRS` for structure					    |
|			      |  values, keyed on :data     | 			   |										    |
+-----------------------------+-----------------------------+----------------------+--------------------------------------------------------------------------------+

.. _TAG_ATTRS:

Tag attributes
^^^^^^^^^^^^^^

Cloud tag attributes have the following YAML structure:

.. code-block:: yaml

  ---
  cloud_tags:
    data:
      tag_key_1: tag_value_1
      tag_key_2: tag_value_2
