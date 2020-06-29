.. meta::
   :description lang=en: Bcome - create your project structure

*****************************
Create your project structure
*****************************

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

Now create a directory for your configuration:

.. code-block:: bash

   mkdir bcome

And within your configuration directory prep the yaml file within which your network configuration will live:

.. code-block:: bash

   cd bcome
   touch networks.yml

Your project directory should now look as follows:

.. code-block:: bash

   .
   ├── Gemfile
   └── bcome
       └── networks.yml
