---
layout: default
title: Publishing in Solr
parent: Helpful Resources
nav_order: 4
---


# Publishing Metadata in Solr
{: .no_toc }

How to publish metadata records in Solr for GeoBlacklight integration
{: .fs-6 .fw-300 }

---
---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Adding Metadata Records to Solr

Metadata for GeoBlacklight instances is stored and indexed in Solr. The Solr application identifies each metadata record as a “document.” The process of adding documents to Solr is called “indexing.” 

**Option A: Manually indexing**

If you have access to your Solr Dashboard panel, you can add records manually by pasting them into the Documents pane.

**Option B: Indexing via scripts**

It is often more practical to use a process for batch adding, updating, and deleting the records. Most of the available processes are in the form of command-line scripts. See [Scripts and Tools](../../helpful-resources/scripts-and-tools) for examples.

## Viewing Solr Metadata within GeoBlacklight

The raw metadata files can be viewed by appending terms to the end of an item's show page URL.

### .xml
{: .no_toc }

* produces a Dublin Core XML document in the [OAI_DC schema](https://www.openarchives.org/OAI/2.0/oai_dc.xsd). The fields for this document can be adjusted in the `solr_document.rb`, which is found here: `app/models/solr_document.rb`. Example: https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677.xml.

### .json
{: .no_toc }

* GeoBlacklight until version 1.9: produces a full metadata file for the item as a flat JSON document.
* GeoBlacklight 2.0+: produces a nested JSON document of the metadata that appears on the item page. This document can be harvested by the [JSON:API](https://jsonapi.org/) protocol.

### /raw
{: .no_toc }

* GeoBlacklight until version 1.9: not available.
* GeoBlacklight 2.0+: displays the full metadata file for the item as a flat JSON document.