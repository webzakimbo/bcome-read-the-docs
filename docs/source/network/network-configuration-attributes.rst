.. meta::
   :description lang=en: Bcome Network configuration file attributes.

.. include:: ../urls.rst

********************
Namespace attributes
********************

Here you'll find the full list of attributes you may use within your networks.yml file in order to define your :doc:`../core-concepts/nodes`:

Namespace Block
===============

Used to configure a node

+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|                             |                             |                                       |                                                                                |
|   attribute key             |  description                | optional                              |   notes                                                                        |
+=============================+=============================+=======================================+================================================================================+
|   type                      | Used to define the node     | no                                    | See :doc:`../core-concepts/nodes` for further information                      |
|                             | type.                       |                                       |										     |
|                             |                             |                                       |										     |
|                             |                             |					    | Permitted values are 'collection', 'inventory', 'inventory-subselect' and      |
|                             |                             |					    | 'inventory-merge'.	  						     |
|                             |                             |					    |										     |
|                             |                             |					    |										     |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|   description               | A description of your 	    | no				    | Your description will be used as a label within your installation's UI.        |
|   			      | node.	   	            |					    |										     |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|   network	              | A hash of attributes        | yes				    | If left blank, any Inventories inheriting this configuration will not be       |
|  			      | defining a Cloud Provider   | 					    | populated with servers unless a Statically defined manifest has been configured|
|                             | configuration.              |                                       | 									             |
|                             |                             |                                       | Restricted to nodes of type 'collection', 'inventory', 'gcp-k8s-cluster' and   |
| 			      |	         	            |					    | 'aws-k8s-cluster'.                                                             |
|                             |                             |                                       |                                                                                |			
|			      |				    |					    | See :ref:`NETWORK_ATTRS`.                        			             |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|   ssh_settings              | A hash of attributes used to| yes                                   | Leave this blank and Bcome will default to initiating direct SSH connection    |
|                             | define an SSH architecture. |					    | attempts only (i.e. no proxies) and will fallback to using your terminal user  |
|                             |                             |					    | as your SSH username.  				      			     |
|                             |				    |					    |							                             |
|                             | 			    |					    | Restricted to nodes of type 'collection' and 'inventory' only.                 |
|			      |				    |					    |										     |
|			      |				    |					    | See :ref:`SSH_ATTRS`.                             			     |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|   sub_filter	              | A hash of attributes used to| yes                                   | Restricted to nodes of type 'inventory-subselect' only.     		     |
|		              | further filter a list of    | 					    |										     |	 
|	                      |	machines from an inventory. |					    | If you're sub-filtering a 'gcp' inventory, your filters are a Hash of GCP tags |
|	                      |				    |					    | and their values.				 				     |
|	                      |	                            |				            |										     |
|                             |                             |                                       | If you're sub-filtering an 'aws' inventory, your filters are a Hash of EC2     |             
|			      |				    |					    | and their values. 							     |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|  override_identifier        | A regular expression used to| yes                                   | Restricted to nodes of type 'inventory', 'inventory-subselect' and             |
|                             | rewrite the names of servers|                                       | 'inventory-merge'.							     |
|			      |	within an inventory	    |					    |										     |
|                             |                             |                                       | A regular expression with a single selector is expected, for example	     |
|                             |                             |					    | given a server named "Foo_Bar" and a regular expression of "[a-z]*_([a-z]*)"   |
|			      |			            |				            | the server will be renamed "Bar".						     |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+ 
|  hidden                     | A toggle to hide a node     | yes                                   | set to 'true' or 'false'                                                       |
|                             | from view.                  |                                       |                                                                                |
|                             |                             |                                       | Hidden nodes may still be interacted with, but will not appear in the          |
|                             |                             |                                       | user interface.                                                                |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+

.. note::

   Note that ``ssh_settings`` and ``network`` configuration may be inherited and overidden in child nodes.

   See :doc:`inheritance-and-overidding`


.. _NETWORK_ATTRS:

Network attributes
------------------

A Hash of attributes used to populate the top-level ``network`` attribute.

Used to configure a Cloud-provider.

See the full list of configurable attributes here:

