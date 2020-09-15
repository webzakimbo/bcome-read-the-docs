.. meta::
   :description lang=en: The Bcome command menu

.. include:: ../urls.rst

************
Command Menu
************

Bcome has a series of in-built commands that can be executed within your namespaces. 

Within any given namespace, invoke ``menu`` to pull up the available in-built commands.

.. note::

   When in Keyed-Access mode (see: :doc:`navigation`) command parameters are whitespace rather than comma-delineated as they are for Console mode.

   For a guide to executing commands, see :doc:`executing-commands`.
   

All in-built commands are described below:

Command lists
-------------

+-----------------------------+--------------------------------------+---------------------------------------+
|                             |                                      |                                       |                                                   
|  command                    |  description                         | namespace availability                |  
+=============================+======================================+=======================================+
|  menu	  	              | Returns a list of all the in-built   | All		                     | 
|  			      | commands available at the current    |  			             |  						 
|  			      | namespace.			     |					     |                                                   
+-----------------------------+--------------------------------------+---------------------------------------+
|  registry                   | Returns a list of all the custom     | All       			     |  
|                             | commands configured to be available  | 					     |							 
|                             | at the current namespace.            |					     |						         
+-----------------------------+--------------------------------------+---------------------------------------+

Navigation commands
-------------------

+-----------------------------+--------------------------------------+---------------------------------------+
|                             |                                      |                                       |                                                   
|   command                   |  description                         | namespace availability                |
+=============================+======================================+=======================================+
|   cd *identifier*           |  Enter a console session for a child | Collection, Inventory, Sub-selected   |
|			      |  namespace.			     | Inventory, Merged Inventory.          |
|			      |  				     |					     |
|			      |	 Console only			     |					     |
+-----------------------------+--------------------------------------+---------------------------------------+
|   back                      |  Return to the parent namespace      | All                                   |
|                             |  console session.                    |                                       |
|                             |                                      | 					     |
|		              |  If at the root namespace, or within |					     |
|			      |  the namespace at which the Console  |					     |
|                             |  was initiated, invoking 'back'      |					     |
|                             |  will exit the Console.              |					     |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|   exit                      |  see 'back', above.                  | All                                   |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|   exit!                     |  Exits a Console session.            | All                                   |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+

.. _SELECTION_COMMANDS:

Selection Commands
------------------

+-----------------------------+--------------------------------------+---------------------------------------+
|                             |                                      |                                       |
|  command                    |  description                         | namespace availability                |
+=============================+======================================+=======================================+
|  workon *identifier1*,      |  Work on specific namespaces only,   | Collection, Inventory, Sub-selected   |
|  *identifier2* ...	      |  inactivating all others from the    | Inventory, Merged Inventory.          |
|			      |  selection.                          |					     |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  enable *identifier1*,      |  Re-enable a namespace within the    | Collection, Inventory, Sub-selected   |                                                  
|  *identifier2*  ...         |  namespace.                          | Inventory, Merged Inventory.          |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |              
+-----------------------------+--------------------------------------+---------------------------------------+
|  disable *identifier1*,     |  Remove a namespace from the         | Collection, Inventory, Sub-selected   |                                      
|  *identifier2* ...          |  selection.                          | Inventory, Merged Inventory.          |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |                                      
+-----------------------------+--------------------------------------+---------------------------------------+
|  enable!                    |  Enable all namespaces within the    | Collection, Inventory, Sub-selected   |
|                             |  selection.			     | Inventory, Merged Inventory.          |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  disable!                   |  Disable all namespaces within the   | Collection, Inventory, Sub-selected   |
|                             |  selection.			     | Inventory, Merged Inventory.          |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+ 
|  first                      |  A shortcut available in Keyed Access| Collection, Inventory, Sub-selected   |
|			      |  mode only when traversing           | Inventory, Merged Inventory.	     |
|                             |  namespaces.			     |                                       |
|			      |					     |                                       |
|			      |  e.g. bcome foo:bar:first:command    |					     |
|                             |                                      |                                       |
|                             |  *Keyed-access only*                 |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+


SSH Commands
------------

