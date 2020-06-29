.. include:: ../urls.rst

.. meta::
   :description lang=en: The role of SSH in a Bcome installation

***
SSH
***

SSH is core to Bcome, as all interactions with machines are over SSH.

It is HIGHLY recommended that you have SSH keys setup on the machines with which you wish to interact and a running ssh-agent.

.. include:: ../getting-started/ssh-version-requirement-note.rst

Bcome will delegate to your local Operating System for all SSH interactions.

.. warning::

   Ensure that you have your ssh-keys added to your local ssh-agent.

   Bcome will reference your ssh-agent's socket via the SSH_AUTH_SOCK environment variable and make use of your configured ssh-keys.

   For access to servers where keys are not configured, authorisation will delegate to the installed configuration.
