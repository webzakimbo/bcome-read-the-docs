.. meta::
   :description lang=en: Bcome usage: Contextual & Interactive Helm shell

.. include:: ../urls.rst

*****************
Interactive Helm
*****************

Overview
^^^^^^^^

Interactive Helm allows you to access a ``helm`` shell scoped to a particular Kubernetes Cluster or Namespace.

* No need to set or change kubectl contexts
* Bcome manages your kubeconfig
* Handle multiple clusters at once, irrespective of origin (EKS, GCP etc)
* Interact with multiple clusters at once from orchestration scripts


Usage
^^^^^

Invoke ``helm`` on any Kubernetes Cluster or Namespace node.  

.. hint::

  For guidance on how to execute commands, see :doc:`../usage/executing-commands`
