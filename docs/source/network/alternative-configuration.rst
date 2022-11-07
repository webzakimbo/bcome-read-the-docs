.. meta::
   :description lang=en: Alternative Bcome network configurations using CONF= and ME=.

.. include:: ../urls.rst

*************************
Alternative configuration
*************************

Overriding network.yml with CONF=
=================================

If you want to use an alternative network configuration to the default file at

.. code-block:: bash

   .
   ├── Gemfile
   └── bcome
       └── networks.yml
  
then create your new configuration, e.g.

.. code-block:: bash

   .
   ├── Gemfile
   └── bcome
       └── networks.yml
       └── alternative-configuration.yml


To use your alternative file, set a reference to it using the CONF= environment variable when invoking Bcome, for example:

.. code-block:: bash

   CONF=bcome/alternative-configuration.yml bcome command

.. hint::

   Using the CONF environment variable is useful if you want to support different views of your infrastructure (e.g. providing views to teams based on role), 
   or if you want to provide access to multiple installations from the same project.


Ad-hoc overriding of network.yml with ME=
=========================================

You may already have seen how configuration may be inherited and overidden in Bcome (see :doc:`inheritance-and-overidding`).  

This can be also be done by referencing an overrides configuration file, and referencing it using the ME environment variable.

For example, consider the following Yaml configuration:

.. code-block:: yaml

   ---
   foo:bar:
     ssh_settings:
       user: "ubuntu"

Save it to the bcome/ configuration directory:

.. code-block:: bash

   .
   ├── Gemfile
   └── bcome
       └── networks.yml
       └── username-override.yml

You may now invoke it as follows:

.. code-block:: bash

   ME=bcome/username-override.yml bcome command

In the example given above this particular configuration override will override the ssh username for node "foo:bar".  You may override any configuration in this way.

This can be useful for

- Supporting a temporary configuration of an installation, for example in order to orchestrate a server installed with a bare operating system pre-bootstrapping, where only the default system users are present.
- Providing a local override for attributes

.. note::

   You can use both CONF= and ME= at the same time. CONF will load an alternative networks.yml configuration file, and ME will provide overrides. 

The me.yml configuration file
==============================

As well as setting an override using ME=, you may place the same contents in a file named me.yml, as follows:

.. code-block:: bash

   .
   ├── Gemfile
   └── bcome
       └── networks.yml
       └── me.yml

Contents in me.yml will be automatically loaded and used to override your Network configuration.

.. hint::

   This is the best way to provide your own personal override within collaborative projects.


Overriding an individual server's configuration
===============================================

To override an individual server's configuration, you must use a server-overrides.yml configuration file:

.. code-block:: bash

   .
   ├── Gemfile
   └── bcome
       └── networks.yml
       └── server-overrides.yml

For example, to override the connection details for 'server_a' within node 'foo:bar', your server-overrides.yml configuration would look as follows:

.. code-block:: yaml

   ---
   foo:bar:server_a:
     ssh_settings:
       user: a_different_username

.. note::

  Any server-specific overrides must be placed within the server-overrides.yml override file, and cannot be placed in the general or overriden network configuration.

