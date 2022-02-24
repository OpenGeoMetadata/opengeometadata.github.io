---
layout: default
title: How to Transform Metadata
parent: Helpful Resources
nav_order: 2
---

# How to Transform Metadata
{: .no_toc }

subtitle
{: .fs-6 .fw-300 }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Heading

Description
Step 2 of the metadata workflow is to convert or transfer information from some or all of the fields to the GeoBlacklight schema.  The result of this process is one or more JSON files that will be parsed and indexed by Solr.  These JSON files will serve as the content to be shown in the GeoBlacklight application.

From the previous section on authoring metadata, a finished metadata file could look like the following example in ISO 19139 format:

![ISO Metadata ](images/ISO_snippet.png)

The process of transforming metadata from the above formats to the GeoBlacklight schema involves mapping or “crosswalking” fields from one format to another.

![ISO to GBL Crosswalk](images/ISO-GBL.jpg)


Most institutions have their own unique set of tools and workflows to perform this transformation.  These workflows may differ depending on the type of item to be referenced.  In most cases, automation of this process is desired although technically, the JSON files could be created manually.

The process, whether automated or manual, typically involves parsing the existing metadata record, extracting the values from selected fields and inserting the value into a new JSON document under the corresponding GeoBlacklight schema field.  In most cases the values can simply be copied over as is, although some additional formatting may be necessary.

Helpful reminders:

* The JSON files in the GeoBlacklight schema do not need to be stored with the data/items they are referencing.
* Multiple items can be referenced in a single JSON file.
* Some fields will contain the same values for each item (e.g. “Schema Version”)
