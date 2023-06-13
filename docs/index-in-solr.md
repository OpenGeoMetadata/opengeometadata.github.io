# Index Metadata in Solr

!!! note

	This page is a work in progress and needs more information.

Metadata records must be indexed in Solr in order to integrate with GeoBlacklight. The Solr application identifies each metadata record as a “document.” The process of adding documents to Solr is called “indexing.”

## Option A: Indexing manually

If you have access to your Solr Dashboard panel, you can add records manually by pasting them into the Documents pane.

## Option B: Indexing via scripts

It is often more practical to use a process for batch adding, updating, and deleting the records. Most of the available processes are in the form of command-line scripts. See the [Metadata Scripts](../scripts) for examples.
