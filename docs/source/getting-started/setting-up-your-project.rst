.. include:: ../urls.rst

.. meta::
   :description lang=en: Setting up your Bcome project.  How to install and initialize Bcome.

Installing and Initializing Bcome
=================================

Create a project directory:

.. code-block:: bash

   mkdir project
   cd project

.. note::

   You've remembered to install Ruby 2.5 or greater, right?  

   Check out how to manage ruby with |RVM_URL|_.

Install the bcome gem, manually:

.. code-block:: bash

   gem install bcome

Or, via a Gemfile:

.. code-block:: bash

   # Gemfile contents. Place this in the root of your project directory.
   source 'https://rubygems.org'
   gem 'bcome'

Which you can then install via bundler:

.. code-block:: bash

   gem install bundler
   bundle install

Now run the initializer to create your configuration files & directories:

.. code-block:: bash

   bcome init 

Or if you've installed via bundler

.. code-block:: bash

   bundle exec bcome init

.. hint::

   It's better to use bundler and even better to alias ``bundle exec bcome`` in your $PATH to shorten how you invoke the framework.  I normally alias to just ``b``

If you've correctly set everything up, your project directory should now look as follows:

.. code-block:: bash

  .
  ├── .aws/
  ├── .gauth/
  │   └── googles-not-so-secret-client-secrets.json
  ├── .kubectl/
  └── bcome
      ├── k8_hierarchy.yml
      ├── metadata
      ├── networks.yml
      ├── orchestration
      └── registry.yml

Directory and config structure overview
=======================================

TODO









