---
layout: default
title: Publishing in Solr
parent: Resources
nav_order: 3
---

# Publishing Metadata in Solr
{: .no_toc }

How to publish metadata records in Solr for GeoBlacklight integration
{: .fs-6 .fw-300 }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Unique keys

Metadata for GeoBlacklight instances is stored and indexed in Solr, which uses a "Unique Key Field" as the identifier for each document. The OGM Aardvark schema was designed with `id` as the Unique Key Field (in GBL 1.0, this field was called `layer_slug_s`). Each item must have a unique key.

## Suffixes
{: .no_toc }

Solr uses the suffix of a metadata element to determine what kind of field it is. The following suffixes are part of the OGM Aardvark schema and may be used by custom fields, too (for a full list of spatial field types and their suffixes, see [this code](https://github.com/geoblacklight/geoblacklight/blob/main/solr/conf/schema.xml#L14)):

| Field Suffix | Type                     | Description                     | Example   |
|:-------------|:-------------------------|:--------------------------------|:----------|
| `_b`         | Boolean                  | Values can be `true` or `false` | `gbl_georeferenced_b`|
| `_im`        | Integer, multivalued     | Digits                          | `gbl_indexYear_im`|
| `_drsim`     | Date range, multivalued  | Date range in a specified string format: "[1980 TO 1995]" | `gbl_dateRange_drsim` |
| `_dt`        | Date                     | Date and time in a specified string format: "YYYY-MM-DDThh:mm:ssZ" | `gbl_mdModified_dt`|
| `_s`         | String                   | Single string of text           | `dct_title_s` |
| `_sm`        | String, multivalued      | Multiple strings of text        | `dct_subject_sm` |

Altering suffixes can result in metadata schema incompatibilities across institutions. Any deviations in element names causes Solr to treat the elements as separate fields: for example `dct_subject_s` and `dct_subject_sm` would be stored separately. If GeoBlacklight is set up to display a facet for `dct_subject_s`, it will not pick up values stored in `dct_subject_sm` in the filter. Therefore, if you are gathering metadata from other institutions, make sure to inspect their metadata fields to determine if there will be inconsistencies in your Solr index.


## Add metadata records to Solr

Metadata for GeoBlacklight instances is stored and indexed in Solr. The Solr application identifies each metadata record as a “document.” The process of adding documents to Solr is called “indexing.”

**Option A: Manually indexing**

If you have access to your Solr Dashboard panel, you can add records manually by pasting them into the Documents pane.

**Option B: Indexing via scripts**

It is often more practical to use a process for batch adding, updating, and deleting the records. Most of the available processes are in the form of command-line scripts. See [Scripts and Tools](scripts-and-tools) for examples.

## View Solr metadata within GeoBlacklight

The raw metadata files can be viewed by appending terms to the end of an item's show page URL.

### .xml
{: .no_toc }

* Produces a Dublin Core XML document in the [OAI_DC schema](https://www.openarchives.org/OAI/2.0/oai_dc.xsd). The fields for this document can be adjusted in the `solr_document.rb`, which is found here: `app/models/solr_document.rb`.
* Example: [https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677.xml](https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677.xml)

### .json
{: .no_toc }

* GeoBlacklight until version 1.9: produces a full metadata file for the item as a flat JSON document.
* GeoBlacklight 2.0+: produces a nested JSON document of the metadata that appears on the item page. This document can be harvested by the [JSON:API](https://jsonapi.org/) protocol.

### /raw
{: .no_toc }

* GeoBlacklight until version 1.9: not available.
* GeoBlacklight 2.0+: displays the full metadata file for the item as a flat JSON document.
