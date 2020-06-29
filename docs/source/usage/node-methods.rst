.. meta::
   :description lang=en: Bcome usage: Public instance methods on the @node object

.. include:: ../urls.rst

*************
@node methods
*************

Various public-instance methods are made available on the :doc:`../core-concepts/node` object.

Whilst these are generally useful for debugging in Console sessions, they will enhance your orchestration scripts.  For a full reference, please refer to the source code: |BCOME_SOURCE|_.

A few notable accessors are detailed below:

On all namespaces
=================

Networking accessors
--------------------

The network driver

.. code-block:: bash

   network_driver
   
Its configuration, as a Hash:

.. code-block:: bash

   network_driver.config

The authenticated Cloud credentials for the current namespace, returned as a Hash. For EC2 this will return the namespace's access key and secret key, for GCP it will return an access_token and the project name. This is useful should you wish to extend an authenticated Bcome session into a custom integration.

.. code-block:: bash

   network_driver.network_credentials

The SSH driver, an instance of ``::Bcome::Ssh::Driver``

.. code-block:: bash

   ssh_driver

The ``Net::SSH::Proxy::Jump`` configuration, should the namespace be configured to proxy its connections:

.. code-block:: bash

   ssh_driver.proxy

Server accessors
----------------

All servers present beneath the current namespace, returns an Array of:

.. code-block:: bash

  machines

Metadata accessors
------------------

The metadata object for this namespace (``::Bcome::Node::Meta::Local``):

.. code-block:: bash

  metadata

All metadata for this namespace as a Hash

.. code-block:: bash

  metadata.all

On inventory namespaces
=======================

Return all cloud servers tagged or labelled with a key matching any value in a specified Array"

.. code-block:: bash

   cloud_tags.fetch(:tag_or_label_name, ["match1", "match2", "match3"])

On server namespaces
=====================

The cloud server if @node is an EC2 server (returns an instance of Fog::Compute::AWS::Server):

.. code-block:: bash

   ec2_server

The cloud server if @node is a GCP server (returns an instance of Google::Apis::ComputeBeta::Instance):

.. code-block:: bash

   gcp_server

Return all configured tags/labels if a cloud server:

.. code-block:: bash

   tags_h

.. note::

   @node may also be extended by applying :doc:`../usage/monkey-patches`.