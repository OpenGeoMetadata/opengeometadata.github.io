---
layout: default
title: Workflow Examples
parent: Helpful Resources
nav_order: 2
---

# Workflow Examples
{: .no_toc }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Stanford University

At Stanford, the [metadata records](https://github.com/OpenGeoMetadata/edu.stanford.purl) are natively authored in ESRI ArcCatalog and then transformed into ISO 19139. The ISO 19139 records are then transformed to MODS for the library catalog and GeoBlacklight for the [GeoBlacklight catalog](https://earthworks.stanford.edu/).

![Stanford Metadata Workflow](/../assets/images/metadata_workflow.png)
_Stanford University Metadata Workflow_

Take, for example, the [metadata for this layer](https://github.com/OpenGeoMetadata/edu.stanford.purl/tree/master/rf/385/pb/1942). It has the [ISO 19139](https://github.com/OpenGeoMetadata/edu.stanford.purl/blob/master/rf/385/pb/1942/iso19139.xml) version of the metadata, along with the Feature Catalog (in [ISO 19110](https://github.com/OpenGeoMetadata/edu.stanford.purl/blob/master/rf/385/pb/1942/iso19110.xml)). We also have the transformation into [MODS](https://github.com/OpenGeoMetadata/edu.stanford.purl/blob/master/rf/385/pb/1942/mods.xml) and to [GeoBlacklight](https://github.com/OpenGeoMetadata/edu.stanford.purl/blob/master/rf/385/pb/1942/geoblacklight.json), as well as a [preview image](https://github.com/OpenGeoMetadata/edu.stanford.purl/blob/master/rf/385/pb/1942/preview.jpg). In some cases, you may even have an [HTML](http://opengeometadata.stanford.edu/metadata/edu.stanford.purl/druid:rv980rt5057/iso19139.html) version of the metadata for someone to read.

## Metadata tools and resources

For scripts and other tools to automate or validate metadata workflows, see [Scripts and Tools](scripts-and-tools).
