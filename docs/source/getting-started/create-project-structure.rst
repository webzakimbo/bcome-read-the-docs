.. include:: ../urls.rst

.. meta::
   :description lang=en: Create your Bcome project structure

***************
Getting Started
***************

Setting up your project
=======================

You will need to install and initialize Bcome.  

See here for how: :doc:`setting-up-your-project`


Define your nodes
======================

Once you've created your project structure the next step is to populate your networks.yml configuration file with your node structure.

See :doc:`../core-concepts/network-configuration` and :doc:`../core-concepts/nodes` for further information.


Configure your cloud authorizations
===================================

To populate your installation with servers or load in a Kubernetes cluster you will need to add an authorization.  

An authorization may be associated with more than one node, and you may add as many different authorizations as you like to your installation, adding as many different AWS or GCP accounts to your project as yyou like.  

When you interact with a Bcome node configured for an authorisation, the framework will authenticate you against the cloud provider in question so that it may retrieve resources.

To add an AWS authorization. See: :doc:`prepare-aws-access`.

To add a GCP authorization. See: :doc:`prepare-gcp-access`.

.. note::

   When manually specifying servers you will not need to create an authorisation. See :doc:`../network/static-manifests` for further information.


Add your cloud authorisation to your nodes
===============================================

Having added cloud authorisations you will likely want to configure them within your nodes. This is done by adding to your networks.yml configuration file.

For a full list of networks.yml attributes and their usage see :doc:`../network/network-configuration-attributes`.

Our |GUIDES|_ site is also a useful resource, as it includes example configuration.


Setup your SSH pathways
=======================

If you're not solely interacting with containers, then configuring :doc:`../core-concepts/ssh` is core to Bcome.

If your server instances are not directly accessible you will need to configure your SSH pathways so that Bcome knows how to navigate the proxies you have in place.  Your SSH pathways will instruct Bcome as to how to proxy its connections allowing it to access your servers.

This is done by adding to your networks.yml configuration file.

For configuration details, please refer to the |SSH_SETTINGS_ATTRS|_ documentation.  Our |GUIDES|_ site also has example configuration.


The Registry & Orchestration
============================

The in-built Registry framework lets you add re-usable orchestration onto your nodes.

It will allow you to define and re-use custom orchestration tasks that can be used to interact with the nodes - your servers, clusters, containers, or ad-hoc kubernetes resources -  in your installation.

See :doc:`../registry/overview` and :doc:`../registry/registry-examples` for more information. Our |GUIDES|_ site also has example configuration.

