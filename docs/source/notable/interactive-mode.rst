.. meta::
   :description lang=en: Bcome usage: Real-time orchestration to multiple machines at once with Bcome's Interactive mode.

.. include:: ../urls.rst

****************
Interactive Mode
****************

Interactive mode allows you to enter repeated commands in a transparent context to either single, or multiple servers/containers without having to enter repeated ``run`` commands (see: :doc:`../usage/command-menu`).

Having established a connection, Interactive mode then provides a secondary interactive pseudo-shell, following which any commands you enter are executed on every server/container.

.. warning::

   Interactive mode can be dangerous.

   You will be executing commands in parallel on every machine in your selection.  Be sure you understand what you're running (and with what privileges) before using this function.

Interactive mode is useful when managing groups of servers/containers in a real-time scenario for example:

* to apply security patches
* to test en masse for vulnerabilities
* to run system updates
* to compare configurations

.. note::

   Interactive mode will create a connection to every server/container that is a child or grand-child of the current node. 
   
   Once connected, connections are cached for speed with reconnections automatic.

For more information on optimising your SSH for interactive mode see :doc:`../usage/optimising-ssh`

Interactive mode may be invoked with the ``interactive`` command on any node. See :doc:`../usage/executing-commands`.
