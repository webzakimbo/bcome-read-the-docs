.. meta::
   :description lang=en: Bcome installation requirements.

************
Requirements
************

- Ruby 2.5 or greater.

- A Ruby compatible OS.

- SSH keys configured on your target machines

- A running ssh-agent on your client machine with all relevant ssh keys added. For programmatic access Bcome references your ``SSH_AUTH_SOCK`` environment variable to find your ssh-agent (and then your keys).

- Servers to connect to !

.. include:: ssh-version-requirement-note.rst
