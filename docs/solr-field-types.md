---
hide:
  - toc
---

## Unique keys

Metadata for GeoBlacklight instances is stored and indexed in Solr, which uses a "Unique Key Field" as the identifier for each document. The OGM Aardvark schema was designed with `id` as the Unique Key Field (in GBL 1.0, this field was called `layer_slug_s`). Each item must have a unique key.

## Suffixes


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

