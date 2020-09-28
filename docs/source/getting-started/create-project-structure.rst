.. meta::
   :description lang=en: Create your Bcome project structure

***************
Getting Started
***************

Create your project structure
=============================

Create a project directory:

.. code-block:: bash

   mkdir project
   cd project
   
Install the bcome gem, manually:

.. code-block:: bash

   gem install bcome

Or, via a Gemfile:

.. code-block:: bash

   source 'https://rubygems.org'
   gem 'bcome'

Which you can then install via bundle:

.. code-block:: bash

   bundle install

Now run the initializer to create your configuration files & directories:

.. code-block:: bash

  init-bcome

Your project directory should now look as follows:

.. code-block:: bash

  .
  ├── .aws
  ├── .gauth
  ├── Gemfile
  └── bcome
      ├── metadata
      ├── networks.yml
      ├── orchestration
      └── registry.yml


Populate your networks.yml configuration
========================================

Once you've created your project structure, the next step is to populate you networks.yml configuration file with your namespace structure.

See :doc:`../core-concepts/network-configuration` for further information.

