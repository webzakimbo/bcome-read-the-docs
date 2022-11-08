.. include:: ../urls.rst

.. meta::
   :description lang=en: Adding a Google Cloud Platform (GCP) authorisation - OAuth 2.0 or a Service Account - to your Bcome installation.

************************
Adding GCP authorisation
************************

GCP authorisation may be achieved either via :ref:`O_AUTH_2_0`, and/or by directly linking a :ref:`SERVICE_ACCOUNT`.

If you want to integrate a GCP account, then follow the steps here.

.. note::

   You may connect as many GCP accounts as you like (using a mix of OAuth 2.0 & Service Account authorisation), and mix with as many accounts from other cloud providers. 

   Bcome will allow you to interact with them all in the same project.

Create directory structure
==========================

For both ``OAuth 2.0`` and ``Service account`` authorisation methods, ensure you have a directory named ``.gauth`` in the root of your project directory.

You haven't already done so, run ``bcome init`` to setup your project directory structure. For more information see :doc: `../getting-started/setting-up-your-project`.

See also :doc: `create-project-structure`.

.. warning::

  Do not commit any files within your .gauth directory to source control.  Your OAuth 2.0 & ServiceAccount secrets will live here, as well as any access tokens returned from GCP when OAuth 2.0 is in use. 


.. _O_AUTH_2_0:

OAuth 2.0
=========

Your own OAuth 2.0 Application
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To integrate OAuth 2.0 with Bcome, you'll need to create a client id and secret.  To do this, follow these steps:

* Login to your |GCP_CONSOLE|_
* From your projects list select your project (or create a new one)
* Go to APIs & Services
* Go to Credentials
* Select Create Credentials, then select OAuth client id
* Under ``Application Type`` select ``Desktop app`` (previously this was 'other')
* Under ``Name``, enter a name for your Oauth client application.
* Hit ``Create``

.. note::

  If you are prompted to create an OAuth consent screen, you will only need to do so with the minimal required settings of App Name, User Support Email, and Developer Email Address.

Next, make a note of the ``Client Id`` and ``Client Secret`` then in your .gauth directory create a file named .gauth/your-secrets-file.json and add the following contents:

.. code-block:: json

   {
     "installed":
     {
       "client_id": "Your client id",
       "client_secret": "Your client secret",
       "type": "authorized_user"
     }
   }

If you forgot to make a note of the Client Id and Client Secret, then:

* Login to you |GCP_CONSOLE|_
* From your projects list select your project
* Go to APIs & Services
* Go to Credentials
* Select your OAuth 2.0 Client application
* Select ``Download JSON``

Save this file to your .gauth directory as .gauth/your-secrets-file.json.  This file may differ slightly in structure to that suggested above, but it will be compatible.

.. note::

  Your .gauth/your-secrets-file.json can be called anything you like. You'll reference this file later on when you add your authorisation to your network configuration.

  Bcome supports multiple GCP authorisations at the same time (either for different GCP accounts, or for different projects within the same account), and you would integrate these by adding a secrets file per GCP project to your .gauth directory.

.. warning::

   Don't commit your secrets file to source control! 

As a final step, visit |GCP_COMPUTE_API|_ and hit ``ENABLE`` to enable the Compute Engine API.  

.. permissions::

   Your OAuth 2.0 users will need as minimum the ``compute.instances.list`` permission.

.. _SERVICE_ACCOUNT:

To make use of this mechanism in your network.yml file, your configuration would look as follows:

.. code-block:: yaml

   ---
   parent:child:
     type: collection
     description: Example custom OAuth application

     network:
       type: gcp
       project: YOUR_PROJECT_NAME
       authentication_scheme: oauth
       secrets_filename: YOUR_SECRETS_FILE_NAME.json
       service_scopes:
       - https://www.googleapis.com/auth/compute.readonly
       - https://www.googleapis.com/auth/cloud-platform

For more information on your networks.yml file, see here: :doc:`../core-concepts/nodes`.

OAuth using application default credentials
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You can authorise with OAuth using Google's default OAuth application if you don't want to setup your own.

Assuming you've run ``bcome init`` you'll see the following file in your ``.gauth`` directory:

.. code-block:: bash

   .gauth
    └── googles-not-so-secret-client-secrets.json


This is Google's default Oauth credentials for GCP.  This file, as the name suggests, is not-so-secret - it's packaged along with the ``gcloud`` distribution, and is what the gcloud binary uses in its authorisation process.  Authorising with this will instruct the framework to authenticate and authorise you in an OAuth loop against Google's default OAuth application.

To make use of this mechanism in your networks.yml file, your configuration would look as follows:

.. code-block:: yaml

   ---
   clusters:
     type: collection
     description: A collection making use of default Google Oauth
     network:
       type: gcp
       authentication_scheme: oauth
       secrets_filename: googles-not-so-secret-client-secrets.json
       service_scopes:
       - openid
       - https://www.googleapis.com/auth/userinfo.email
       - https://www.googleapis.com/auth/cloud-platform
       - https://www.googleapis.com/auth/appengine.admin
       - https://www.googleapis.com/auth/compute
       - https://www.googleapis.com/auth/accounts.reauth


Note that you will still need to require defined service scopes, as above.

For more information on your networks.yml file, see here: :doc: `../core-concepts/nodes`.

Service Account
===============

Service Account authorisation requires credentials in JSON format.

* Follow this guide here in order to create your credentials: |GCP_SERVICE_ACCOUNT_CREDS_HOW_TO|_ 
* Download the credentials file in JSON format and save it to your .gauth directory. Your file will look something like this:

.. code-block:: yaml

   {
     "type": "service_account",
     "project_id": "your project id",
     "private_key_id": "your private key id",
     "private_key": "your private key",
     "client_email": "your client email",
     "client_id": "your client id",
     "auth_uri": "https://accounts.google.com/o/oauth2/auth",
     "token_uri": "https://oauth2.googleapis.com/token",
     "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
     "client_x509_cert_url": "your client x509 cert url"
   }


Save your service account credentials json file to your .gauth directory under any name you like. You'll reference this file later on in your networks.yml configuration file.

.. note::

   For demonstrations of GCP authorisation in use, please see our guides:  |GCP_OAUTH_GUIDE|_ / |GCP_AUTH_SA_GUIDE|_.

.. hint::

   To add your GCP authorisation to your network configuration, see :doc:`../core-concepts/network-configuration`.

To make use of this mechanism in your network.yml file, your configuration would look as follows:

.. code-block:: json

   ---
   parent:child:
     type: collection
     description: Service account authorisation
  
     network:
       type: PROJECT_NAME
       project: wbznet
       authentication_scheme: oauth
       service_scopes:
       - https://www.googleapis.com/auth/compute.readonly
       - https://www.googleapis.com/auth/cloud-platform
       service_account_credentials: YOUR_SERVICE_ACCOUNT_CREDENTIALS.json

For more information on your networks.yml file, see here: :doc:`../core-concepts/nodes`.
