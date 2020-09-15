.. meta::
   :description lang=en: The @node namespace object

.. include:: ../urls.rst

*****
@node
*****

``@node`` is an instance of a namespace (see: :doc:`../core-concepts/namespaces`). 

* Whenever you’re in a Console session, you are in the scope of an instance of @node.

* When you use Keyed Access to key into a namespace, the last namespace key will reference an instance of @node.

* An instance of @node is made available to you within your orchestration scripts.

@node is the Ruby object that encapsulates the current namespace. 

.. note::

   See :doc:`../usage/navigation` for the difference between the Console and Keyed-access.

Interacting with @node
----------------------

You may directly interact with @node as follows:

* By invoking Menu commands (see: :doc:`../usage/command-menu`).
* By invoking custom Registry tasks (see: :doc:`../registry/overview`)
* By accessing public-instance methods made available by the framework (see :doc:`../usage/node-methods`)
