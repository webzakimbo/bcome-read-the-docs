.. meta::
   :description lang=en: Bcome orchestration: Registry method types

Registry method types
=====================

There are three types of Registry methods:

Shortcuts
---------

A shortcut references a command that you would otherwise invoke manually. 

The example below declares a shortcut to the command ``sudo puppetserver ca list --all`` made available via a method hook of ``list_certs``

.. code-block:: yaml

  ---
  gcp:(dev|prod):xops:puppet:
  - type: shortcut
    description: List certificates
    console_command: list_certs
    shortcut_command: "sudo puppetserver ca list --all"
    group: certificates

Any node with a breadcrumb matching the regular expression ``/gcp:(dev|prod):xops:puppet/`` would have the list_certs method hook available to it. 

Internal Hooks
--------------

An Internal Hook allows for the invoking of Internal ruby scripts. 

Below I declare a method hook to a custom orchestration class - ``SystemStatus``.  The node context in which the class is invoked would be made available to the orchestration script instance via the ``@node`` instance variable. 

.. code-block:: bash

   ---
   gcp:(dev|prod):app_servers:
   - type: internal
     description: "Web HTTP status"
     console_command: web_status
     group: status
     orch_klass: SystemStatus

Any node with a breadcrumb matching the regular expression ``/gcp:(dev|prod):app_servers/`` would have the 'web_status' method hook available to it.

See :doc:`../orchestration/internal-ruby-scripting` for information on how to write your internal scripts.

.. note::

   The full orchestration class node is not passed to the orch_klass parameter - only the class name.

Passing arguments
^^^^^^^^^^^^^^^^^

Internal Hook invocations may be passed arguments (see :doc:`registry-configuration-attributes`) when called in Keyed-Access mode (see: :doc:`../usage/navigation`).

For example, should you wish to pass an argument 'foo' with a value of 'bar' to the Internal script above for node 'gcp:prod:app_servers' you would invoke the following:

.. code-block:: bash

   bcome gcp:prod:app_servers:web_status foo=bar   

To pass in multiple arguments, you could invoke the following:

.. code-block:: bash

   bcome gcp:prod:app_servers:web_status first=value second=othervalue

Within your internal script, your arguments are made available to you within the ``@arguments`` variable.

External Hooks
--------------

An External Hook allows for the invoking of :doc:`../orchestration/external-ruby-scripting`

Below I declare a method hook to call a capistrano deployment script.

.. code-block:: yaml

   ---
   "(aws|gcp):(prod|dev):wbzsite(:.+)?":
   - type: external
     description: "Deploy web application"
     console_command: deploy
     group: deployment
     local_command: bundle exec cap wbz_frontend deploy build=%build%
     defaults:
       build: "master"

When declaring a method hook to an external script, Bcome will append an environment variable named ``bcome_context`` to the command.  This allows you to link your external script to the node context in which it was called.

The node context
^^^^^^^^^^^^^^^^^^^^^

If you invoked the method hook above as follows:

.. code-block:: bash

   bcome gcp:prod:wbzsite:deploy

Bcome would execute the following command:

.. code-block:: bash

   bcome_context="gcp:prod:wbzsite" bundle exec cap wbz_frontend deploy build=master 

Within your external script you would load your node context as follows:

.. code-block:: bash

   require 'bcome'

   orchestrator = ::Bcome::Orchestrator.instance
   node = ORCH.get(ENV["bcome_context"])

   ...

Passing arguments
^^^^^^^^^^^^^^^^^

External Hook declarations may be configured to take arguments (see :doc:`registry-configuration-attributes`).  

This is achieved using placeholders delineated with ``%``.  For example should you wish to add 'foo' as an argument attribute to command 'my/command', such that it would be executed as follows - 

.. code-block:: bash

   my/command foo=value

You would define your 'local_command' attribute within your external hook declaration as follows:

.. code-block:: bash

   ---
   local_command: my/command foo=%foo%

And you would set a default value for foo:

.. code-block:: bash

   ---
   local_command: my/command foo=%foo%
   defaults:
     foo: value

Any command argument is made available to your External script as an environnent variable. For example, to load your 'foo' argument within your script:

.. code-block:: bash

   foo = ENV['foo']

