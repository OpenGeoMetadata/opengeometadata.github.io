---
layout: default
title: Current Schema
nav_order: 4
has_children: true
has_toc: true
permalink: /docs/current-schema
---

# Current Schema
{: .no_toc }

Details about the new OpenGeoMetadata metadata schema, OGM Aardvark
{: .fs-6 .fw-300 }

OGM Aardvark is the newest metadata application profile schema for GeoBlacklight. Launched in 2021, it replaces the GeoBlacklight metadata schema version 1.0 ([GBL 1.0](../../legacy-schemas/gbl-1.0)). Aardvark incorporates additional fields for better descriptions of a wider range of resources, as well as syntactical updates in order to improve interoperability between institutions and between schemas.

OGM Aardvark was intentionally developed with cross-application in mind and can be used to describe geospatial assets of all kinds. For GeoBlacklight users, it is the recommended schema for installations starting with GeoBlacklight version 4.0.

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Why is this called Aardvark?

The term “aardvark” represents a new naming convention to specify metadata schema versions. This convention is intended to reduce confusion between the metadata schema version and GeoBlacklight software versions, which uses numerical-based indicators.


## Why do we need an updated schema?

GeoBlacklight and its original metadata application schema (1.0) are well-suited to describing single layers of GIS data served out as OGC web services and documented with supplemental metadata, such as ISO 19115 (19139). Since that time, the growing community of GeoBlacklight adopters has introduced new use cases and institutional requirements. This growth brought several challenges to the metadata application schema as it was originally conceived including:

*   a lack of fields for statements about rights
*   a lack of clarity around how to define relationships between items
*   few options for describing other types of resources, such as scanned maps, collections, and websites
*   mandatory fields that did not have applicable values (i.e. **Geometry Type**)
*   single-valued fields that could have multiple values (i.e. **Language**, **Publisher**)
*   fields with names that were not intuitive for new users

