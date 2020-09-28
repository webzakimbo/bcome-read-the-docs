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


Define your namespaces
======================

Once you've created your project structure the next step is to populate your networks.yml configuration file with your namespace structure.

See :doc:`../core-concepts/network-configuration` and :doc:`../core-concepts/namespaces` for further information.


Configure your cloud authorizations
===================================

To populate your installation with servers from a cloud provider you will need to add an authorization.  

An authorization may be associated with more than one namespace, whilst you may add as many different authorizations as you like to your installation.  

When you interact with a Bcome namespace configured for an authorisation, the framework will authenticate you against the cloud provider in question so that it may retrieve a server list, which it will then use to populate your Inventory.

To add an AWS authorization. See: :doc:`prepare-aws-access`.

To add a GCP authorization. See: :doc:`prepare-gcp-access`.

.. note::

   When manually specifying servers you will not need to create an authorisation. See :doc:`../network/static-manifests` for further information.


Add your cloud authorisation to your namespaces
===============================================

Having added cloud authorisations you will likely want to configure them within your namespaces. This is done by adding to your networks.yml configuration file.

For a full list of networks.yml attributes and their usage see :doc:`../network/network-configuration-attributes`.

Our |GUIDES|_ site is also a useful resource, as it includes example configuration.


Setup your SSH pathways
=======================

:doc:`../core-concepts/ssh` is core to Bcome.

If your server instances are not directly accessible you will need to configure your SSH pathways so that Bcome knows how to navigate the proxies you have in place.

This is done by adding to your networks.yml configuration file.

For configuration details, please refer to the |SSH_SETTINGS_ATTRS|_ documentation.  Our |GUIDES|_ site also has example configuration.


The Registry & Orchestration
============================

The in-built Registry framework is what makes Bcome your DevOps Console. 

It will allow you to associate and re-use custom tasks - i.e. custom orchestration - with your namespaces.

See :doc:`../registry/overview` and :doc:`../registry/registry-examples` for more information. Our |GUIDES|_ site also has example configuration.

