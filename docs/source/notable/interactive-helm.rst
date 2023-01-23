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

Additional system requirements
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You will need ``helm`` installed and in PATH.

Usage
^^^^^

Invoke ``helm`` on any Kubernetes Cluster or Namespace node and you will be presented with a shell.  Any commands you enter here will be delegated to ``helm``, in the context of the Cluster or Cluster Namespace on which it was invoked.

You won't need to enter 'helm' when you pass commands in the resulting subshell, e.g. rather than 'helm ls' you can just enter 'ls'. Similarly, when you're in the context of a Cluster Namespace you won't have to enter "-n namespace", this also being managed for you by the framework.

.. hint::

  For guidance on how to execute commands, see :doc:`../usage/executing-commands`
