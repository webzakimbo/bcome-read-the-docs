Some additional useful functions
--------------------------------

Prompt for a metadata decryption key:

.. code-block:: bash

   ::Bcome::Node::MetaDataLoader.instance.prompt_for_decryption_key

Silence command output:

.. code-block:: bash

   ::Bcome::Orchestrator.instance.silence_command_output!

Initiate an SSH connection to all server instances within a given namespace (rather than lazy-load them):

.. code-block:: bash

   # with a progress bar
   ::Bcome::Ssh::Connector.connect(namespace, show_progress: true)

   # without a progress bar
   ::Bcome::Ssh::Connector.connect(namespace, show_progress: false)
