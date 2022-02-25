---
layout: default
title: Scripts and Tools
parent: Helpful Resources
nav_order: 5
---

# Scripts and Tools
{: .no_toc }

subtitle
{: .fs-6 .fw-300 }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Tools

### Standalone scripts
These scripts can be downloaded and used locally for creating, transforming, and publishing GeoBlacklight metadata.
#### [SdrFriend](https://github.com/NYULibraries/sdrfriend)
* Overview: SdrFriend is a Ruby gem that allows people of various skill levels to interface with DSpace, GDAL, GeoServer, and other spatial data collection tools (performs rake tasks on a SDI, crosswalks csv and JSON files).
* Requirements: Ruby 2.4.0 [if needed: Ruby Version Manager (RVM)], homebrew, bundler
* Originator: NYU

#### [GeoCombine](https://github.com/OpenGeoMetadata/GeoCombine)
* Overview: A Ruby toolkit that is useful for cloning, updating, and indexing metadata from OpenGeoMetdata and includes a library for converting metadata between standards. [XSL sheets are found here](https://github.com/OpenGeoMetadata/GeoCombine/tree/master/lib/xslt)
* Requirements: Ruby
* Originator: Stanford

#### [JSON Schema](https://github.com/geoblacklight/geoblacklight/blob/master/schema/geoblacklight-schema.json)
* Overview: A JSON file for validating the structural form of the GBL metadata

#### [Convert MARC files to GeoBlacklight Metadata files](https://github.com/mjanowiecki/geoportal/wiki)
* Overview: This is a preliminary workflow to convert MARC metadata for historic and print maps into JSON metadata according to the GeoBlacklight 1.0 Metadata Schema.
* Requirements: Python
* Originator: Johns Hopkins University
* Related resource: [Johns Hopkins University Geoportal Metadata Application Profile (JHU-GMAP) 1.0](https://github.com/jhu-data-services/GeoBlacklightMetadata)

### Integrated applications
These tools were built as part of automated workflows for specific repositories

#### [GeoDataLoader](https://github.com/culibraries/geo-data-loader)
* Overview: A custom tool with a built-in metadata editor that can load information directly into Geoserver. Can accept templates if multiple uploads are needed.
* Requirements: bootstrap, handlebars, jquery
* Originator: CU Boulder

#### [Figgy](https://github.com/pulibrary/figgy#dependencies)
* Overview: A digital repository application in use at Princeton University Library for storing and managing digital representations of manuscripts, ephemera, vector, and raster data for export into a variety of front-end displays.
* Requirements: Ruby, Java, Postgres, GDAL [and more](https://github.com/pulibrary/figgy#dependencies)
* Originator: Princeton

## Resources
* An earlier version of the GeoBlacklight schema and the motivations behind its design is published in the Code4Lib Journal: "[A Metadata Schema for Geospatial Resource Discovery Use Cases](http://journal.code4lib.org/articles/9710)"
* Stanford [Metadata Workflow](https://github.com/kimdurante/metadataWorkflow) - These guidelines outline operations for the creation and management of geospatial metadata in the Stanford Digital Repository (SDR) and the Stanford Spatial Data Infrastructure (SSDI).
* NYU [code examples, workflow steps, and ideas for managing the Spatial Data Repository](https://github.com/NYULibraries/sdr-documentation)
* Big Ten Academic Alliance Geospatial Data Project's [Metadata Handbook](https://z.umn.edu/gbl-handbook)
* [Consortial Geospatial Data Collection: Toward Standards and Processes for Shared GeoBlacklight Metadata](https://osf.io/preprints/lissa/kp5r6/) - article discussing strategies for authorship and management of interoperable GeoBlacklight metadata
