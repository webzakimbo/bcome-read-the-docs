.. include:: ../urls.rst

.. meta::
   :description lang=en: Your network configuration defines the architecture of your nodes and SSH configuration.

*********************
Network Configuration
*********************

Your Network Configuration defines the architecture of your :doc:`nodes`.  

In its most basic form it is a single YAML configuration file named ``networks.yml`` and stored within your ``bcome`` configuration directory (see: :doc:`../getting-started/create-project-structure`).

Network Configuration takes the following form:

.. code-block:: yaml

   ---
   node_key:
     attribute: value

   node_key:child_node_key
     attribute: value

For further information please refer to our :doc:`nodes` documentation.

The |GUIDES|_ also have example implementations to get you started. 

.. note::

   Your network configuration may also be overriden and/or supplemented with additional configuration (see :doc:`../network/alternative-configuration`).

