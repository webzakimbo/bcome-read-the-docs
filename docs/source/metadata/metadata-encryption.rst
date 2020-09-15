.. meta::
   :description lang=en: Bcome Metadata Framework encryption.

Metadata Encryption
===================

Metadata files (see: :doc:`metadata-framework`) may be encrypted with a single key.  

This allows you to collaborate with others without sharing sensitive data directly (i.e. within your source control system).

The encryption process uses a symmetric block cipher, ``AES-256-ECB``

.. note::

   The use of AES-256-ECB will become deprecated in a future release with an intended upgrade to AES-256-CBC.  An upgrade path will be provided for already encrypted files.

Encryption commands
-------------------

Packing
^^^^^^^

Encryption is referred to as ``packing``.

To pack all your metadata files, invoke the following:

.. code-block:: bash

   bcome pack_metadata

You will be prompted for a Metadata key, which will be used to encrypt your data.

Should you now investigate your ``metadata`` directory, you will see that all your YAML files now have a ``.enc`` counterpart.

.. note:: 

   If any metadata YAML file already has a .enc counterpart, you will need to provide the same metadata key used to encrypt that file in order to pack all the others.

.. hint::

   Commit only your .enc files to source control, and create a workflow around Packing & Unpacking.

Unpacking
^^^^^^^^^

Decryption is referred to as ``unpacking``.

To unpack all your metadata files, invoke the following:

.. code-block:: bash

   bcome unpack_metadata

You will be prompted for the same key as was used to Pack your metadata originally.

.. warning::

   Should there be any differences between your .enc metadata files and their .yml counterparts during unpacking, you will prompted for confirmation before proceeding.

   The .yml files would otherwise be overwritten with the decrypted contents.

Metadata Diffs
^^^^^^^^^^^^^^

To see the differences between your encrypted metadata and unpacked metadata, use the following command:

.. code-block:: yaml

   bcome diff_metadata

Changing your encryption key
----------------------------

To change your encryption key:

* ensure that your unpacked yml metadata contain the correct contents
* remove all *.enc files
* re pack your metadata with a new key, using the ``pack_metadata`` command. 

