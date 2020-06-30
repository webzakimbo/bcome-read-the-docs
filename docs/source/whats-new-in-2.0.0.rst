.. meta::
   :description lang=en: What's new in Bcome 2.0.0

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
* multi-cloud: Orchestrate machines form multiple-clouds at the same time
* hybrid-cloud:  Orchestrate your static/on-premise infrasrtucture as well as your Cloud machines at the same time.
* hybrid-multi-cloud: Create merged multi-cloud & static inventories and orchestrate them all from the same scripts/console.

Multi-hop SSH proxying
----------------------

Configure chains of SSH proxies, allowing for transparent multi-hop setups.

Metadata
--------

Metadata now has a 'diff' function see :doc:`metadata/metadata-encryption`