+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|                             |                             |          				    |                                             			      	     |
|   attribute key             |  description                | optional 				    |   notes                 				                             |
+=============================+=============================+=======================================+================================================================================+
|  type                       | The cloud provider type     |  yes                                  | Set to "gcp" for Google Cloud Platform. Set to "ec2" for Amazon Web Services.  |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+

Google Cloud platform specific network attributes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|                             |                             |                                       |                                                                                |
|   attribute key             |  description                | optional                              |   notes                                                                        |
+=============================+=============================+=======================================+================================================================================+
|  project                    | GCP project id              |  Required for 'gcp' provider type     | Be careful to set this to the project id, and not the project name.            |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|  zone                       | GCP zone                    |  Required for 'gcp' provider type     | For a full list of zones see: |GCP_ZONES|_.                                    |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|  authentication_scheme      | GCP authentication scheme   |  Required for 'gcp' provider type     | Supported schemes are 'oauth' or 'service_account'. For OAuth 2.0 setup see    |
|                             |                             |          			            | :doc:`../getting-started/prepare-gcp-access`                                   |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|  service_scopes             | An array of GCP auth scopes |  Optional for 'gcp' provider type     | A minimum scope of |GCP_SCOPE_COMPUTE_READONLY|_ is                            |
|                             | passed to GCP during        |                                       | required in order to list resources.  For OAuth 2.0                            |
|                             | authorisation.              |  				            | |GCP_SCOPE_CLOUD_PLATFORM|_ is required.                                       |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|  filters  ('gcp' provider)  | A filter string to filter   |  Optional for 'gcp' provider type     | As an example, to return running instances, set filter to "status:running"     |
|                             | instances returned by GCP.  |       				    | For further information on topic filtering, see |GCP_TOPIC_FILTERING|_.        |
|                             |                             |                                       | You may also filter by_label. Have a look at our |GUIDES|_ site for examples 
|                             |                             |                                       | of this.
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|  service_account_credentials| The name of the service     |  Optional for 'gcp' provider type     | Required for the service_account authentication scheme only. See               | 
|                             | account credentials json    |       				    | :doc:`../getting-started/prepare-gcp-access`.                                  |
|                             | file, to be found within    |          				    |                                                                                |
|                             | the .gauth directory.       |         			            |                                                                                |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|  secrets_filename           | The name of your OAuth 2.0  | Optional for 'gcp' provider type	    | Required for the oauth authentication scheme only. 		             |
|			      | clients secrets filename    | 				            | See :doc:`../getting-started/prepare-gcp-access`.				     |
|			      | to be found within the      |			                    |										     |	
|			      | .gauth directory.	    |					    |									             |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+	

.. note::

  Google Cloud Platform require a minimum permission of ``compute.instances.list`` for OAuth 2.0 authorisations.  Ensure that any users attempting to authorize by OAuth 2.0 have been
  configured with a role containing this permission.


AWS specific network attributes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|                             |                             |                                       |                                                                                |
|   attribute key             |  description                | optional                              |   notes                                                                        |
+=============================+=============================+=======================================+================================================================================+
|  credentials_keys           | The reference to an AWS     |  Required for 'ec2' provider type     | For setup see :doc:`../getting-started/prepare-aws-access`.                    |
|                             | credentials key from your   |         				    |                                                                                |
|                             | .aws/keys file              |  					    |                                                                                |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|  provisioning_region        | An EC2 provisioning region  |  Required for 'ec2' provider type     | e.g. eu-west-1                                                                 | 
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+
|  filters ('ec2' provider)   | A hash of ec2 filters sent  |  Optional for 'ec2' provider type     | For a full list of available filters, see |EC2_FILTER_LIST|_.                  | 
|                             | during the lookup request to|                                       |                                                                                |
|                             | ec2.                        |                                       |                                                                                |
+-----------------------------+-----------------------------+---------------------------------------+--------------------------------------------------------------------------------+

.. _SSH_ATTRS:

SSH Settings Attributes
-----------------------

A hash of attributes used to populate the top-level ``ssh_settings`` attribute.

