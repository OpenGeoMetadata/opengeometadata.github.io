---
layout: default
title: Scripts and Tools
parent: Metadata
nav_order: 6
---

# Scripts and Tools
{: .no_toc }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Standalone scripts

These scripts can be downloaded and used locally for creating, transforming, and publishing OGM schema metadata.

### [SdrFriend](https://github.com/NYULibraries/sdrfriend)
{: .no_toc }

| Overview     | SdrFriend is a Ruby gem that allows people of various skill levels to interface with DSpace, GDAL, GeoServer, and other spatial data collection tools (performs rake tasks on a SDI, crosswalks csv and JSON files). |
| Requirements | Ruby 2.4.0 [if needed: Ruby Version Manager (RVM)], homebrew, bundler |
| Originator   | NYU |

### [GeoCombine](https://github.com/OpenGeoMetadata/GeoCombine)
{: .no_toc }

| Overview     | A Ruby toolkit that is useful for cloning, updating, and indexing metadata from OpenGeoMetdata and includes a library for converting metadata between standards. [XSL sheets are found here](https://github.com/OpenGeoMetadata/GeoCombine/tree/master/lib/xslt). |
| Requirements | Ruby |
| Originator   | Stanford |

### [JSON Schema](https://github.com/geoblacklight/geoblacklight/blob/master/schema/geoblacklight-schema.json)
{: .no_toc }

| Overview     | A JSON file for validating the structural form of the GBL metadata. |

### [Convert MARC files to GeoBlacklight Metadata files](https://github.com/mjanowiecki/geoportal/tree/main/aardvark)
{: .no_toc }

| Overview     | A preliminary workflow to convert MARC metadata for historic and print maps into JSON metadata according to the GeoBlacklight 1.0 Metadata Schema. |
| Requirements | Python |
| Originator   | Johns Hopkins University |
| Related resource | Johns Hopkins University Geoportal Metadata Application Profile [(JHU-GMAP) 1.0](https://github.com/jhu-data-services/GeoBlacklightMetadata) |

### [OGM Aardvark Metadata Scripts](https://github.com/umass-gis/metadata-scripts)
{: .no_toc }

| Overview     | Basic Pythons scripts to convert ArcGIS-generated XML files to Aardvark schema JSON files. Queries the GeoNames database to retrieve placenames for the `dct_spatial_sm` field. |
| Requirements | Python |
| Originator   | UMass Amherst |

## Integrated applications
These tools were built as part of automated workflows for specific repositories.

### [GeoDataLoader](https://github.com/culibraries/geo-data-loader)
{: .no_toc }

| Overview     | A custom tool with a built-in metadata editor that can load information directly into Geoserver. Can accept templates if multiple uploads are needed. |
| Requirements | bootstrap, handlebars, jquery |
| Originator   | CU Boulder |

### [Figgy](https://github.com/pulibrary/figgy#dependencies)
{: .no_toc }

| Overview     | A digital repository application in use at Princeton University Library for storing and managing digital representations of manuscripts, ephemera, vector, and raster data for export into a variety of front-end displays. |
| Requirements | Ruby, Java, Postgres, GDAL [and more](https://github.com/pulibrary/figgy#dependencies) |
| Originator   | Princeton |
