---
layout: default
title: Writing Metadata
parent: Helpful Resources
nav_order: 2
---

# Writing Metadata
{: .no_toc }

subtitle
{: .fs-6 .fw-300 }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Validating Metadata

The current version of the schema is available as a [JSON-Schema file](https://github.com/geoblacklight/geoblacklight/tree/main/schema). This file format provides support for data validation with the [JSON Schema Vocabulary](http://json-schema.org).

* **Recommended Method**: Use [GeoCombine](https://github.com/OpenGeoMetadata/GeoCombine), which has a [.valid? method](http://www.rubydoc.info/gems/geo_combine/0.1.0/GeoCombine/Geoblacklight#valid%3F-instance_method) that makes using these tools simple.

## Viewing Metadata

This section refers to documentation created for GeoBlacklight version 2.0. The code may look different if you are running a newer version of the software.
{: .note}

The metadata that appears on an item's show page is set by a file called `catalog_controller.rb`. This file is located in the application at `app/controllers/catalog_controller.rb`. For more information on how to customize the show page, see [this section of the GeoBlacklight tutorial](https://geoblacklight.org/tutorial/2015/02/09/customize-your-application.html#customize-metadata-shown).

Other metadata views can be found by appending terms to the end of an item's show page URL. Note that there are some differences in these features between GeoBlacklight 2.0 and earlier versions. See [this section of the upgrade guide to GeoBlacklight version 2.0](https://github.com/geoblacklight/geoblacklight/wiki/GeoBlacklight-2.0-Upgrade-Guide#update-catalogcontroller) to enable all of these features. The following methods involve adding an extension to the show page URL:

### .xml
{: .no_toc }

* produces a Dublin Core XML document in the [OAI_DC schema](https://www.openarchives.org/OAI/2.0/oai_dc.xsd). The fields for this document can be adjusted in the `solr_document.rb`, which is found here: `app/models/solr_document.rb`. Example: https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677.xml.

### .json
{: .no_toc }

* GeoBlacklight until version 1.9: produces a full metadata file for the item as a flat JSON document.
* GeoBlacklight 2.0+: produces a nested JSON document of the metadata that appears on the item page. This document can be harvested by the [JSON:API](https://jsonapi.org/) protocol.

### /raw
{: .no_toc }

* GeoBlacklight until version 1.9: not available.
* GeoBlacklight 2.0+: displays the full metadata file for the item as a flat JSON document.
