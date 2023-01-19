.. meta::
   :description lang=en: The Bcome command menu

.. include:: ../urls.rst

************
Command Menu
************

Bcome has a series of in-built commands that can be executed within your nodes.

Within any given node, invoke ``menu`` to pull up the available in-built commands.

.. note::

   When in Keyed-Access mode (see: :doc:`navigation`) command parameters are whitespace rather than comma-delineated as they are for Console mode.

   For a guide to executing commands, see :doc:`executing-commands`.
   

All in-built commands are described below:

Command lists
-------------

+-----------------------------+--------------------------------------+---------------------------------------+
|                             |                                      |                                       |                                                   
|  command                    |  description                         | node type                             |  
+=============================+======================================+=======================================+
|  menu	  	              | Returns a list of all the in-built   | All		                     | 
|  			      | commands available at the current    |  			             |  						 
|  			      | node.			             |					     |                                                   
+-----------------------------+--------------------------------------+---------------------------------------+
|  registry                   | Returns a list of all the custom     | All       			     |  
|                             | commands configured to be available  | 					     |							 
|                             | at the current node.                 |					     |						         
+-----------------------------+--------------------------------------+---------------------------------------+

Navigation commands
-------------------

+-----------------------------+--------------------------------------+---------------------------------------+
|                             |                                      |                                       |                                                   
|   command                   |  description                         | node type                             |
+=============================+======================================+=======================================+
|   cd name                   |  Enter a console session for a child | Collection, Inventory, Sub-selected   |
|			      |  node.		      	             | Inventory, Merged Inventory.          |
|   cd name1:name2            |  				     |					     |
|			      |	 Console only			     |					     |
|   cd #rootname:name2        |                                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|   back                      |  Return to the parent node           | All                                   |
|                             |  console session.                    |                                       |
|                             |                                      | 					     |
|		              |  If at the root node, or within      |					     |
|			      |  the node at which the Console       |					     |
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
|  command                    |  description                         | node type                             |
+=============================+======================================+=======================================+
|  workon *identifier1*,      |  Work on specific node only,         | Collection, Inventory, Sub-selected   |
|  *identifier2* ...	      |  inactivating all others from the    | Inventory, Merged Inventory.          |
|			      |  selection.                          |					     |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  enable *identifier1*,      |  Re-enable a node within the         | Collection, Inventory, Sub-selected   |                                                  
|  *identifier2*  ...         |  node.                               | Inventory, Merged Inventory.          |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |              
+-----------------------------+--------------------------------------+---------------------------------------+
|  disable *identifier1*,     |  Remove a node from the              | Collection, Inventory, Sub-selected   |                                      
|  *identifier2* ...          |  selection.                          | Inventory, Merged Inventory.          |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |                                      
+-----------------------------+--------------------------------------+---------------------------------------+
|  enable!                    |  Enable all node within the          | Collection, Inventory, Sub-selected   |
|                             |  selection.			     | Inventory, Merged Inventory.          |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  disable!                   |  Disable all node within the         | Collection, Inventory, Sub-selected   |
|                             |  selection.			     | Inventory, Merged Inventory.          |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+ 
|  first                      |  A shortcut available in Keyed Access| Collection, Inventory, Sub-selected   |
|			      |  mode only when traversing           | Inventory, Merged Inventory.	     |
|                             |  node.			             |                                       |
|			      |					     |                                       |
|			      |  e.g. bcome foo:bar:first:command    |					     |
|                             |                                      |                                       |
|                             |  *Keyed-access only*                 |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+


Interactive Commands
--------------------

Interactive are those that interact directly with servers or containters.

+-----------------------------+--------------------------------------+---------------------------------------+
|                             |                                      |                                       |
|  command                    |  description                         | available to node                     |
+=============================+======================================+=======================================+
|  ping			      |  Test connectivity against all       | All excluding Kubernetes.             |
|			      |  servers in the selection.	     |					     |
+-----------------------------+--------------------------------------+---------------------------------------+
|  run *command1*, *command2* |  Execute a command to be run         | Any (runs over entire selection)	     |
|			      |  against *all* servers contained in  |					     |
|			      |  the selection.	                     |				             |
+-----------------------------+--------------------------------------+---------------------------------------+
|  interactive                |  Access an interactive ssh           | All				     |
|                             |  pseudo-shell allowing you to execute| 					     |
|                             |  commands against all servers that   |					     |
|                             |  are children or grandchildren of the|					     |
|			      |  current node.    		     | 				             |
+-----------------------------+--------------------------------------+---------------------------------------+
|  tunnel *local port*,       |  Create a Tunnel over SSH	     | Server. 				     |
|  *destination port*	      |  				     |				             |
|                             |  Transparently bypasses proxies.     |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  pseudo_tty *command*       |  Invoke a pseudo-tty session.	     | Server				     |
+-----------------------------+--------------------------------------+---------------------------------------+
|  execute_script             |  Execute a local bash-script over ssh| Server			             |	
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
|  command                     |  description                         | node type                             |
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
|  command                    |  description                         | node type                             |
+=============================+======================================+=======================================+
|  ls                         |  List all child node.                | Collection, Inventory, Sub-selected   |
|                             |                                      | Inventory, Merged Inventory.          |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  lsr                        |  Reload (e.g. from remote) then list | Any Kubernetes node.                  | 
|                             |  all child nodes.                    |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  lsa                        |  List all active child nodes         | Collection, Inventory, Sub-selected   |
|                             |                                      | Inventory, Merged Inventory.          |
|                             |  See :ref:`SELECTION_COMMANDS`       |                                       |
|                             |                                      |                                       |
|                             |  *Console only*                      |                                       |
+-----------------------------+--------------------------------------+---------------------------------------+
|  tree                       |  Print a tree view of all child      | Collection, Inventory, Sub-selected   |
|                             |  nodes and their sub-nodes.          | Inventory, Merged Inventory.          |
+-----------------------------+--------------------------------------+---------------------------------------+
|  meta                       |  List all Metadata available to      | All				     |
|			      |  the current node.    	             |					     |
|			      |					     |					     |
|		              |  See: :doc:                          |				     	     |
|			      |  `../metadata/metadata-commands` for | 					     |
|			      |  working with metadata. 	     |					     |
+-----------------------------+--------------------------------------+---------------------------------------+
|  tags                       |  List all cloud provider tags/labels | Server, Inventory, Sub-selected       | 
| 			      |  associated with the server(s)       | Inventory, Merged Inventory.          |                             
+-----------------------------+--------------------------------------+---------------------------------------+
|  routes		      |  Print SSH routing tree.             | All, excluding Kubernetes nodes       |
+-----------------------------+--------------------------------------+---------------------------------------+

