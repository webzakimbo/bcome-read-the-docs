.. meta::
   :description lang=en: Bcome orchestration: An overview of The Registry.

*****************
Registry Overview
*****************

The purpose of the Registry is to place custom method hooks directly onto your namespaces.  These method hooks are then surfaced within Bcome, and allow you to call custom functionality within the context of the namespaces associated with them.

Each Bcome namespace has its own Registry, the framework giving you a means of adding context-specific method hooks to your application.  It is in this way that you are able to build up unique (re-usable) interfaces on top of your namespaces.

.. note::

  The Registry is designed for reusability, and so you may associate the same tasks with different namespaces, DRY'ing up your code.

  Have a look also at the :doc:`../metadata/metadata-framework`. By associating context-specific data to your namespaces, the same Registry task re-used becomes way more powerful. 

Within any namespace in Bcome, invoke the ``registry`` method to view your available methods. 

For configuration, see :doc:`registry-configuration-file` and :doc:`registry-configuration-attributes`.

For examples see :doc:`registry-examples`.

For further information on Bcome's in-built commands see :doc:`../usage/executing-commands` and :doc:`../usage/command-menu`.

.. hint::

  Whilst providing convenience accessors for your orchestrative functions, adding Registry methods is the means with which you build up your installation into a self-documenting application tailored to your own requirements.

