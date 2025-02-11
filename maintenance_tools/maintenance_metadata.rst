.. meta::
   :description: digiKam Maintenance Tool to Synchronize Metadata
   :keywords: digiKam, documentation, user manual, photo management, open source, free, learn, easy, maintenance, metadata, synchronizer

.. metadata-placeholder

   :authors: - digiKam Team

   :license: see Credits and License page for details (https://docs.digikam.org/en/credits_license.html)

.. _maintenance_metadata:

Metadata Synchronizer
=====================

.. contents::

.. figure:: images/maintenance_metadata_synchronizer.webp
    :alt:
    :align: center

    The digiKam Maintenance Options to Synchronize Metadata

This process synchronize items metadata with database contents. The operation **Direction** can be:

    - From the database to files.

    - From files to the database.

.. note::

    As synchronization is a time consuming process, especially when metadata are written in files, it's a good idea to restrict the job to certain albums or tags. 

The synchronization depends of the settings from :menuselection:`Settings --> Configure digiKam...` and **Metadata** page. All these settings is described in :ref:`the dedicated section <metadata_settings>` from **Setup Application**.

While the metadata synchronizer process is under progress, as the process may take much time and digiKam cannot be used, a non modal dialog appear to make sure that no database corruption occurs.

.. figure:: images/maintenance_metadata_process.webp
    :alt:
    :align: center

    The Metadata Synchronization Process Running in Background
