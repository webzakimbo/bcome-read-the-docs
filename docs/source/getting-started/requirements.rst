.. meta::
   :description lang=en: Bcome installation requirements.

************
Requirements
************

- Ruby 2.5 or greater.

- A Ruby compatible OS.

- SSH keys configured on your target machines.

- To interact with machines over SSH you'll need a running ssh-agent on your client (where Bcome is installed) with all relevant ssh keys added.  For programmatic access, Bcome makes use of your ``SSH_AUTH_SOCK`` environment variable to find your ssh-agent (and then your keys).

.. include:: ssh-version-requirement-note.rst

.. include:: m1-mac-requirements.rst
