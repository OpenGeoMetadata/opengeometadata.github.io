---
layout: default
title: Fields
parent: OGM Metadata Basics
grand_parent: Helpful Resources
nav_order: 1
---

# Fields
{: .no_toc }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

See the [current schema](ogm-aardvark) for a full description of fields, expected values, and obligations.

## How fields are named

### Suffixes
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

## Fields related to identity

There are three fields that relate to a layer's identity.

**WxS Identifier**
<br>OGM Aardvark: `gbl_wxsIdentifier_s`
<br>GBL 1.0: `layer_id_s`

This field is used to identify the layer or store for a WFS, WMS, or WCS web service so GeoBlacklight can construct the full web service link. It should point to a specific layer within an OGC geospatial web service. This value is only used _when_ you have WxS services listed in your references field (`dct_references_s`). Examples:

* `sde:SDE_DATA.CI_F7PROVINCES_1995`
* `UCB:elev_100ft_polygon`
* `aa111bb2222 `

**ID**
<br>OGM Aardvark: `id`
<br>GBL 1.0: `layer_slug_s`

This field makes up the URL for the resource in GeoBlacklight. It is visible to the user and is used to create permalinks. The value should be alpha-numeric characters separated by dashes. If having a readable slug is desired, it is common to use the form `institution-keyword1-keyword2`. It should also be globally unique across all institutions in *your* GeoBlacklight index. Examples:

* `india-map`
* `stanford-andhra-pradesh-village-boundaries`
* `stanford-aa111bb2222`

**Identifier**
<br>OGM Aardvark: `dct_identifer_sm`
<br>GBL 1.0: `dc_identifier_s`

This is a general purpose field that can contain one or more persistent identifers or permalinks, as well as other identifiers like DOIs, catalog numbers, and/or other system numbers. It is not visible in the GeoBlacklight interface. Examples:

* `http://purl.stanford.edu/vr593vj7147`
* `http://hdl.handle.net/2451/34708`
* `urn:example.org:ad0e6ebc-824e-4450-a0d9-987f2232724f`
* `5864 .L7 E635 1998 .G7`

## Custom fields

If an organization wishes to implement a custom metadata field for their GeoBlacklight instance, the naming schema should reference the organization as follows: `organization_elementName_solrFieldType`.

Examples:
* `b1g_code_s` - Internal code that organizes items by their source collection
* `nyu_addl_dspace_s` - A 5 digit number that is the "internal identifier" for DSpace, the repository software that mints handles for all NYU's items. The internal id must be paired with the handle in order to post metadata and data via the system API.
