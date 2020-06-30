.. meta::
   :description lang=en: Breaking changes in Bcome 2.0.0

Breaking changes in Bcome 2.0.0
===============================

Bootstrapping mode
------------------

Previous Bcome releases came with a Bootstrap toggle in order to flip the SSH connection configuration. This feature has been removed, and superseded by the ``ME=`` and/or ``me.yml`` configuration overrides.

For more information see :doc:`network/alternative-configuration`

SSH Key handling
----------------

Pre 2.0.0, Bcome implicitly utilised ssh keys in the client's ssh-agent for ssh'ing into (i.e. getting a terminal onto) a node, whilst programmatic access relied on the paths to SSH keys being expressly added to configuration.

In 2.0.0 you no longer need to specify ssh keys for programmatic access.  

All you need to do now is ensure that you have your ssh-agent running, and all keys in play added to your agent.  Bcome will then reference your ``SSH_AUTH_SOCK`` environment variable to find your ssh-agent (and then your keys).

SSH Proxying
------------

For simplicity, Bcome now utilises SSH's ProxyJump (-J) syntax rather than ProxyCommand. As such, Bcome requires that all clients and forwarding proxies have an SSH version compatible with ProxyJump, such as OpenSsh >= 7.3

Support for ProxyCommand will be re-introduced as an override option to ProxyJump in a future release.

Merge of static & cached inventories
------------------------------------

Static manifests (:doc:`network/static-manifests` are how defined in the same way as Bcome handles the caching of remote inventories.  

If you're using static manifests, you will need to rename your ``machines-cache.yml`` to ``static-cache.yml``.

Change to location of AWS credentials
-------------------------------------

Bcome now expects AWS credentials keys to be written to ``project-directory/.aws/keys`` rather than the previous path at ``~/.fog``
