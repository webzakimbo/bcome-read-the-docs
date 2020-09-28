.. include:: ../urls.rst

.. meta::
   :description lang=en: Bcome orchestration: Registry configuration file - registry.yml

***************************
Registry Configuration File
***************************

The Registry is configured with a configuration file named 'registry.yml', that is placed in your 'bcome' configuration directory, as follows:

.. code-block:: bash

   .
   └── project
       └── bcome
           └── registry.yml


The YAML configuration is a simple Hash structure representing an Array of script declarations, each one keyed on a Regular expression intended to match a specific Bcome namespace breadcrumb pattern.

.. code-block:: yaml

   ---
    (regular)expression.+:
      - array
      - of
      - available
      - scripts

    (another|pattern)tomatch?:
      - another
      - list
      - of
      - scripts

Within Bcome, any namespace with a breadcrumb pattern matching a given Registry declaration's regular expression, will have that script available to it.

Let's imagine you had the following namespace structure:

.. code-block:: bash

   .
   └── estate
       ├── aws
       │   ├── dev
       │   │   └── app_servers
       │   └── prod
       │       └── app_servers
       └── gcp
           ├── dev
           │   └── app_servers
           └── prod
               └── app_servers

And let's say you need to associate an orchestration script with every 'app_server' inventory.

Your regular expression could look as follows:

.. code-block:: yaml

   ---
   (aws|gcp):(dev|prod):app_servers
   ...

.. note::

   The root namespace name ('estate' in the example above) is always implicit in registry declarations.

For information & examples on configuring scripts, see :doc:`registry-examples`.  Our |GUIDES|_ site also has example configurations.

