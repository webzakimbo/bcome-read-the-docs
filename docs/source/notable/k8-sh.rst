.. meta::
   :description lang=en: Bcome usage: Accessing a shell on a running Kubernetes container

.. include:: ../urls.rst

***************
Container shell
***************

When in the scope of a Kubernetes container node you can access a shell on the remote container via Bcome.

Usage
^^^^^

Invoke ``sh`` on any Bcome node whose associated container supports the "/bin/sh" shell and you will enter a session on the container.

Let's imagine the following Pod -> Container hierarchy:

.. code-block:: bash

   .
   └── pod_foo
       └── container_bar

Access a console session and enter the container shell for container `container_bar`:

.. code-block:: bash

  > bcome pod_foo:container_bar
  > sh

Or access directly from your terminal, using keyed access:

.. code-block:: bash

  > bcome pod_foo:container_bar:sh

.. note::

  For more guidance on how to execute commands, see :doc:`../usage/executing-commands`

Switching shells
^^^^^^^^^^^^^^^^

By default 'sh' assumes a "/bin/sh" shell present on your container. In console mode (see :doc:`../usage/navigation`) you may pick an alternative shell.

For example, given the following available shells 

* bash (/bin/bash)
* ash (/bin/ash)
* sh (/bin/sh)
* dash (/bin/dash)

You would select `ash` by invoking the shell as follows:

.. code-block:: bash

  > sh("ash")

