.. meta::
   :description lang=en: Bcome usage: Optimising SSH

.. include:: ../urls.rst

**************
Optimising Ssh
**************

When interacting with machines over SSH Bcome will attempt to connect to all machines in any given selection at once, re-trying connection attempts and auto-reconnecting should connections be lost.

It will also cache the connections until the Bcome session has terminated.

This can be problemmatic for some jump hosts with default configuration, that may not be able to handle Bcome's connection attempts. 

This can be resolved by correctly setting your jump host's SSH daemon's ``MaxStartups`` and ``MaxSessions`` attributes (if you're running OpenSSH) in line with your installation's requirements.

.. note::

   As a general rule of thumb, set MaxStartups and MaxSessions to be equal to the number of machines you need to manage via a particular jump host.  A lower number will result in dropped connections, that although Bcome will catch and attempt re-connection, could result in slower startup time and/or failure to connect.