Kubernetes
----------

+-----------------------------+------------------------------------------+---------------------------------------+
|                             |                                          |                                       |
|  command                    |  description                             | node type                             |
+=============================+==========================================+=======================================+
|  config                     |  Display the config for a node's         | Any kubernetes node.                  |
|                             |  associated kubernetes object.           |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  logs                       |  Aggregate logs from all containers      | Any kubernetes node.                  |
|                             |  into one live stream.                   |                                       |                                             
+-----------------------------+------------------------------------------+---------------------------------------+
|  pathways                   |  Render a tree view of all routing       | Any kubernetes node.                  |
|                             |  pathways (hosts->path->pod->container). |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  helm                       |  Access an interactive helm shell        | GKE Cluster, EKS Cluster, Kubernetes  |
|                             |  scoped to the underlying kubernetes     | namespace.                            |
|                             |  object's kubernetes context.            |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  kubectl                    |  Access kubectl scoped to the underlying | GKE Cluster, EKS Cluster, Kubernetes  |
|                             |  kubernetes object's kubernetes context. | namespace.                            |
+-----------------------------+------------------------------------------+---------------------------------------+
|  reauthorize                |  Reauthorize with the cluster API        | Any kubernetes node.                  |
+-----------------------------+------------------------------------------+---------------------------------------+
|  tunnel                     |  Forward a Pod port to your local machine| Pod                                   |
+-----------------------------+------------------------------------------+---------------------------------------+
|  describe                   |  Describe the underlying kubernetes      | Any kubernetes node                   |  
|                             |  object.                                 |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  export                     |  Export a cluster or cluster namespace's | GKE Cluster, EKS Cluster, Kubernetes  |
|                             |  context so that it may be used with     | namespace.                            |
|                             |  external applications outside of Bcome  |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  info                       |  Cluster information.                    | GKE Cluster, EKS Cluster.             |
+-----------------------------+------------------------------------------+---------------------------------------+
|  info_dump                  |  Cluster information dump.               | GKE Cluster, EKS Cluster.             |
+-----------------------------+------------------------------------------+---------------------------------------+
|  interactive                |  Execute commands in an interative shell | Any kubernetes node.                  |
|                             |  against all containers.                 |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  pseudo_tty                 |  Execute a command using an interactive  | Kubernetes container.                 | 
|                             |  session.                                |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  sh                         |  Enter a shell on a running container.   | Kubernetes container.                 |
+-----------------------------+------------------------------------------+---------------------------------------+
|  focus *object*             |  Switch workspace to focus on a specific | GKE Cluster, EKS Cluster.             |  
|                             |  kubernetes resource type.               |                                       |
|                             |                                          |                                       |
|                             |  e.g. for secrets, *focus secret*        |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  vrender *view*             |  Render an alternative hierarchy view.   | GKE Cluster, EKS Cluster.             |
|                             |                                          |                                       |
|                             |  Enter 'menu' to see available options.  |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+ 
|  vfocus *view*              |  Switch your workspace to use an         | GKE Cluster, EKS Cluster.             |
|                             |  alternative hierarchy view.             |                                       |
|                             |                                          |                                       |
|                             |  Enter 'menu' to see available options.  |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  read                       |  Output the contents of a Kubernetes     | K8Cluster Secret                      |
|                             |  secret (decoded).                       |                                       |
+-----------------------------+------------------------------------------+---------------------------------------+
|  trigger                    |  Trigger a cronjob.                      | K8Cluster Cronjob                     |
+-----------------------------+------------------------------------------+---------------------------------------+



Miscellaneous 
-------------

+-----------------------------+------------------------------------------------------+---------------------------------------+
|                             |                                                      |                                       |
|  command                    |  description                                         | node type                             |
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
