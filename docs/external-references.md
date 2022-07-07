---
layout: default
title: External References
parent:  Metadata
nav_order: 2
---

# References
{: .no_toc }

Explaining the "References" field and how it works
{: .fs-6 .fw-300 }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## JSON formatting

The field `dct_references_s` defines external services and references using the [Cat-Interop](https://github.com/OSGeo/Cat-Interop) approach. The field value is a serialized JSON array of key/value pairs. Keys represent XML namespace URIs, and values represent the URL.

* key:value 1 = "URI":"https://example.com"
* key:value 2 = "URI":"https://otherexample.com"

To format this field in JSON, double quotations `"` must be [escaped](../#escaped-characters) with a backslash `\`.

```json
{
  "dct_references_s": "{
    \"http://schema.org/url\":\"http://purl.stanford.edu/bm662dm5913\",
    \"http://schema.org/downloadUrl\":\"http://stacks.stanford.edu/file/druid:bm662dm5913/data.zip\"
    }"
}
```

## Reference URIs

These are URIs that can be used as keys in the `dct_references_s` field.

| Type                      | Reference URI    | Function in GeoBlacklight   |
|:--------------------------|:--------------|:-----------------------------|
| Download data dictionary / documentation | `http://lccn.loc.gov/sh85035852` | Link to download documentation |
| Download file | `http://schema.org/downloadUrl` | Link to download file (for multiple download links, [see below](#how-to-configure-multiple-download-links) |
| Full layer description | `http://schema.org/url` | View further descriptive information about the layer |
| International Image Interoperability Framework (IIIF) Image API | `http://iiif.io/api/image` | Load the image viewer using [Leaflet-IIIF](https://github.com/mejackreed/Leaflet-IIIF) |
| International Image Interoperability Framework (IIIF) Presentation API Manifest | `http://iiif.io/api/presentation#manifest` | View the IIIF manifest |
| Metadata in FGDC | `http://www.opengis.net/cat/csw/csdgm` | View structured metadata in FGDC standard expressed as XML |
| Metadata in HTML | `http://www.w3.org/1999/xhtml` | View structured metadata in any standard expressed as HTML |
| Metadata in ISO 19139 | `http://www.isotc211.org/schemas/2005/gmd/` | View structured metadata in ISO standard expressed as XML |
| Metadata in MODS | `http://www.loc.gov/mods/v3` | View structured metadata in MODS format |
| OpenIndexMap	            | `https://openindexmaps.org`	                    | Provide an index map preview   |
| Web Mapping Service (WMS) | `http://www.opengis.net/def/serviceType/ogc/wms` | Link to preview layer, inspect features, and download data (vector: KMZ, raster: GeoTIFF) |
| Web Feature Service (WFS) | `http://www.opengis.net/def/serviceType/ogc/wfs` | Link to download vectors (GeoJSON, shapefile) |

### ArcGIS URIs
{: .no_toc }

| Type                      | Reference URI                                   | Function in GeoBlacklight               |
|:--------------------------|:------------------------------------------------|:----------------------------------------|
| ArcGIS FeatureLayer       | `urn:x-esri:serviceType:ArcGIS#FeatureLayer`    | Preview an ArcGIS FeatureLayer Service  |
| ArcGIS TiledMapLayer      | `urn:x-esri:serviceType:ArcGIS#TiledMapLayer`   | Preview an ArcGIS TiledMapLayer Service |
| ArcGIS DynamicMapLayer    | `urn:x-esri:serviceType:ArcGIS#DynamicMapLayer` | Preview an ArcGIS DynamicMapLayer Service |
| ArcGIS ImageMapLayer      | `urn:x-esri:serviceType:ArcGIS#ImageMapLayer`   | Previews a ArcGIS ImageMapLayer Service |

### URIs for specific institutions
{: .no_toc }

| Type                      | Reference URI                                   | Function in GeoBlacklight               |
|:--------------------------|:------------------------------------------------|:----------------------------------------|
| Harvard Geospatial Library email download | `http://schema.org/DownloadAction` | Retrieve a file via email from the Harvard Geospatial Library |

## How to configure multiple download links

Beginning with GeoBlacklight version 3.0, multiple download links and file formats can be included in the `dct_references_s` field. For more details on this update, see [this pull request](https://github.com/geoblacklight/geoblacklight/pull/916).

To enable multiple downloads:
* Make the value for the download file URI (`http://schema.org/downloadUrl`) into an array. This means it is enclosed in [square brackets].
* Create one or more objects inside the array. These are enclosed in {curly brackets}.
* Inside the object, define two `key:value` pairs separated by a comma.
* Enclose each key and each value in double quotes.
* [Escape](../#escaped-characters) double quotations `"` with a backslash `\`

In formatted JSON, this would look like:
```json
{
  "dct_references_s": "{\"http://schema.org/downloadUrl\":[
    {
      \"url\":\"https://example.com\",
      \"label\":\"Shapefile\"
    },
    {
      \"url\":\"https://otherexample.com\",
      \"label\":\"KMZ\"
    }]
  }"
}
```

### Examples
{: .no_toc }

For an exmaple of a complete JSON file with multiple downloads, see [this record](https://github.com/geoblacklight/geoblacklight/blob/main/spec/fixtures/solr_documents/multiple-downloads.json).

**Single download**

```json
{
  "dct_references_s": "{\"http://schema.org/downloadUrl\":\"https://cugir-data.s3.amazonaws.com/00/79/50/cugir-007950.zip\"}"
}
```

**Single download as an array**

When using an array for downloads, the value after the `"label"` key will be used as the text in the Download panel button.

```json
{
  "dct_references_s": "{\"http://schema.org/downloadUrl\":[
    {
      \"url\":\"https://cugir-data.s3.amazonaws.com/00/79/50/cugir-007950.zip\",
      \"label\":\"Shapefile\"
    }]
  }"
}
```

**Multiple downloads**

```json
{
  "dct_references_s": "{\"http://schema.org/downloadUrl\":[
    {
      \"url\":\"https://cugir-data.s3.amazonaws.com/00/79/50/cugir-007950.zip\",
      \"label\":\"Shapefile\"
    },
    {
      \"url\":\"https://cugir-data.s3.amazonaws.com/00/79/50/agBROO.pdf\",
      \"label\":\"PDF\"
    },
    {
      \"url\":\"https://cugir-data.s3.amazonaws.com/00/79/50/agBROO2011.kmz\",
      \"label\":\"KMZ\"
    }]
  }"
}
```
