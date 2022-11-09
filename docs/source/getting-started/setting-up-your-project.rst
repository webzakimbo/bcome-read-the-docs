.. include:: ../urls.rst

.. meta::
   :description lang=en: Setting up your Bcome project.  How to install and initialize Bcome.

Installing and Initializing Bcome
=================================

.. note::

   Make sure you've read the installation requirements: :doc:`../getting-started/setting-up-your-project`.

   If you're new to Ruby, consider using |RVM_URL|_ to manage it.
  
Create a project directory:

.. code-block:: bash

   mkdir project
   cd project

Now install the |BCOME_GEM|_ manually:

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









