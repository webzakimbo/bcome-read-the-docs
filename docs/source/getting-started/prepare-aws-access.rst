.. include:: urls.rst

.. meta::
   :description lang=en: Preparing an AWS account authorization for Bcome.

*****************
AWS authorization
*****************

AWS authorization is achieved by linking an AWS IAM user with your local instance of the Bcome client.

If you want to integrate an AWS account, then follow the steps here. 

.. note::

   You may connect as many AWS accounts as you like, and mix with as many accounts from other cloud providers. 

   Bcome will allow you to interact with them all in the same project.

Create directory structure
==========================

Create a directory named ``.aws`` in the root of your project directory.

If you've correctly setup your project directory structure (see: :doc:`create-project-structure`), your directory structure should now look like::

   .
   ├── .aws
   ├── Gemfile
   └── bcome
       └── networks.yml


Generate an AWS access key and secret access key
------------------------------------------------

From within your chosen AWS account, generate a secret key and secret access key for the IAM user you wish to link to Bcome.  This IAM user should have:

- Programmatic access to the AWS API
- As minimum, an associated policy of ``AmazonEC2ReadOnlyAccess``

Have a look here_ for an AWS guide on how to do this.

.. _here: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html

The Bcome framework will use this key & secret in order to conduct queries against Amazon's EC2 API.  This allows Bcome to populate your instance with resources from your account.

.. note::

   If you add custom orchestration to Bcome that requires access to features other than EC2, you will of course need to augment the permissions available to your IAM user.

Add the AWS keys to your bcome project
---------------------------------------

Create a file named ``keys`` in your .aws directory

Within this file, create a key to reference your AWS account e.g. my_key

And then within your keys file add in the following yaml:

.. code-block:: json

   ---
   my_key:
      aws_access_key_id: [your access key]
      aws_secret_access_key: [your secret access key]

.. warning::

  Do not commit your ``keys`` file to source control.


Configuring multiple AWS accounts
---------------------------------

You can add as many AWS accounts as you like. This allows you to work with machines from disparate accounts within the same project.

Given a second AWS account referenced by the key 'my other key', your keys file would look as follows:

.. code-block:: json

   ---
   my_key:
     aws_access_key_id: [your access key]
     aws_secret_access_key: [your secret access key]
   my_other_key:
     aws_access_key_id: [second access key]
     aws_secret_access_key: [second secret access key]

.. note::

   For a demonstration of an AWS authorization in use, please see the |AWS_AUTH_GUIDE|_

   For a full list of namespace attributes, which will help you utilise your AWS authorization within your project, see :doc:`../core-concepts/network-configuration.html`

