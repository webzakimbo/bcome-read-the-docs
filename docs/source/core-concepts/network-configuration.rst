.. include:: ../urls.rst

.. meta::
   :description lang=en: Core Bcome concepts - the network configuration file

*********************
Network Configuration
*********************

Your Network Configuration defines the architecture of your :doc:`namespaces` and SSH configuration.  

In its most basic form it is a single YAML configuration file named ``networks.yml`` and stored within your ``bcome`` configuration directory (see: :doc:`../getting-started/create-project-structure`).

Network Configuration takes the following form:

.. code-block:: yaml

   ---
   namespace_key:
     attribute: value

   namespace_key:child_namespace_key
     attribute: value

For further information please refer to our :doc:`namespaces` documentation.

The |GUIDES|_ also have example implementations to get you started. 

.. note::

   Your network configuration may also be overriden and/or supplemented with additional configuration (see :doc:`../network/alternative-configuration`).

