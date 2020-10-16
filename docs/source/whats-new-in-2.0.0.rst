.. include:: urls.rst

.. meta::
   :description lang=en: What's new in Bcome 2.0.0?

What's new in 2.0.0
====================

Google Cloud Platform
---------------------

You may now integrate GCP. 

See: :doc:`getting-started/prepare-gcp-access`

Static Cloud
------------

You may now add static/on-premise infrastructure and/or add in machines from providers for which Bcome does not currently have API support.

See: :doc:`network/static-manifests`


Merged Inventories
------------------

Merge inventories from disparate networks, clouds or static/on-premise configurations. 

This will give you installations that are:

* multi-network: Orchestrate machines from multiple networks within the same cloud provider at the same time.
* multi-cloud: Orchestrate machines from multiple-clouds at the same time
* hybrid-cloud:  Orchestrate your static/on-premise infrastructure as well as your Cloud machines at the same time.
* hybrid-multi-cloud: Create merged multi-cloud & static inventories and orchestrate them all from the same scripts/console.

Multi-hop SSH proxying
----------------------

Configure chains of SSH proxies, allowing for transparent multi-hop setups.

SSH Key handling
----------------

Pre 2.0.0, Bcome implicitly utilised ssh keys in the client's ssh-agent for ssh'ing into (i.e. getting a terminal onto) a node, whilst programmatic access relied on the paths to SSH keys being expressly added to configuration.

In 2.0.0 you no longer need to specify ssh key paths for programmatic access.

All you need to do now is ensure that you have your ssh-agent running, and all keys in play added to your agent.  Bcome will then reference your ``SSH_AUTH_SOCK`` environment variable to find your ssh-agent (and then your keys).


Metadata
--------

Metadata now has a 'diff' function see :doc:`metadata/metadata-encryption`

Tree View
---------

New and improved network tree-view.

Routes view
-----------

The new ``routes`` command prints out an SSH routing tree for any namespace. See it in action here: |ROUTES_GUIDE|_.

