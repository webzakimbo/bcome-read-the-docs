.. meta::
   :description lang=en: Your Bcome installation's architecture will be determined directly by how you lay out your nodes.  Learn about the different node types here.

.. include:: ../urls.rst

*****
Nodes
*****

Introduction
============

A node is an object that represents a resource within Bcome. It can be navigated to using the CLI, or it can be interacted with programmatically.  

Exposed onto any node object - whether reached via CLI navigation, directly through keyed-access, or in custom code from a Registry script -  are the methods provided by the framework (by the menu) and any custom tasks added by you to your Registry (see :doc:`../registry/overview`).

Your installation's architecture - its interface - is determined directly by how you declare your nodes in your networks.yml file. How you do this will determine the application the framework generates for you, and what shared behaviour or configuration is inherited by child nodes.

.. note::

   If you don't have a networks.yml file yet, you will need to initialize your project. See: :doc:`../getting-started/setting-up-your-project`.

Declaring Nodes
===============

Nodes in your networks.yml configuration are declared via YAML (see: :doc:`../network/network-configuration-attributes`) in the following format:

.. code-block:: yaml

  ---
  node_key:
    description: A description of your node
    type:  the node type

Nodes are laid out in a parent - child format, for example:

.. code-block:: yaml

   ---
   grandparent:
     description: "The grandparent"
     type: collection

   grandparent:parent:
     description: "The parent"
     type: collection

   grandparent:parent:child:
     description: "The child"
     type: inventory

Any networking configuration declared in a parent node in the networks.yml configuration will be inherited by any child node, unless expressly overidden in the child. This allows children to inherit networking configuraton from their parent (e.g. a GCP authorisation) but override where appropriate (e.g. a location or region). For more information, see :doc:`../network/network-configuration-attributes`).

Any metadata declared in a parent node will in inherited (i.e. available) to any child node, unless expressly overidden in the metadata for that child. For more information, see :doc:`../metadata/metadata-framework`.

.. note::

   Declared nodes can be of type: ``collection``, ``inventory``, ``inventory-subselect``, ``inventory-merge``, ``aws-k8s-cluster``, or ``gcp-k8s-cluster``


Declared Node Types
===================

The following nodes type can be declared directly in the network config:

Collection
^^^^^^^^^^

Collections may contain any number of other collections and any number of inventories, and is denoted by type 'collection'.

.. code-block:: yaml

  ---
  "my_collection":
    type: collection
    description: My collection    

.. note::

   Your installation must have at least one, and only one ``root`` collection. All other nodes are located below the root.  This collection references your Estate, as it contains within it all other nodes.

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

GKE Cluster
^^^^^^^^^^^

A GKE Kubernetes Cluster, hosted in Google Cloud Platform.

.. code-block:: yaml

   ---
   "foo:bar:production-cluster":
     type: gcp-k8s-cluster
     description: My production cluster
     cluster:
       location: gcp-location 
       name: cluster-name
     network:
       override: attribute
       override: another

AWS Cluster
^^^^^^^^^^^

An EKS Kubernetes cluster hosted in Amazon Web Services.

.. code-block:: yaml

   ---
   "foo:bar:production-cluster":
     type: aws-k8s-cluster
     description: My production cluster
     cluster:
       name: CLUSTER_NAME
       account_id: AWS_ACCOUNT_ID # needed to infer the cluster's arn
   
.. note::

   Inventories, EKS and GKE clusters are dynamic node types.  Whilst they can be placed inside any other ``collection`` nothing can be placed beneath them as their contents are auto-populated.

System Node Types
=================

System node types are automatically populated into specific declared node types: 

Server
^^^^^^

A Server directly represents a server from a cloud provider (determined by your network configuration, see: :doc:`network-configuration-attributes`) , or one from a statically defined manifest (see :doc:`static-manifests`).

Servers are used to populate Inventories.

Kubernetes Node Types
^^^^^^^^^^^^^^^^^^^^^

Many common Kubernetes types are modelled as Bcome nodes:

- Namespace
- Ingress
- Service
- Deployment
- Pod
- Container
- Secret
- Cron Job

and some uncommon ones:

- Istio VirtualService

A abstract Bcome node type -  a Crd, or Custom Resource Definition - is returned for any ad-hoc objects returned that do not have an explicit Bcome Kubernetes node type to assign it.

As for all Bcome nodes, all Kubernetes node types are provided with convenience accessors and are extensible within the framework for custom orchestration tasks.

