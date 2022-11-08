.. include:: ../urls.rst

.. meta::
   :description lang=en: Setting up your Bcome project.  How to install and initialize Bcome.

Installing and Initializing Bcome
=================================

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

   bcome init 

Your project directory should now look as follows:

.. code-block:: bash

  .
  ├── .aws
  ├── .gauth
  ├── .kubectl/
  ├── Gemfile
  └── bcome
      ├── k8_hierarchy.yml
      ├── metadata/
      ├── networks.yml
      ├── orchestration/
      └── registry.yml
