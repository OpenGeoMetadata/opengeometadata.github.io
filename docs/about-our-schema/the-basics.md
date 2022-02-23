---
layout: default
title: The Basics
parent: About Our Schema
nav_order: 2
---

# The Basics
{: .no_toc }

How OGM metadata is structured
{: .fs-6 .fw-300 }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Overview

The OGM metadata schema is designed for GIS resource discovery and focuses mainly on discovery use cases. Text search, faceted search and refinement, and spatial search and relevancy are among the primary features that the schema enables. It:

* is based on [Dublin Core](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/), with custom elements added for spatial values
* is designed for discovery - to help users _find_ items
* is not designed for complete technical documentation, such as a GIS dataset's processing history
* includes elements for external links, such as downloads, web services, or supplemental metadata
* requires records to be formatted as JSON files

## Layers

The schemas are organized around "layers" as the unit of description. Each layer corresponds to a single set of data that can be described, downloaded, and (often) previewed. For example, this shapefile of [census boundaries](https://earthworks.stanford.edu/catalog/stanford-rf385pb1942) is considered a single layer in GeoBlacklight.

"A layer is a specific unit of data that contains a set of geospatial features, a metadata description, and a feature catalog. For example, a census layer would have the geometries of census tracts and the demographic results within each tract." [(Hardy and Durante 2014)](http://journal.code4lib.org/articles/9710)

## Unique Keys

Metadata for GeoBlacklight instances is stored and indexed in Solr, which uses a "Unique Key Field" as the identifier for each document. The OGM Aardvark schema was designed with `id` as the Unique Key Field (in GBL 1.0, this field was called `layer_slug_s`). Each item must have a unique key.

## JSON Format

OGM metadata is formatted as flat JSON files.

### Terms to Know
{: .no_toc }

#### Key:value pairs
{: .no_toc }

  * the `key` is either a metadata field name or an external reference URI
  * the `value` is the string, array, boolean, integer, etc. that goes in the field
  * strings are surrounded by 'single' or "double" quotation marks

```
"dct_identifier_sm": "http://purl.stanford.edu/dp018hs9766"
```

#### Objects
{: .no_toc }

  * consist of `key:value` pairs inside {curly brackets}
  * brackets are often put on a separate line to aid in readability

```
{
  "geoblacklight_version": "1.0",
  "dc_identifier_s": "https://cugir.library.cornell.edu/catalog/cugir-007950",
  ...
}
```

#### Arrays
{: .no_toc }

  * ordered collections of items
  * surrounded by [square brackets]
  * used for fields that can have multiple values, such as `dct_subject_sm` or multiple download links within the `dct_references_s` element.

```
"dct_subject_sm": [
    "Continental margins",
    "Multibeam mapping",
    "Elevation",
    "Imagery and Base Maps",
    "Inland Waters"
  ]
```

#### Escaped Characters
{: .no_toc }

  * certain characters are reserved for the JSON format, including double quotations `"` and forward slash `/`
  * if these characters are present in a string, they must be preceded by a backslash `\` in order for the JSON to function properly
  * the parentheses `"` and forward slashes `/` in URLs must be escaped with a backslash `\`

```
"dct_references_s": "{\"http:\/\/schema.org/url\":\"http:\/\/purl.stanford.edu\/dp018hs9766\",\"http:\/\/schema.org/downloadUrl\":\"http://stacks.stanford.edu/file/druid:dp018hs9766/data.zip\"}"
```

#### "Stringified JSON"
{: .no_toc }

  * the `dct_references_s` field in the GeoBlacklight JSON is sometimes referred to as "stringified JSON"; it looks like an object, but it is actually a string
  * the backslash `\` in the example above is an indication that this value is stringified JSON


### Example
{: .no_toc }

This is an example of a complete OGM Aardvark JSON file from the [Big Ten Geoportal](https://github.com/BTAA-Geospatial-Data-Project/geoportal/blob/develop/test/fixtures/files/btaa_documents/b1g_description_multiple.json). It contains several custom namespaced fields, indicated by the `b1g` prefix:

```json
{
  "id": "18bed919-fc86-4e02-a909-15f8bb9899bb",
  "model_name_ssi": "Document",
  "model_pk_ssi": "6ecf0720-52f4-49d3-b44e-32335e0c6dac",
  "gbl_mdVersion_s": "Aardvark",
  "dct_title_s": "Map of Part of the Province of Manitoba",
  "dct_alternative_sm": [
    "Map of part of the province of Manitoba shewing Dominion lands surveyed and lands disposed of."
  ],
  "dct_description_sm": [
    "1 map : col. ; 61 x 97 cm.",
    "Has table of distances from Winnipeg and Emerson.",
    "Shows lands owned by Canadian Pacific Railway, schools and Hudson Bay Company."
  ],
  "dct_language_sm": [
    "eng"
  ],
  "gbl_resourceClass_sm": [
    "Maps"
  ],
  "dct_subject_sm": [
    "Railroads"
  ],
  "dcat_keyword_sm": [
    "Real property Manitoba Maps."
  ],
  "dct_issued_s": "1881",
  "gbl_dateRange_drsim": [
    "[1881 TO 1881]"
  ],
  "gbl_indexYear_im": [
    1881
  ],
  "dct_spatial_sm": [
    "Manitoba,  Canada",
    "Canada",
    "Canada"
  ],
  "b1g_geonames_sm": [
    "http://sws.geonames.org/6065171"
  ],
  "locn_geometry": "ENVELOPE(-101.63,-94.87,51.07,49)",
  "dcat_centroid_ss": "50.035,-98.25",
  "pcdm_memberOf_sm": [
    "07d-01"
  ],
  "dct_format_s": "JPEG",
  "dct_references_s": "{\"http://schema.org/url\":\"https://quod.lib.umich.edu/c/clark1ic/x-003280519/39015091910987\",\"http://iiif.io/api/presentation#manifest\":\"https://quod.lib.umich.edu/cgi/i/image/api/search/clark1ic:003280519\"}",
  "b1g_image_ss": "https://quod.lib.umich.edu/cgi/i/image/api/image/clark1ic:003280519:39015091910987/full/res:1/0/native.jpg",
  "b1g_access_s": "{}",
  "dct_identifier_sm": [
    "G 3481 .G46 1881 .C3",
    "003280519",
    "39015091910987"
  ],
  "geomg_id_s": "18bed919-fc86-4e02-a909-15f8bb9899bb",
  "schema_provider_s": "University of Michigan",
  "b1g_code_s": "07d-01",
  "b1g_status_s": "Active",
  "b1g_dct_accrualMethod_s": "MARC",
  "b1g_dateAccessioned_sm": [
    "2021-04-16"
  ],
  "b1g_publication_state_s": "published",
  "dct_accessRights_s": "Public",
  "gbl_mdModified_dt": "2021-05-08T17:18:30Z",
  "date_created_dtsi": "2021-04-16T19:03:14Z",
  "date_modified_dtsi": "2021-05-08T17:18:30Z",
  "b1g_geom_import_id_ssi": "260"
}
```
