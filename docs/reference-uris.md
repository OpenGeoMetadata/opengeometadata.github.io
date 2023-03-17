---
hide:
  -toc
---

# Reference URIs

These are URIs that can be used as keys in the [`dct_references_s`](ogm-aardvark/references.md) field.

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


| Type                      | Reference URI                                   | Function in GeoBlacklight               |
|:--------------------------|:------------------------------------------------|:----------------------------------------|
| ArcGIS FeatureLayer       | `urn:x-esri:serviceType:ArcGIS#FeatureLayer`    | Preview an ArcGIS FeatureLayer Service  |
| ArcGIS TiledMapLayer      | `urn:x-esri:serviceType:ArcGIS#TiledMapLayer`   | Preview an ArcGIS TiledMapLayer Service |
| ArcGIS DynamicMapLayer    | `urn:x-esri:serviceType:ArcGIS#DynamicMapLayer` | Preview an ArcGIS DynamicMapLayer Service |
| ArcGIS ImageMapLayer      | `urn:x-esri:serviceType:ArcGIS#ImageMapLayer`   | Previews a ArcGIS ImageMapLayer Service |

### URIs for specific institutions


| Type                      | Reference URI                                   | Function in GeoBlacklight               |
|:--------------------------|:------------------------------------------------|:----------------------------------------|
| Harvard Geospatial Library email download | `http://schema.org/DownloadAction` | Retrieve a file via email from the Harvard Geospatial Library |