.. include:: ../urls.rst

.. meta::
   :description lang=en: Core Bcome concepts - your Estate

*******
Estate
*******

The sum-total of all your defined Bcome namespaces is referred to as your ``Estate``.

You may construct your estate as follows:

Single network
--------------

A single network from a given cloud provider e.g. a Production environment in AWS.

This is the most basic setup.


Multi-network
-------------

Any number of networks from a given cloud provider e.g. multiple pipeline environments in a single cloud provider that you wish to manage.

This is a typical setup where multiple development & production environments are in play.

Multi-cloud
-----------

Any combination of networks/projects from multiple clouds e.g. a Production environment environment in one cloud, and perhaps a fallback used as part of a disaster recovery system in another.

Static
------

On-premise infrastructure, or integrations of providers for which Bcome does not yet have a dedicated driver where your inventories are not dynamically retrieved - rather they are statically defined.  

Hybrid Cloud
------------

Any combination of the above e.g. on-premise infrastructure that you wish to orchestrate alongside cloud-based application environments.


.. note::

   Bcome will allow you to merge all your infrastructure into one installation, such that you may orchestrate across your different clouds & networks at the same time.