.. note::

   Namespaces without an SSH Settings element will default to initiating direct connection attempts against your servers using your local terminal username as the SSH username. Proxied
   ssh connections will not be possible.

See the full list of configurable attributes here:

+-----------------------------+-----------------------------+----------+--------------------------------------------------------------------------------+
|                             |                             |          |                                                                                |
|   attribute key             |  description                | optional |   notes                                                                        |
+=============================+=============================+==========+================================================================================+
|  user                       | The SSH username to use for | Yes      | Most implementations will leave this blank, causing Bcome to fallback to using |
|                             | SSH connections.            |          | the local terminal user's username as the SSH user. Setting a username within  |
|                             |                             |          | will override this.                                                            | 
+-----------------------------+-----------------------------+----------+--------------------------------------------------------------------------------+ 
|  proxy                      | An array of proxies         | Yes      | If proxies are configured, Bcome will craft an SSH connection jumping through  |
|                             |                             |          | each proxy in the order in which they are declared in the proxy array, position|
|			      |				    |	       | 0 being first hop.                                                             |
|			      |				    |	       |										|
|			      |				    |	       |							                        |
|			      |				    |	       | If a proxy is a Bcome node, its public_ip_address will be used to route        |
|		              |				    |          | the connection if present.  If there is no public_ip_address available, Bcome  |
|			      |				    |	       | will default to using the node's internal_ip_address to route the connection.  |
|   		  	      |				    |	       |									        |
|			      |			            |	       | Using this pattern you may proxy via multiple hops into your networks.         |
|			      |				    |	       |									        |
|			      |			            |	       | See :ref:`PROXY_ATTRS`.	    		   	                        |
+-----------------------------+-----------------------------+----------+--------------------------------------------------------------------------------+

.. _PROXY_ATTRS:

Proxy Attributes
^^^^^^^^^^^^^^^^

Used to define an SSH Proxy.

See the full list of configurable attributes here:

+-----------------------------+-----------------------------+----------+--------------------------------------------------------------------------------+
|                             |                             |          |                                                                                |
|   attribute key             |  description                | optional |   notes                                                                        |
+=============================+=============================+==========+================================================================================+
|  host_lookup  	      | The type of host lookup to  | No       | Permitted values are: 'by_bcome_node',  'by_host_or_ip' or                     |
|                             | perform.                    |          | 'by_inventory_node'.								|
|			      |			            |	       |										|
|			      |				    |	       | Note that 'by_host_or_ip' must be used to reference proxies without public     |
|		              |				    |	       | interfaces.                                                                    |
+-----------------------------+-----------------------------+----------+--------------------------------------------------------------------------------+
|  namespace                  | A bcome node                | Yes      | Required for host_lookup type 'by_bcome_node'. Allows for referencing    	|
|  			      | in breadcrumb format, e.g.  |	       | proxy machines that can be defined anwywhere within the Bcome installation.	|
|			      | node_key:node_key           |	       | 										|
+-----------------------------+-----------------------------+----------+--------------------------------------------------------------------------------+
|  host_id		      | A hostname or ip address, or| Yes      | Required for host_lookup type 'by_host_or_ip'.					|
|  			      | reference to a host from    |          | 										|
| 			      | your ssh config or hosts    |          |										|
|			      |	file.                 	    |          |										|
|			      |				    |	       |										|
|		              |	In other words, anything    |	       |										|
|                             | that your underlying OS can |	       |										|	
| 			      | resolve as an SSH target    |	       |										|
+-----------------------------+-----------------------------+----------+--------------------------------------------------------------------------------+	
|  node_identifier            | The name of the node within | Yes      | Required for host_lookup type 'by_inventory_node'.                             |
|                             | the same Inventory that you |          |                                                                                |
|                             | wish to declare as your SSH |          | 									        |
|                             | proxy machine.              |          | 									        |
+-----------------------------+-----------------------------+----------+--------------------------------------------------------------------------------+
|  bastion_host_user          | The ssh username to be used | Yes      | Default to the Bcome installation's local SSH username.		        |
|                             | for bypassing the proxy.    |          | 										|
+-----------------------------+-----------------------------+----------+--------------------------------------------------------------------------------+
