.. meta::
   :description lang=en: Bcome usage: Optimising SSH and dealing with dropped connections due to default jump host configuration.

.. include:: ../urls.rst

**************
Optimising Ssh
**************

When interacting with machines over SSH Bcome will attempt to connect to all machines in any given selection at once, re-trying connection attempts and auto-reconnecting should connections be lost.

It will also cache the connections until the Bcome session has terminated.

This can be problemmatic for some jump hosts with default configuration, that may not be setup to handle the volume of concurrent connection requests that Bcome will make (one per server in your selected node). 

This can be resolved by correctly setting your jump host's SSH daemon's ``MaxStartups`` and ``MaxSessions`` attributes (if you're running OpenSSH) in line with your installation's requirements.

.. note::

   As a general rule of thumb set MaxStartups and MaxSessions to be equal to the number of machines you need to manage via a particular jump host.  A lower number will result in dropped connections, and although Bcome will catch these and re-connect, this can result in a slower startup time.

