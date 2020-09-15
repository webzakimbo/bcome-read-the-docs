.. meta::
   :description lang=en: Bcome usage: Accessing remote pseudo terminals using pseudo_tty

.. include:: ../urls.rst

**********
Pseudo-tty
**********

Bcome's pseudo-tty mode allows you to access a pseudo terminal from any server namespaces.

As Bcome handles your SSH configuration for you via your :doc:`../core-concepts/network-configuration`, setting up a pseudo-tty session becomes simple. 

This is useful should you wish to do something like the following:

* Tail a remote log file from your local server
* Open up a remote console, e.g. a MySQL console, Rails console, MongoDb etc


How to use pseudo-tty within Bcome
==================================

Use case 1: tail a remote file
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You wish to tail a remote log file, and you usually SSH in to your server and type in the following:

.. code-block:: bash

   tail -f /path/to/your/file.log

Given a server namespace named app1 within a collection namespace of production, you would instead:

.. code-block:: bash

   bcome production:app1:pseudo_tty "tail -f /path/to/your/file.log"

Use case 2: open a mysql console
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You wish to open up a mysql console, and you’d usually SSH in to your server and type in the the following:

.. code-block:: bash

   mysql -u user -p password -h hostname database

Given a server namespace named app1 within a collection namespace of production, you would instead:

.. code-block:: bash

   bcome production:app1:pseudo_tty "mysql -u user -p password -h hostname database"

Access from the Console
=======================

The pseudo_tty function is also accessible directly from the Console.

.. code-block:: bash

   bcome namespace
   cd server
   pseudo_tty "your command"


Incorporating Pseudo-tty sessions as a Registry hook
==================================================

You may wish to be able to access a database console directly from Bcome as follows:

.. code-block:: bash

   bcome staging:app1:db

The 'db' invocation would be a Bcome registry hook (see: :doc:`../registry/overview`), referencing an internal script (see :doc:`../orchestration/internal-ruby-scripting`), within which you would declare the pseudo-tty function as follows:

.. code-block:: ruby
  
   def execute
     @node.pseudo_tty("mysql -u user -p password -h host")
   end
  
