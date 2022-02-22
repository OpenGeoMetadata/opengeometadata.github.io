---
layout: default
title: The Basics
parent: About Our Schemas
nav_order: 2
---

# The Basics
{: .no_toc }

Overview of how OGM metadata is structured
{: .fs-6 .fw-300 }

OGM metadata schemas are designed for GIS resource discovery and focus mainly on discovery use cases. Text search, faceted search and refinement, and spatial search and relevancy are among the primary features that the schemas enable. They are:

* based on [Dublin Core](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/), with custom elements added for spatial values
* designed for discovery - to help users _find_ items
* not designed for complete technical documentation, such as a GIS dataset's processing history
* include elements for external links, such as downloads, web services, or supplemental metadata
* records are formatted as JSON files

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Layers

The schemas are organized around "layers" as the unit of description. Each layer corresponds to a single set of data that can be described, downloaded, and (often) previewed. For example, this shapefile of [census boundaries](https://earthworks.stanford.edu/catalog/stanford-rf385pb1942) is considered a single layer in GeoBlacklight.

"A layer is a specific unit of data that contains a set of geospatial features, a metadata description, and a feature catalog. For example, a census layer would have the geometries of census tracts and the demographic results within each tract." [(Hardy and Durante 2014)](http://journal.code4lib.org/articles/9710)

## Fields
See the [current schema](../../aardvarkSchema) for field descriptions and values.

### Fields related to identity

There are three fields in the OpenGeoMetadata schemas that relate to a layer's identity.

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

### Custom fields

If an organization wishes to implement a custom metadata field for their GeoBlacklight instance, the naming schema should reference the organization as follows: `organization_elementName_solrFieldType`.

Examples:
* `b1g_code_s` - Internal code that organizes items by their source collection
* `nyu_addl_dspace_s` - A 5 digit number that is the "internal identifier" for DSpace, the repository software that mints handles for all NYU's items. The internal id must be paired with the handle in order to post metadata and data via the system API.

### Deprecated fields

Fields are occasionally deprecated during revisions of the schemas. See the [GBL 1.0 --> OGM Aardvark](../about-ogm-aardvark/#crosswalkable-and-new-elements) crosswalk table for a complete list of deprecated field names from the most recent update. In addition, these previous deprecated fields may occur in older metadata records:

* `uuid`
* `dc_relation_sm`
* `georss_box_s`
* `georss_point_s`
* `georss_polygon_s`

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
