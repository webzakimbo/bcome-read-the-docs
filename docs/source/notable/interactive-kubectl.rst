.. meta::
   :description lang=en: Bcome usage: Contextual & Interactive kubectl shell

.. include:: ../urls.rst

*******************
Interactive Kubectl
*******************

Overview
^^^^^^^^

Interactive Kubectl allows you to access a ``kubectl`` shell scoped to a particular Kubernetes Cluster or Namespace.

* No need to set or change contexts
* Bcome manages your kubeconfig
* Handle multiple clusters at once, irrespective of origin (EKS, GCP etc)
* Interact with multiple clusters at once from orchestration scripts

Additional system requirements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You will need ``kubectl`` installed and in PATH.

Usage
^^^^^

Invoke ``kubectl`` on any Kubernetes Cluster node.

.. hint::

  For guidance on how to execute commands, see :doc:`../usage/executing-commands`


Any commands you enter will be passed directly to Kubectl.

