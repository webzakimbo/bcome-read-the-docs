.. include:: ../urls.rst

.. meta::
   :description lang=en: Create your Bcome project structure

***************
Getting Started
***************

Create your project structure
=============================

Create a project directory:

.. code-block:: bash

   mkdir project
   cd project
   
Install the bcome gem, manually:

.. code-block:: bash

   gem install bcome

Or, via a Gemfile:

.. code-block:: bash

   source 'https://rubygems.org'
   gem 'bcome'

Which you can then install via bundle:

.. code-block:: bash

   bundle install

Now run the initializer to create your configuration files & directories:

.. code-block:: bash

  init-bcome

Your project directory should now look as follows:

.. code-block:: bash

  .
  ├── .aws
  ├── .gauth
  ├── Gemfile
  └── bcome
      ├── metadata
      ├── networks.yml
      ├── orchestration
      └── registry.yml


Define your namespaces
======================

Once you've created your project structure the next step is to populate your networks.yml configuration file with your namespace structure.

See :doc:`../core-concepts/network-configuration` and :doc:`../core-concepts/namespaces` for further information.


Configure your cloud authorizations
===================================

To populate your installation with servers from a cloud provider you will need to add an authorization.  

An authorization may be associated with more than one namespace, whilst you may add as many authorizations as you like to your installation.  

When you interact with a Bcome namespace configured for an authorisation, the framework will authenticate you against the cloud provider in question so that it may perform a List (and Filter) action to retrieve a server list, which it will then use to populate your Inventory.

To add an AWS authorization. See: :doc:`prepare-aws-access`.

To add a GCP authorization. See: :doc:`prepare-gcp-access`.

.. note::

   When manually specifying servers you will not need to create an authorisation. See doc:`../network/static-manifests` for further information.


Add you authorisation to your namespaces
========================================

Having added cloud authorisations you will likely want to configure them within your namespaces. This is done by adding to your networks.yml configuration file.

For a full list of networks.yml attributes and their usage see :doc:`../network/network-configuration-attributes`.

Our |GUIDES|_ site is also a useful resource, as it includes example configuration.


Setup your SSH pathways
=======================

:doc:`../core-concepts/ssh` is core to Bcome.

If your server instances are not directly accessible you will need to configure your SSH pathways so that Bcome knows how to navigate the proxies you have in place.

This is done by adding to your networks.yml configuration file.

For configuration details, please refer to the |SSH_SETTINGS_ATTRS|_ documentation.  The |GUIDES|_ also have example configuration.


The Registry & Orchestration
============================

The in-built Registry framework is what makes Bcome your DevOps Console. 

It will allow you to associate and re-use custom tasks - i.e. custom orchestration - with your namespaces.

See :doc:`../registry/overview` and :doc:`../registry/registry-examples` for more information. The |GUIDES|_ also have example configuration.

