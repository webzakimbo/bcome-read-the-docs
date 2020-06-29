.. meta::
   :description lang=en: Bcome Namespaces

.. include:: ../urls.rst

**********
Namespaces
**********

Your installation's architecture will be determined directly by how you lay out your namespaces, which should be a direct representation of how you wish to visualize and manage your platforms, environments, applications etc.

The sum-total of all your namespaces is referred to within Bcome as your :doc:`../core-concepts/estate`.

Namespaces are declared via YAML (see: :doc:`../network/network-configuration-attributes`) in the following format:

.. code-block:: yaml

  ---
  namespace_key:
    description: "A description of your namespace"
    type:  the namespace type

Namespaces are laid out in a parent - child format, for example:

.. code-block:: yaml

   ```
   grandparent:
     description: "The grandparent"
     type: collection

   grandparent:parent:
     description: "The parent"
     type: collection

   grandparent:parent:child:
     description: "The child"
     type: inventory

.. note::

   Namespaces can be of type: ``collection``, ``inventory``, ``inventory-subselect`` or ``inventory-merge``


Namespace Types
===============

Collection
^^^^^^^^^^

Collections may contain any number of other collections and any number of inventories, and is denoted by type 'collection'.

.. code-block:: yaml

  ---
  "my_collection":
    type: collection
    description: My collection    

.. note::

   Your installation must have at least one, and only one ``root`` collection. All other namespaces are located below the root.  This collection references your Estate, as it contains within it all other namespaces.

Inventory
^^^^^^^^^

An inventory contains servers, either populated from a particular cloud account or from a statically defined manifest.  It is denoted by type 'inventory'.

.. code-block:: yaml

  ---
  "my_inventory":
    type: inventory
    description: My inventory

Sub-selected Inventory
^^^^^^^^^^^^^^^^^^^^^^

A Sub-selected Inventory contains servers that have been populated as a result of applying filters to an Inventory. It is denoted by type 'inventory-subselect'.

It requires an origin Inventory referenced by the ``subselect_from``) attribute upon which the subselect is actioned, in addition to a filter block.

.. code-block:: yaml

  ---
  "root_collection":
    type: collection
    description: My root collection

  "root_collection:my_inventory":
    type: inventory
    description: My Inventory

  "root_collection:my_sub_selected_inventory":
    type: inventory_subselect
    description: My Sub-selected Inventory
    subselect_from: my_inventory
    filters: ...

Note that the 'subselect_from' key denotes a breadcrumb to the subselected from inventory (minus the root collection). For example, consider the following:

.. code-block:: yaml

   ---
   "estate":
     type: collection
     description: Root collection

   "estate:platform":
     type: collection
     description: Platform collection

   "estate:platform:production":
     type: collection
     description: Production environment
   
   "estate:platform:production:servers":
     type: inventory
     description: All my servers


You could create a sub-selection from the 'servers' Inventory as follows:

.. code-block:: yaml

   ---
   "estate:platform:production:app_servers":
     type: inventory-subselect
     description: My application servers for platform production
     subselect_from: platform:production:servers
     sub_filter: {} 

The root collection key in the sub-select_from attribute - in this instance 'estate' - is implicit.
    
.. note:: 

   See: :doc:`../network/network-configuration-attributes` for sub_filter options.


Merged Inventory
^^^^^^^^^^^^^^^^

A merged inventory is the result of a union of two or more Inventories and/or Sub-selected inventories. It is denoted by type 'inventory-merge'.

It requires contributing Inventories and/or contributing Sub-Selected-inventories to be specified using the 'contributors' attribute. For example:

.. code-block:: yaml

   ---
   "merged:frontend":
     type: inventory-merge
     description: Production and Development frontend servers
     contributors:
     - production:frontend
     - development:frontend

.. hint::
 
   Use Merged Inventories to create 'Multi-cloud' and/or 'Hybrid-cloud' views.

   A Merged Inventory may have contributors from the same or different networks within the same Cloud, different Clouds, or from statically declared manifests.

Server
^^^^^^

A Server directly represents a server from a Cloud provider, or one from a the statically defined manifest. 

With the exception of :doc:`static-manifests`, servers are not declared, rather they are populated into Inventories from by your Network configuration (see: :doc:`network-configuration-attributes`).
