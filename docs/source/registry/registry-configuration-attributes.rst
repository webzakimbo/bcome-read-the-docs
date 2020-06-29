.. meta::
   :description lang=en: Bcome orchestration: registry confuguration attributes 


*********************************
Registry Configuration Attributes
*********************************

Here you'll find the full list of attributes for your registry.yml file (see: doc:`registry-configiration-file`).

+--------------------------+---------------------------------------+---------------------------------------+
|                          |                                       |                                       |
|  attribute key           |  description                          |  optional                             |
+==========================+=======================================+=======================================+
|  type                    |  the type of Registry declaration:    |  No                                   |
|                          |  ``shortcut``, ``internal``, or       |                                       |
|                          |  ``external``.                        |                                       |
+--------------------------+---------------------------------------+---------------------------------------+
|  description             |  A description of your command.       |  No                                   |
|                          |                                       |                                       |
+--------------------------+---------------------------------------+---------------------------------------+
|  console_commad          |  The command to invoke within Bcome   |  No                                   |
|                          |  will invoke your Registry methiod    |                                       |
+--------------------------+---------------------------------------+---------------------------------------+
|  group                   |  A group name. All commands with the  |  No                                   |
|                          |  same group are grouped together when |                                       |
|                          |  Registry declarations are listed     |                                       |
+--------------------------+---------------------------------------+---------------------------------------+
|  shortcut_command        |  The remote command to execute when   |  Required for type ``shortcut``       |
|                          |  the script is invoked.               |                                       |
+--------------------------+---------------------------------------+---------------------------------------+
|  run_as_pseudo_tty       |  true OR false			   |  Optional for type ``shortcut`` only  |
+--------------------------+---------------------------------------+---------------------------------------+
|  orch_klass              |  Your orchestration class name.       |  Required for type ``internal``       |
+--------------------------+---------------------------------------+---------------------------------------+
|  local_command           |  The system command that is to be     |  Required for type ``external``       |
|                          |  executed locally.                    |                                       |
+--------------------------+---------------------------------------+---------------------------------------+
|  defaults                |  A Hash of optional values passed in  |  Optional for types ``external`` and  |
|                          |  to your local command.               |  ``internal``.                        |
|		           | 					   |				           |
|			   |  Available as ENV variables to        |                                       |
|			   |  external scripts, and from the       |                                       |
|			   |  @arguments Hash to internal scripts. |                                       |
+--------------------------+---------------------------------------+---------------------------------------+
|  restrict_to_node        |  Set to 'server', 'inventory'         |  Yes		                   |
|			   |  (all inventory types), or            |					   |
|		           |  'collection'.			   |					   |
|                          |           			           |                                       |
|			   |  Registry method will only be made    |                                       |
|			   |  available to namespaces of the       |                                       |
|			   |  declared type.			   |					   |
+--------------------------+---------------------------------------+---------------------------------------+

.. note::

   See :doc:`registry-configuration-file` for an introduction to the registry.yml configuration file.