+-----------------------------+--------------------------------------+---------------------------------------+
|                             |                                      |                                       |
|  command                    |  description                         | namespace availability                |
+=============================+======================================+=======================================+
|  ping			      |  Test connectivity against all       | All				     |
|			      |  servers in the selection.	     |					     |
+-----------------------------+--------------------------------------+---------------------------------------+
|  run *command1*, *command2* |  Execute a command to be run         | All			             |
|			      |  against *all* servers contained in  |					     |
|			      |  the selection.	                     |				             |
+-----------------------------+--------------------------------------+---------------------------------------+
|  interactive                |  Access an interactive ssh           | All				     |
|                             |  pseudo-shell allowing you to execute| 					     |
|                             |  commands against all servers that   |					     |
|                             |  are children or grandchildren of the|					     |
|			      |  current namespace.		     | 				             |
+-----------------------------+--------------------------------------+---------------------------------------+
|  tunnel *local port*,       |  Create a Tunnel over SSH	     | Server. 				     |
|  *destination port*	      |  				     |				             |
|                             |  Transparently bypasses proxies.     |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  pseudo_tty *command*       |  Invoke a pseudo-tty session.	     | Server				     |
+-----------------------------+--------------------------------------+---------------------------------------+
|  execute_script             |  Execute a local bash-script over ssh| All			             |	
|  *path/to/bash/script*      |  against all servers in the          |					     |
|			      |  selection.			     |					     |
+-----------------------------+--------------------------------------+---------------------------------------+
|  ssh *identifier*	      |  Ssh to a server         	     | Inventory, Sub-selected               |
|                             | 				     | Inventory, Merged Inventory.	     |
+-----------------------------+--------------------------------------+---------------------------------------+
|  ssh                        |	 Ssh to a server		     | Server			             |
|                             |					     |					     |
+-----------------------------+--------------------------------------+---------------------------------------+

File & script commands
----------------------

+------------------------------+--------------------------------------+---------------------------------------+
|                              |                                      |                                       |
|  command                     |  description                         | namespace availability                |
+==============================+======================================+=======================================+
|  put *local/path*,           |  Upload a file (or directory,        | All				      | 
|  */remote/path*	       |  recursively) over SCP to all        |					      |
|			       |  servers in the selection.  	      |				              |
+------------------------------+--------------------------------------+---------------------------------------+
|  rsync *local/path*          |  Upload a file (or directory,        | All                                   |
|  */remote/path*	       |  recursively) over rsync (faster)    | 				      |
|			       |  to all servers in the selection.    |				              |
+------------------------------+--------------------------------------+---------------------------------------+
|  put_str *"string contents"* |  Write a file /to/remote/path to all | All				      |
|  */remote/path*	       |  servers in the selection from a     |					      |
|			       |  String.			      |					      |
+------------------------------+--------------------------------------+---------------------------------------+
|  get */remote/path*          |  Download a file or directory.       | Server		                      |
+------------------------------+--------------------------------------+---------------------------------------+

Informational
-------------

+-----------------------------+--------------------------------------+---------------------------------------+
|                             |                                      |                                       |
|  command                    |  description                         | namespace availability                |
+=============================+======================================+=======================================+
|  ls                         |  List all child namespaces.          | Collection, Inventory, Sub-selected   |
|                             |                                      | Inventory, Merged Inventory.          |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  lsa                        |  List all active child namespaces    | Collection, Inventory, Sub-selected   |
|                             |                                      | Inventory, Merged Inventory.          |
|                             |  See :ref:`SELECTION_COMMANDS`       |                                       |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  tree                       |  Print a tree view of all child      | Collection, Inventory, Sub-selected   |
|                             |  namespaces and their sub-namespaces.| Inventory, Merged Inventory.          |
+-----------------------------+--------------------------------------+---------------------------------------+
|  meta                       |  List all Metadata available to      | All				     |
|			      |  the current namespace.		     |					     |
|			      |					     |					     |
|		              |  See: :doc:                          |				     	     |
|			      |  `../metadata/metadata-commands` for | 					     |
|			      |  working with metadata. 	     |					     |
+-----------------------------+--------------------------------------+---------------------------------------+
|  tags                       |  List all cloud provider tags/labels | Server, Inventory, Sub-selected       | 
| 			      |  associated with the server(s)       | Inventory, Merged Inventory.          |                             
+-----------------------------+--------------------------------------+---------------------------------------+
|  routes		      |  Print SSH routing tree.             | All				     |
+-----------------------------+--------------------------------------+---------------------------------------+


Miscellaneous 
-------------

+-----------------------------+------------------------------------------------------+---------------------------------------+
|                             |                                                      |                                       |
|  command                    |  description                                         | namespace availability                |
+=============================+======================================================+=======================================+
|  reload		      |  Re-populate an inventory from its                   | Inventory, Sub-selected Inventory     |
|			      |  source, e.g. reload all servers from                |				             |
|			      |  within an inventory from its remote                 |					     |
|			      |  cloud.				                     |					     |
+-----------------------------+------------------------------------------------------+---------------------------------------+
|  cache		      |  Save a local copy of an inventory.                  | Inventory.			     |
|			      |				                             |				             |
|			      |  The cache is saved as a static manifest.            |					     |
|			      |  (see: :doc:`../network/static-manifests`)           |                                       |
|		              |							     |                                       | 
|			      |  To disable the Cache, remove the static manifest.   |                                       |
+-----------------------------+------------------------------------------------------+---------------------------------------+
