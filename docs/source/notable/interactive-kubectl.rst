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

Invoke ``kubectl`` on any Kubernetes Cluster node and you will be presented with a shell. Any commands you enter will be delegated to kubectl, in the context of the Cluster or Cluster Namespace on which it was invoked.

You won't need to enter 'kubectl' when you pass commands in the resulting subshell, e.g. rather than 'kubectl get pods' you can just enter 'get pods'. Similarly, when you're in the context of a Cluster Namespace you won't have to enter "-n namespace", this also being managed for you by the framework.

.. hint::

  For guidance on how to execute commands, see :doc:`../usage/executing-commands`
