.. meta::
   :description lang=en: Bcome installation requirements.

************
Requirements
************

- Ruby 2.5 or greater.

- A Ruby compatible OS.

- If you intend to interact with servers over SSH, you'll need a running ssh-agent with your keys added.  For programmatic access, Bcome makes use of your ``SSH_AUTH_SOCK`` environment variable to find your ssh-agent (and then your keys).

- ``kubectl`` installed and in $PATH if you intended to interact with Kubernetes clusters.

- ``helm`` installed and in $PATH if you intend to interact with Kubernetes clusters and wish to add a Helm hook.

- ``Terraform`` installed and in $PATH if you intend to add a Terraform hook.

.. include:: ssh-version-requirement-note.rst

.. include:: m1-mac-requirements.rst
