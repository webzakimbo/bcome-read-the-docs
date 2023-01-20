.. meta::
   :description lang=en: Bcome installation requirements.

************
Requirements
************

- Ruby 2.5 or greater.

- A running ssh-agent with your keys added if you intend to interact with servers over SSH. For programmatic access, Bcome makes use of your ``SSH_AUTH_SOCK`` environment variable to find your ssh-agent (and then your keys).

- ``kubectl`` installed and in PATH if you intended to interact with Kubernetes clusters (contextual kubectl, tied to a Kubernetes cluster or namespace).

- ``helm`` installed and in PATH if you intend to interact with Kubernetes clusters and wish to add a Helm hook (contextual helm invocation, tied to a Kubernetes cluster or namespace)

.. include:: ssh-version-requirement-note.rst

.. include:: m1-mac-requirements.rst
