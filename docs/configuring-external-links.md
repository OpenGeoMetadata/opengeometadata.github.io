# Configuring External Links (dct_references_s)

This page provides guidance on how to format the [References](ogm-aardvark/references.md) field in either GBL 1.0 or OGM Aardvark.

## JSON formatting

The field `dct_references_s` defines external services and references using the [Cat-Interop](https://github.com/OSGeo/Cat-Interop) approach. The field value is a serialized JSON array of key/value pairs. Keys represent XML namespace URIs, and values represent the URL.

* key:value 1 = "URI":"https://example.com"
* key:value 2 = "URI":"https://otherexample.com"

To format this field in JSON, double quotations `"` must be [escaped](../JSON-format#escaped-characters) with a backslash `\`.

```json
{
  "dct_references_s": "{
    \"http://schema.org/url\":\"http://purl.stanford.edu/bm662dm5913\",
    \"http://schema.org/downloadUrl\":\"http://stacks.stanford.edu/file/druid:bm662dm5913/data.zip\"
    }"
}
```

## Configuring multiple download links

Beginning with GeoBlacklight version 3.0, multiple download links and file formats can be included in the `dct_references_s` field. For more details on this update, see [this pull request](https://github.com/geoblacklight/geoblacklight/pull/916).

To enable multiple downloads:
* Make the value for the download file URI (`http://schema.org/downloadUrl`) into an array. This means it is enclosed in [square brackets].
* Create one or more objects inside the array. These are enclosed in {curly brackets}.
* Inside the object, define two `key:value` pairs separated by a comma.
* Enclose each key and each value in double quotes.
* [Escape](../JSON-format#escaped-characters) double quotations `"` with a backslash `\`

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