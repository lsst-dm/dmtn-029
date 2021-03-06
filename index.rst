..
  Technote content.

  See https://developer.lsst.io/docs/rst_styleguide.html
  for a guide to reStructuredText writing.

  Do not put the title, authors or other metadata in this document;
  those are automatically added.

  Use the following syntax for sections:

  Sections
  ========

  and

  Subsections
  -----------

  and

  Subsubsections
  ^^^^^^^^^^^^^^

  To add images, add the image file (png, svg or jpeg preferred) to the
  _static/ directory. The reST syntax for adding the image is

  .. figure:: /_static/filename.ext
     :name: fig-label
     :target: http://target.link/url

     Caption text.

   Run: ``make html`` and ``open _build/html/index.html`` to preview your work.
   See the README at https://github.com/lsst-sqre/lsst-technote-bootstrap or
   this repo's README for more info.

   Feel free to delete this instructional comment.

:tocdepth: 1
.. Please do not modify tocdepth; will be fixed when a new Sphinx theme is shipped.

.. sectnum::

.. Add content below. Do not include the document title.

.. note::

   **This technote is not yet published.**

The Scope of the Document
=========================

  This technical note documents a parallel procedure and tools developed for loading the SDSS/Stripe82 catalogs
  into PDAC Qserv. The catalogs were produced in a course of the LSST Summer 2013 Data Challenge effort
  which is covered in details at:

  - https://dev.lsstcorp.org/trac/wiki/Summer2013
  - https://confluence.lsstcorp.org/display/DM/Properties+of+the+2013+SDSS+Stripe+82+reprocessing

  Note that the current document won't provide any further explanation on how the catalogs were put together
  and prepared for the loading beyond the bare minimum info which is related to a location and a general
  structure of the input files used by the loading tools. The catalog preparation topics are fully covered
  in the following JIRA tickets:

  - https://jira.lsstcorp.org/browse/DM-6905 - Locate the test dataset for PDAC
  - https://jira.lsstcorp.org/browse/DM-7007 - Investigate coverage of S13 databases found so far
  - https://jira.lsstcorp.org/browse/DM-7053 - Assemble a complete database with S13 DRP catalog
  - https://jira.lsstcorp.org/browse/DM-7498 - Begin ingest of S13 DRP data to PDAC


Introduction
============

   Here be a brief overview of the loading procedure, tools (GitHub), etc.

Explain the environment
=======================

  - read-only GPFS
  - explain how to start/stop/inspect Qserv
  - explain where to find log files

Input datasets and configuration files
======================================

  - located on GPFS
  - explain what's found in there and how it was produced (links to the JIRA
    tickets explaining the merge procedure)

Tools needed
============

  - sudo yum installing required dependencies on the nodes
  - install stack
  - install a specific ticket & build it
  - replicate stack across all nodes

Configuring Qserv
=================

  - Creating database on all nodes and granting privileges
  - setting up WMGR secret file on all nodes
  - configuring CSS on Master
  - configuring MySQL in worker nodes - adding the database name to this table:

  .. code-block:: sql

    SELECT * FROM qservw_worker.Dbs;

  .. table:: Result set

    +------------------------+
    | db                     |
    +========================+
    | sdss_stripe82_00       |
    +------------------------+


Loading tables
==============

Non-partitioned tables
----------------------

  - a special case of _NoFile table

Deep Forced Sources
-------------------

  - the director table of the Qserv catalog
  - explain steps
  - explain the performance of the process


Deep Sources
------------

  - explain steps
  - explain the performance of the process

Testing
=======

  - log to the Master node
  - how to connect to the mysql-proxy process
  - queries

Cleaning up and starting from scratch
=====================================

  - explain all steps needed to reset Qserv





