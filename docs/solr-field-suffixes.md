---
hide:
  - toc
---

# Solr Field Suffixes

The following suffixes are part of the OGM Aardvark schema and may be used by custom fields. 

| Field Suffix | Type                     | Description                     | Example   |
|:-------------|:-------------------------|:--------------------------------|:----------|
| `_b`         | Boolean                  | Values can be `true` or `false` | `gbl_georeferenced_b`|
| `_im`        | Integer, multivalued     | Digits                          | `gbl_indexYear_im`|
| `_drsim`     | Date range, multivalued  | Date range in a specified string format: "[1980 TO 1995]" | `gbl_dateRange_drsim` |
| `_dt`        | Date                     | Date and time in a specified string format: "YYYY-MM-DDThh:mm:ssZ" | `gbl_mdModified_dt`|
| `_s`         | String                   | Single string of text           | `dct_title_s` |
| `_sm`        | String, multivalued      | Multiple strings of text        | `dct_subject_sm` |

!!! tip

	For a full list of spatial field types and their suffixes used in GeoBlacklight, see [https://github.com/geoblacklight/geoblacklight/blob/main/solr/conf/schema.xml#L14](https://github.com/geoblacklight/geoblacklight/blob/main/solr/conf/schema.xml#L14).


