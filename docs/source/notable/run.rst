.. meta::
   :description lang=en: Bcome usage: Using run to execute a command or commands across single or multiple servers and containers

.. include:: ../urls.rst

***
Run
***

The 'run' command allows you to execute commands on your servers (over SSH), or on your Kubernetes containers (transparently, via Kubectl). You can target either individual, or groups of servers/containers where the same command is executed in parallel on all machines in your selection.

.. hint::

  When in console mode you can use the in-built ``workon`` command to modify the scope of your selection.  See :doc:`../usage/command-menu` or enter ``menu`` when in console mode for more information on how to use ``workon``.

Run may be invoked with the ``run`` command on any node. See :doc:`../usage/executing-commands`.

.. note::

   When in console mode Bcome caches all SSH connections, with re-connection automatic, resulting in faster execution of repeated 'run' commands.

For more information on optimising your SSH connections see :doc:`../usage/optimising-ssh`
