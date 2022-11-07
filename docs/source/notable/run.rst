.. meta::
   :description lang=en: Bcome usage: Using run to execute a command or commands across single or multiple servers

.. include:: ../urls.rst

***
Run
***

The 'run' command allows you to execute commands on your servers over SSH. You can target either individual, or groups of servers (where you execute the same command on multiple machines in parallel).

Run may be invoked with the ``run`` command on any node. See :doc:`../usage/executing-commands`.

.. note::

   When in the Console, Bcome caches all SSH connections, with re-connection automatic, resulting in faster execution of repeated 'run' commands.

For more information on optimising your SSH connections see :doc:`../usage/optimising-ssh`
