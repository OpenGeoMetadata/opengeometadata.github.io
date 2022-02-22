---
layout: default
title: References
parent: About Our Schema
nav_order: 4
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

## Heading

## External Services

The field `dct_references_s` defines external services and references using the [CatInterOp](https://github.com/OSGeo/Cat-Interop) approach. The field value is a serialized JSON array of key/value pairs, with keys representing XML namespace URI's and values the URL, for example:

```xml
<field name="dct_references_s">
  {
    "http://schema.org/url":"http://purl.stanford.edu/bb509gh7292",
    "http://schema.org/downloadUrl":"http://stacks.stanford.edu/file/druid:bb509gh7292/data.zip",
    "http://www.loc.gov/mods/v3":"http://purl.stanford.edu/bb509gh7292.mods",
    "http://www.isotc211.org/schemas/2005/gmd/":"http://opengeometadata.stanford.edu/metadata/edu.stanford.purl/druid:bb509gh7292/iso19139.xml",
    "http://www.w3.org/1999/xhtml":"http://opengeometadata.stanford.edu/metadata/edu.stanford.purl/druid:bb509gh7292/default.html",
    "http://www.opengis.net/def/serviceType/ogc/wfs":"https://geowebservices-restricted.stanford.edu/geoserver/wfs",
    "http://www.opengis.net/def/serviceType/ogc/wms":"https://geowebservices-restricted.stanford.edu/geoserver/wms"
  }
</field>
```