The minimal nature of the original GeoBlacklight schema combined with the growing environment of customized local fields has presented obstacles for new adopters. Instead of being able to rely on the official application schema to meet all or most of their needs, they must develop local solutions. Ultimately, in order to use GeoBlacklight, many adopters implemented custom fields. [A review of extant custom fields](https://github.com/geoblacklight/geoblacklight/issues/937) in 2020 revealed that at least six institutions had added or altered fields in the GeoBlacklight schema. Altogether, over 20 custom fields were in use. The result of these custom fields was metadata that was not fully interoperable across institutions. For example, three schools had implemented three different fields for indicating rights or licenses.


## Who came up with the schema?

The GeoBlacklight Metadata Schema Workgroup consisted of 16 people from 12 institutions. The workgroup formed during the Summer Community Sprint in August 2020 and met every three weeks thereafter through January 2021. The group wrapped up after the Winter Community Sprint in February 2021, during which time they consulted with application developers and finalized the recommendations for Aardvark.

**Workgroup Goals**

1. Systematically assess and evaluate the GeoBlacklight Schema 1.0
2. Develop a new GeoBlacklight Metadata Schema that features:
    1. improved interoperability with DCAT and Dublin Core-based schemas
    2. new fields for rights
    3. new fields for item relations
    4. new recommendations for controlled vocabularies and values
3. Develop a new [Metadata Application Profile (MAP)](https://www.loc.gov/aba/pcc/taskgroup/Metadata-Application-Profiles.html) for GeoBlacklight

**Workgroup Constraints & Considerations**

*   The GeoBlacklight schema was designed as an application-specific schema purely for discovery. It should not be a replacement for a full-fledged geospatial standard, such as ISO 19139.
*   Elements that drive the functionality of GeoBlacklight should be examined cautiously, as changes to the schema for these elements will require new application development time to implement.
*   New elements that are optional and additive are easier to adopt than ones that are syntactical replacements of existing fields.
*   Although backward compatibility is usually preferred, it may not be possible to accommodate both schemas within a single application. Any breaking changes must be clearly stated and documented.

**Workgroup Members**

* Abigail Pennington (UC San Diego)
* Adi Ranganath (New York University)
* Amy Work (UC San Diego)
* Andrew Battista (New York University)
* Diane Fritz (Auraria Library)
* Karen Majewicz (University of Minnesota/BTAA)
* Keith Jenkins (Cornell University)
* Kimberly Durante (Stanford University)
* Lena Denis (Johns Hopkins University)
* Mara Blake (Johns Hopkins University)
* Marc McGee (Harvard University)
* Margaret Mering (University of Nebraska-Lincoln)
* Michelle Janowiecki (Johns Hopkins University)
* Stephen Appel (University of Wisconsin-Milwaukee)
* Susan Powell (UC Berkeley)
* Tom Brittnacher (UC Santa Barbara)


**Helpful Metadata Terminology used by the Workgroup**

*   **URI**: This is the name we give to the metadata element itself. For example, the URI for the GeoBlacklight subject field is `dct_subject_sm`.
*   **Namespace**: This is how we signify which family of standards or schemas an element belongs to. For the GeoBlacklight schema, this takes the form of the URI’s prefix. For the URI `dct_subject_sm`,  `dct_` is the prefix and signifies that this element is from Dublin Core.
*   **Solr field type**: This is the suffix appended to the URI and indicates what kind of Solr field should be indexed. For `dct_subject_sm`, the `_sm` stands for String Multiple. It indicates that the field type is a string and that it can have multiple values.
*   **Value**: This is the information that is entered in a field. It may be free text (literal value) or a URI/code (nonliteral value).


## What is different about the new schema?

### New elements for rights
{: .no_toc }

One of the highest priorities for the Workgroup was to identify appropriate elements to capture rights information. This information is required at many participating institutions, and was the cause of multiple custom fields at different institutions that served the same purpose.

After examining how rights are implemented for different projects, notably the Digital Public Library of America (DPLA) and [RightsStatements.org,](https://rightsstatements.org) we recommended three new fields and a renaming of one field. This change is the one instance in which we recommended that an existing GeoBlacklight element with application functionality be replaced by another.

The new set of rights elements are:

| Label              | URI                     | Description and Entry Guidelines |
|:-------------------|:------------------------|:---------------------------------|
| Access Rights      | `dct_accessRights_s`    | One of two possible values, "Public" or "Restricted"; controls whether a user can preview or download an item. This element replaces `dc_rights_s`. |
| Rights             | `dct_rights_sm`         | Free-text field for generic, catch-all access and usage rights. Can include clickable links. |
| License            | `dct_license_sm`        | Field for one or more URIs. Recommended sources are [Creative Commons](https://creativecommons.org/) or [Open Data Commons](https://opendatacommons.org/). |
| Rights Holder      | `dct_rightsHolder_sm`   | Free-text field for the person or organization owning or managing rights over the resource. |


### New elements for item relations
{: .no_toc }

One of the thorniest issues we tackled was how to define item relations. We identified four new relationships, redefined two, and added a general, catch-all **Relation** field. The value for each field should be the ID (slug) of the related item.

GeoBlacklight version 3.4 and earlier has an Item Relations widget that displays items identified in the **Source** field. Beginning with version 4, this has been updated to use the same widget for each of these fields

The new set of relationship elements are:

| Label              | URI                     | Description and Entry Guidelines |
|:-------------------|:------------------------|:---------------------------------|
| Source             | `dct_source_sm`         | For items that have been derived from another item (e.g. a digitized shapefile from a historical map). |
| Is Part Of         | `dct_isPartOf_sm`       | For items that are a subset of another item (e.g. a page in a book). This value type is changing from free-text in Version 1.0 to an ID (slug) in the new schema. |
| Member Of          | `pcdm_memberOf_sm`      | For items in a collection.       |
| Replaces           | `dct_replaces_sm`       | To refer to an item that has been deprecated. |
| Is Replaced By     | `dct_isReplacedBy_sm`   | To point the user to a new item. |
| Version            | `dct_isVersionOf_sm`    | To indicate that an item is part of a series of resources that are updated or altered. |
| Relation            | `dct_relation_sm`      | For a general purpose relation.  |


### Consistent namespaces for all metadata element URIs
{: .no_toc }

The new version always gives preference to elements found in established schemas over custom fields.

* **`dct_`**: This signifies that the field is part of the [Dublin Core Metadata Initiative (DCMI) Metadata Terms](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/). Any Dublin Core fields from the GeoBlacklight Schema 1.0 were updated to use the `dct_` namespace.
* **`dcat_`**: This signifies that the field is from the [Data Catalog Vocabulary (DCAT) Version 2](https://www.w3.org/TR/vocab-dcat-2/).
* **`pcdm_`**: This refers to the [Portland Common Data Model](https://github.com/duraspace/pcdm/wiki), which is a framework for many digital repository systems. We drew from it to establish one of the item relationship fields.
* **`gbl_`**: This stands for GeoBlacklight and is used for any field that is application-specific or has no analogous term in other schemas.


### Multivalued elements whenever possible
{: .no_toc }

The original schema features several descriptive metadata fields that only accept one value. The new schema expands many of these to multiple. This changes the URI suffix from `_s` to` _sm`. Although it will not affect the GeoBlacklight functionality, this practice may conflict with indexing, as Solr will treat `dct_publisher_s` as a different field than `dct_publisher_sm`.


## How do I convert my Version 1.0 metadata into Aardvark?

The GeoBlacklight community is working to develop tools within GeoCombine that will systematically convert 1.0 metadata into Aardvark. In the meantime, [this python script](https://github.com/BTAA-Geospatial-Data-Project/GBL-Schema-Update) can be used to batch convert JSON files. The information below can help with crosswalking if these tools aren't sufficient.

### Crosswalkable and new elements
{: .no_toc }

Most of the elements from GBL Version 1.0 can be crosswalked directly into OGM Aardvark. The values for these elements are the same - only the URI name has changed or the field has been converted to an array.  The following chart shows the mapping from GeoBlacklight version 1.0 into corresponding Aardvark fields.

|  # |       Label       |        GBL 1.0           |      OGM Aardvark      |                Note               |
|:---|:------------------|:-------------------------|:-----------------------|:----------------------------------|
| 01 |       Title       | `dc_title_s`             | `dct_title_s`          |           new namespace           |
| 02 | Alternative Title |                          | `dct_alternative_sm`   |             new field             |
| 03 |    Description    | `dc_description_s`       | `dct_description_sm`   |new namespace; single to multi-valued|
| 04 |      Language     | `dc_language_s` or `_sm` | `dct_language_sm`      |new namespace; single to multi-valued|
| 05 |      Creator      | `dc_creator_sm`          | `dct_creator_sm`       |           new namespace           |
| 06 |     Publisher     | `dc_publisher_s`         | `dct_publisher_sm`     |new namespace; single to multi-valued|
| 07 |      Provider     | `dct_provenance_s`       | `schema_provider_s`    |            new URI name           |
| 08 |   Resource Class  |                          | `gbl_resourceClass_sm` |             new field             |
| 09 |   Resource Type   |                          | `gbl_resourceType_sm`  |             new field             |
| 10 |      Subject      | `dc_subject_sm`          | `dct_subject_sm`       |           new namespace           |
| 11 |       Theme       |                          | `dcat_theme_sm`        |             new field             |
| 12 |      Keyword      |                          | `dcat_keyword_sm`      |             new field             |
| 13 | Temporal Coverage | `dct_temporal_sm`        | `dct_temporal_sm`      |             no change             |
| 14 |    Date Issued    | `dct_issued_s`           | `dct_issued_s`         |             no change             |
| 15 |     Index Year    | `solr_year_i`            | `gbl_indexYear_im`     |new URI name; single to multi-valued|
| 16 |     Date Range    |                          | `gbl_dateRange_drsim`  |             new field             |
| 17 |  Spatial Coverage | `dct_spatial_sm`         | `dct_spatial_sm`       |             no change             |
| 18 |      Geometry     | `solr_geom`              | `locn_geometry`        |             new field             |
| 19 |    Bounding Box   | `solr_geom`              | `dcat_bbox`            |             new field             |
| 20 |      Centroid     |                          | `dcat_centroid`        |             new field             |
| 21 |      Relation     |                          | `dct_relation_sm`      |             new field             |
| 22 |     Member Of     |                          | `pcdm_memberOf_sm`     |             new field             |
| 23 |     Is Part Of    |                          | `dct_isPartOf_sm`      |new value type (see [Elements without a crosswalk](../../aardvarkSchema/resource-class/#elements-without-a-crosswalk))|
| 24 |       Source      | `dc_source_sm`           | `dct_source_sm`        |           new namespace           |
| 25 |      Version      |                          | `dct_isVersionOf_sm`   |             new field             |
| 26 |      Replaces     |                          | `dct_replaces_sm`      |             new field             |
| 27 |   Is Replaced By  |                          | `dct_isReplacedBy_sm`  |             new field             |
| 28 |       Rights      |                          | `dct_rights_sm`        |             new field             |
| 29 |   Rights Holder   |                          | `dct_rightsHolder_sm`  |             new field             |
| 30 |      License      |                          | `dct_license_sm`       |             new field             |
| 31 |   Access Rights   | `dc_rights_s`            | `dct_accessRights_s`   |            new URI name           |
| 32 |       Format      | `dc_format_s`            | `dct_format_s`         |           new namespace           |
| 33 |     File Size     |                          | `gbl_fileSize_s`       |             new field             |
| 34 |   WxS Identifier  | `layer_id_s`             | `gbl_wxsIdentifier_s`  |            new URI name           |
| 35 |     References    | `dct_references_s`       | `dct_references_s`     |             no change             |
| 36 |         ID        | `layer_slug_s`           | `id`                   |            new URI name           |
| 37 |     Identifier    | `dc_identifier_s`        | `dct_identifier_sm`    |new namespace; single to multi-valued |
| 38 |      Modified     | `layer_modified_dt`      | `gbl_mdModified_dt`    |            new URI name           |
| 39 |  Metadata Version | `geoblacklight_version`  | `gbl_mdVersion_s`      |            new URI name           |
| 40 |     Suppressed    | `suppressed_b`           | `gbl_suppressed_b`     |           new namespace           |
| 41 |   Georeferenced   |                          | `gbl_georeferenced_b`  |             new field             |

### Elements without a crosswalk
{: .no_toc }

There are three elements in GBL 1.0 that do not directly translate into OGM Aardvark. While they have been replaced with similar fields in OGM Aardvark, the **values themselves** would need to be altered during crosswalking.

**Type (dc_type_s)**
* GBL 1.0 Description: This single-valued GBL 1.0 field observes the Dublin Core controlled vocabulary for Type, including Dataset, Image, Collection, Interactive Resource, or Physical Object.
* Similar Aardvark element: This has been replaced in Aardvark with the multi-valued [Resource Class](../aardvarkSchema/resource-class/), which uses a custom controlled vocabulary of Collections, Datasets, Imagery, Maps, Web Services, and/or Other.

**Geometry Type (layer_geom_type_s)**
* GBL 1.0 Description: This single-valued GBL 1.0 field differentiates between vector (Point, Line, Polygon), raster (Raster, Image), non-spatial formats (Table), or a combination (Mixed).
* Similar Aardvark element: This has been replaced in Aardvark with the multi-valued [Resource Type](../aardvarkSchema/resource-type/), which uses a controlled vocabulary drawn from Library of Congress cartographic genres and GIS geometries.

**Is Part Of (dct_isPartOf_sm)**
* GBL 1.0 Description: This multi-valued GBL 1.0 plain text field is for writing out the name of a collection. Example: `dct_isPartOf_sm:"Village Maps of India"`
* Similar Aardvark element: The URI is the same in Aardvark, but it is now a non-literal field. The value must be one or more IDs that reference another record within the system. Example: `dct_isPartOf_sm:"princeton-z603r079s"`

## Will Aardvark work with my GeoBlacklight installation?

You will need to upgrade to at least GeoBlacklight version 3.3 to test out Aardvark. All previously hardcoded field names were removed in GeoBlacklight version 3.3 (see [this pull request](https://github.com/geoblacklight/geoblacklight/pull/1020) for more information). This means that field names are defined in the `settings.yml` file and can be configured to use Aardvark. However, only the fields in the crosswalk will have display, facet, or other functionality enabled by default in version 3.3.

Some of the new fields in Aardvark will be tied to default application functionality beginning with Version 4.0. We plan to include item relation widgets for the new relationships (such as **Member Of** and **Is Version Of**) and reorganize the facets to include the new categories (such as Resource Class and Resource Type).
