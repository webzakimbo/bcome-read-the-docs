.. include:: ../urls.rst

.. meta::
   :description lang=en: Preparing a GCP account for Bcome: OAuth 2.0 or Service Account authorisation

*****************
GCP authorization
*****************

GCP authorisation may be achieved either via :ref:`O_AUTH_2_0`, and/or by directly linking a :ref:`SERVICE_ACCOUNT`.

If you want to integrate a GCP account, then follow the steps here.

.. note::

   You may connect as many GCP accounts as you like (using a mix of OAuth 2.0 & Service Account authorisation), and mix with as many accounts from other cloud providers. 

   Bcome will allow you to interact with them all in the same project.

Create directory structure
==========================

For both ``OAuth 2.0`` and ``Service account`` authorisation methods, create a directory named ``.gauth`` in the root of your project directory.

If you've correctly setup your project directory structure (see: :doc:`create-project-structure`), your directory structure should now look like::

   .
   ├── .gauth
   ├── Gemfile
   └── bcome
       └── networks.yml

.. _O_AUTH_2_0:

OAuth 2.0
=========

To integrate OAuth 2.0 with Bcome, you'll need to create a client id and secret.  To do this, follow these steps:

* Login to your |GCP_CONSOLE|_
* From your projects list select your project (or create a new one)
* Go to APIs & Services
* Go to Credentials
* Hit New Credentials, then select OAuth client id
* Under ``Application Type`` select ``Other``
* Under ``Name``, enter a name for your Bcome console installation.
* Hit ``Create``

Make a note of the ``Client Id`` and ``Client Secret`` then in your .gauth directory create a file named .gauth/your-secrets-file.json and add the following contents:

.. code-block:: json

   {
     "installed":
     {
       "client_id": "Your client id",
       "client_secret": "Your client secret",
       "type": "authorized_user"
     }
   }

.. note::

  Your .gauth/your-secrets-file.json can be called anything you like. You'll reference this file later on in your networks.yml configuration file.  

  Bcome supports multiple GCP accounts at the same time (either for different GCP accounts, or for different projects within the same account), and you would integrate these by adding a secrets file per GCP project to your .gauth directory.

.. warning::

   Don't commit your secrets file to source control.

As a final step, visit |GCP_COMPUTE_API|_ and hit ``ENABLE`` to enable the Compute Engine API.  

.. permissions::

   Your OAuth 2.0 users will need as minimum the ``compute.instances.list`` permission.

.. _SERVICE_ACCOUNT:

Service Account
===============

Service Account authorization requires credentials in JSON format.

* Follow this guide here in order to create your credentials: |GCP_SERVICE_ACCOUNT_CREDS_HOW_TO|_ 
* Download the credentials file in JSON format and save it to your .gauth directory. Your file will look something like this:

.. code-block:: json

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

   For demonstrations of GCP authorization in use, please see our guides:  |GCP_OAUTH_GUIDE|_ / |GCP_AUTH_SA_GUIDE|_.

   For a full list of namespace attributes, which will help you utilise your GCP authorization within your project, see :doc:`../core-concepts/network-configuration`
