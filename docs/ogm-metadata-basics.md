---
layout: default
title: OGM Metadata Basics
parent: Helpful Resources
nav_order: 1
has_children: true
has_toc: false
---

# OGM Metadata Basics
{: .no_toc }

The basics of the OpenGeoMetadata metadata structure
{: .fs-6 .fw-300 }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Purpose

The OGM metadata schema is designed for GIS resource discovery and focuses mainly on discovery use cases. Text search, faceted search and refinement, and spatial search and relevancy are among the primary features that the schema enables. It:

* is based on [Dublin Core](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/), with custom elements added for spatial values
* is designed for discovery - to help users _find_ items
* is not designed for complete technical documentation, such as a GIS dataset's processing history
* includes elements for external links, such as downloads, web services, or supplemental metadata
* requires records to be formatted as JSON files

## Layers

The schemas are organized around "layers" as the unit of description. Each layer corresponds to a single set of data that can be described, downloaded, and (often) previewed. For example, this shapefile of [census boundaries](https://earthworks.stanford.edu/catalog/stanford-rf385pb1942) is considered a single layer in GeoBlacklight.

"A layer is a specific unit of data that contains a set of geospatial features, a metadata description, and a feature catalog. For example, a census layer would have the geometries of census tracts and the demographic results within each tract." [(Hardy and Durante 2014)](http://journal.code4lib.org/articles/9710)

## Unique keys

Metadata for GeoBlacklight instances is stored and indexed in Solr, which uses a "Unique Key Field" as the identifier for each document. The OGM Aardvark schema was designed with `id` as the Unique Key Field (in GBL 1.0, this field was called `layer_slug_s`). Each item must have a unique key.

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

This is an example of a complete OGM Aardvark JSON file:

```json
{
  "dct_title_s": "Racial Covenants [Hennepin County, Minnesota] (1910-1955)",
  "dct_alternative_sm": [
    "Racial Covenants in Hennepin County"
  ],
  "dct_description_sm": [
    "This data was compiled by the Mapping Prejudice Project and shows the location of racial covenants recorded in Hennepin County between 1910 and 1955. Racial covenants were legal clauses embedded in property records that restricted ownership and occupancy of land parcels based on race. These covenants dramatically reshaped the demographic landscape of Hennepin County in the first half of the twentieth century. In 1948, the United States Supreme Court ruled racial covenants to be legally unenforceable in the Shelly v. Kraemer decision. Racial covenants continued to be inserted into property records, however, prompting the Minnesota state legislature to outlaw the recording of new racial covenants in 1953. The same legislative body made covenants illegal in 1962. The practice was formally ended nationally with the passage of the Fair Housing Act in 1968."
  ],
  "dct_language_sm": [
    "eng"
  ],
  "dct_creator_sm": [
    "Ehrman-Solberg, Kevin",
    "Petersen, Penny",
    "Mills, Marguerite",
    "Delegard, Kirsten",
    "Mattke, Ryan"
  ],
  "dct_publisher_sm": [
    "University of Minnesota Mapping Prejudice Project"
  ],
  "schema_provider_s": "University of Minnesota",
  "gbl_resourceClass_sm": [
    "Datasets",
    "Web services"
  ],
  "gbl_resourceType_sm": [
    "Polygon data",
    "Vector data"
  ],
  "dcat_theme_sm": [
    "Society"
  ],
  "dcat_keyword_sm": [
    "Minneapolis",
    "racial covenants}segregation",
    "redlining",
    "real estate"
  ],
  "dct_temporal_sm": [
    "1910-1955"
  ],
  "dct_issued_s": "2020-12",
  "gbl_indexYear_im": [
    "1910"
  ],
  "gbl_dateRange_drsim": [
    "[1910 TO 1955]"
  ],
  "dct_spatial_sm": [
    "Bloomington, Minnesota",
    "Brooklyn Center, Minnesota",
    "Brooklyn Park, Minnesota",
    "Champlin, Minnesota",
    "Crystal, Minnesota",
    "Deephaven, Minnesota",
    "Eden Prairie, Minnesota",
    "Edina, Minnesota",
    "Golden Valley, Minnesota",
    "Greenwood, Minnesota",
    "Hopkins, Minnesota",
    "Maple Grove, Minnesota",
    "Maple Plain, Minnesota",
    "Medina, Minnesota",
    "Minneapolis, Minnesota",
    "Minnetonka, Minnesota",
    "Minnetonka Beach, Minnesota",
    "Minnetrista, Minnesota",
    "Mound, Minnesota",
    "Orono, Minnesota",
    "Osseo, Minnesota",
    "Plymouth, Minnesota",
    "Rays Lynnhurst, Minnesota",
    "Richfield, Minnesota",
    "Robbinsdale, Minnesota",
    "Shorewood, Minnesota",
    "St. Anthony, Minnesota",
    "St. Louis Park, Minnesota",
    "Tonka Bay, Minnesota",
    "Wayzata, Minnesota",
    "Woodland, Minnesota",
    "Hennepin County, Minnesota",
    "Minnesota"
  ],
  "locn_geometry": "POLYGON((-93.77 45.24, -93.17 45.24, -93.17 44.78, -93.77 44.78, -93.77 45.24))",
  "dcat_bbox": "ENVELOPE(-93.77,-93.17,45.24,44.78)",
  "dcat_centroid": "45.01,-93.47",
  "pcdm_memberOf_sm": [
    "dc8c18df-7d64-4ff4-a754-d18d0891187d"
  ],
  "dct_isPartOf_sm": [
    "05d-12",
    "05d-03"
  ],
  "dct_rights_sm": [
    "Content distributed via the University of Minnesota's Digital Conservancy may be subject to additional license and use restrictions applied by the depositor."
  ],
  "dct_license_sm": [
    "http://creativecommons.org/licenses/by-nc/3.0/us/"
  ],
  "dct_accessRights_s": "Public",
  "dct_format_s": "Shapefile",
  "dct_references_s": "{\"http://schema.org/url\":\"https://doi.org/10.13020/a88t-yb14\",\"http://lccn.loc.gov/sh85035852\":\"https://conservancy.umn.edu/bitstream/handle/11299/217209/Hennepin_County_Racial_Covenants_Codebook.txt\",\"urn:x-esri:serviceType:ArcGIS#FeatureLayer\":\"https://services.arcgis.com/8df8p0NlLFEShl0r/ArcGIS/rest/services/Hennepin_County_Racial_Covenants/FeatureServer/0\",\"http://schema.org/downloadUrl\":[{\"label\":\"covenants shapefile (4.554Mb)\",\"url\":\"https://conservancy.umn.edu/bitstream/handle/11299/217209/Hennepin_County_Racial_Covenants.zip\"},{\"label\":\"covenants CSV (9.925Mb)\",\"url\":\"https://conservancy.umn.edu/bitstream/handle/11299/217209/Hennepin_County_Racial_Covenants_Table.csv\"}]}",
  "id": "0455d309-e4e9-473e-8c3f-b42a6a2e16fc",
  "dct_identifier_sm": [
    "https://doi.org/10.13020/a88t-yb14"
  ],
  "gbl_mdModified_dt": "2022-09-14T20:18:27Z",
  "gbl_mdVersion_s": "Aardvark"
}
```
