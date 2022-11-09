.. meta::
   :description lang=en: An overview of Bcome's network configuration file.

.. include:: ../urls.rst

********
Overview 
********

Introduction
============

A Bcome installation is configured through the definition of a networks.yml configuration file, where you - 

* Declare nodes through parent-child relationships
* Declare your nodes' configuration elements, for example, your SSH architecture.

To begin, navigate to your project directory, and initialize your project using: 

.. code-block:: bash

   bcome init

For more information see: :doc:`../getting-started/setting-up-your-project`.

Also understand what the available Bcome nodes are: :doc:`../core-concepts/nodes`.

Configuration
=============

Your network is configured by first defining :doc:`../core-concepts/nodes`, which determine your installation's architecture, followed by configuring your nodes by declaring :doc:`elements`.
