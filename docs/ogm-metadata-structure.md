---
layout: default
title: OGM Metadata Structure
parent: Metadata
nav_order: 1
has_children: false
has_toc: false
---

# OGM Metadata Structure
{: .no_toc }

The OpenGeoMetadata metadata structure
{: .fs-6 .fw-300 }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Layers

The schemas are organized around "layers" as the unit of description. Each layer corresponds to a single set of data that can be described, downloaded, and (often) previewed. For example, this shapefile of [census boundaries](https://earthworks.stanford.edu/catalog/stanford-rf385pb1942) is considered a single layer in GeoBlacklight.

"A layer is a specific unit of data that contains a set of geospatial features, a metadata description, and a feature catalog. For example, a census layer would have the geometries of census tracts and the demographic results within each tract." [(Hardy and Durante 2014)](http://journal.code4lib.org/articles/9710)

## Unique keys

Metadata for GeoBlacklight instances is stored and indexed in Solr, which uses a "Unique Key Field" as the identifier for each document. The OGM Aardvark schema was designed with `id` as the Unique Key Field (in GBL 1.0, this field was called `layer_slug_s`). Each item must have a unique key.

## How fields are named

{: .no_toc }

Solr uses the suffix of a metadata element to determine what kind of field it is. The following suffixes are part of the OGM Aardvark schema and may be used by custom fields, too (for a full list of spatial field types and their suffixes, see [this code](https://github.com/geoblacklight/geoblacklight/blob/main/solr/conf/schema.xml#L14)):

| Field Suffix | Type                     | Description                     | Example   |
|:-------------|:-------------------------|:--------------------------------|:----------|
| `_b`         | Boolean                  | Values can be "TRUE" or "FALSE" | `gbl_georeferenced_b`|
| `_im`        | Integer, multi-valued    | Digits                          | `gbl_indexYear_im`|
| `_drsim`     | Date range, multi-valued | Date range in a specified format: “[1980 TO 1995]” | `gbl_dateRange_drsim` |
| `_dt`        | Date                     | Date and time in a specified format: YYYY-MM-DDThh:mm:ssZ | `gbl_mdModified_dt`|
| `_s`         | String                   | Single string of text           | `dct_title_s` |
| `_sm`        | String, multi-valued     | Multiple strings of text        | `dct_subject_sm` |

Altering suffixes can result in metadata schema incompatibilities across institutions. Any deviations in element names causes Solr to treat the elements as separate fields: for example `dct_subject_s` and `dct_subject_sm` would be stored separately. If GeoBlacklight is set up to display a facet for `dct_subject_s`, it will not pick up values stored in `dct_subject_sm` in the filter. Therefore, if you are gathering metadata from other institutions, make sure to inspect their metadata fields to determine if there will be inconsistencies in your Solr index.
See the [current schema](ogm-aardvark) for a full description of fields, expected values, and obligations.

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



## JSON format

OGM metadata is formatted as flat JSON files.

### Terms to know
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

```json
{
  "geoblacklight_version": "1.0",
  "dc_identifier_s": "https://cugir.library.cornell.edu/catalog/cugir-007950"
}
```

#### Arrays
{: .no_toc }

  * ordered collections of items
  * surrounded by [square brackets]
  * used for fields that can have multiple values, such as `dct_subject_sm` or multiple download links within the `dct_references_s` element.

```json
{
  "dct_subject_sm": [
    "Continental margins",
    "Multibeam mapping",
    "Elevation",
    "Imagery and Base Maps",
    "Inland Waters"
  ]
}
```

#### Escaped characters
{: .no_toc }

  * certain characters are reserved for the JSON format, including double quotations `"`
  * if these characters are present in a string, they must be preceded by a backslash `\` in order for the JSON to function properly
  * double quotations `"` within strings must be escaped with a backslash `\`

```json
{
  "dct_references_s": "{\"http://schema.org/url\":\"http://purl.stanford.edu/dp018hs9766\",\"http://schema.org/downloadUrl\":\"http://stacks.stanford.edu/file/druid:dp018hs9766/data.zip\"}"
}
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
