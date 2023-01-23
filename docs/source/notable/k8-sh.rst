.. meta::
   :description lang=en: Bcome usage: Accessing a shell on a running Kubernetes container

.. include:: ../urls.rst

***************
Container shell
***************

When in the scope of a Kubernetes container node, you may access a shell by invoking the "sh" method.

Usage
^^^^^

Invoke ``sh`` on any Bcome Container node that supports the "/bin/sh" shell and you will enter a session on the container.

.. note::

  For guidance on how to execute commands, see :doc:`../usage/executing-commands`

Switching shells
^^^^^^^^^^^^^^^^

By default, this feature assumes a "/bin/sh" shell present on your container.

When in console mode (see :doc:`../usage/navigation`) you may pick an alternative shell by reference when invoking `sh`.

For example, given the following available shells 

* bash (/bin/bash)
* ash (/bin/ash)
* sh (/bin/sh)
* dash (/bin/dash)

You would select `ash` by invoking the shell as follows:

.. code-block:: bash

  > sh("ash")

