---
layout: default
title: About Aardvark
nav_order: 2
---

# About Aardvark
{: .no_toc }

GeoBlacklight Metadata Schema (2021)
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introducing Aardvark

This document introduces Aardvark, the new metadata application profile schema for GeoBlacklight. This schema incorporates additional fields for better descriptions of a wider range of resources, as well as syntactical updates in order to improve interoperability between institutions and between schemas.


## Why is this called Aardvark?

The term “aardvark” represents a new naming convention to specify metadata schema versions. This convention is intended to reduce confusion between the metadata schema version and GeoBlacklight software versions, which uses numerical-based indicators.


## Why do we need an updated schema?

GeoBlacklight and its original metadata application schema (1.0) are well-suited to describing single layers of GIS data served out as OGC web services and documented with supplemental metadata, such as ISO 19115 (19139). Since that time, the growing community of GeoBlacklight adopters has introduced new use cases and institutional requirements. This growth brought several challenges to the metadata application schema as it was originally conceived including:

*   a lack of fields for statements about rights
*   a lack of clarity around how to define relationships between items
*   few options for describing other types of resources, such as scanned maps, collections, and websites
*   mandatory fields that did not have applicable values (i.e. Geometry Type)
*   single-valued fields that could have multiple values (i.e. Language, Publisher)
*   fields with names that were not intuitive for new users

The minimal nature of the original GeoBlacklight schema combined with the growing environment of customized local fields has presented obstacles for new adopters. Instead of being able to rely on the official application schema to meet all or most of their needs, they must develop local solutions. Ultimately, in order to use GeoBlacklight, many adopters implemented custom fields. [A review of extant custom fields in 2020](https://github.com/geoblacklight/geoblacklight/issues/937) revealed that at least six institutions had added or altered fields in the GeoBlacklight schema. Altogether, over 20 custom fields were in use. The result of these custom fields was metadata that was not fully interoperable across institutions. For example, three schools had implemented three different fields for indicating rights or licenses.


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

*   **URI**: This is the name we give to the metadata element itself. For example, the URI for the GeoBlacklight subject field is `dct_subject_sm`
*   **Namespace**: This is how we signify which family of standards or schemas an element belongs to. For the GeoBlacklight schema, this takes the form of the URI’s prefix. For the URI `dct_subject_sm`,  `dct_` is the prefix and signifies that this element is from Dublin Core.
*   **Solr field type**: This is the suffix appended to the URI and indicates what kind of Solr field should be indexed. For `dct_subject_sm`, the `_sm` stands for String Multiple. It indicates that the field type is a string and that it can have multiple values
*   **Value**: This is the information that is entered in a field. It may be free text (literal value) or a URI/code (nonliteral value).


## What is different about the new schema?

### New elements for Rights

One of the highest priorities for the Workgroup was to identify appropriate elements to capture rights information. This information is required at many participating institutions, and was the cause of multiple custom fields at different institutions that served the same purpose.

After examining how rights are implemented for different projects, notably the Digital Public Library of America (DPLA) and [RightsStatements.org,](https://rightsstatements.org) we recommend three new fields and a renaming of one field. This change is the one instance in which we recommend that an existing GeoBlacklight element with application functionality is replaced by another.

The new set of Rights elements are:


<table>
  <tr>
   <td><strong>Label</strong>
   </td>
   <td><strong>URI</strong>
   </td>
   <td><strong>description & entry guidelines</strong>
   </td>
  </tr>
  <tr>
   <td>Access Rights
   </td>
   <td>dct_accessRights_s
   </td>
   <td>One of two possible values, "Public" or "Restricted"; controls whether a user can preview or download an item. This element replaces dc_rights_s
   </td>
  </tr>
  <tr>
   <td>Rights
   </td>
   <td>dct_rights_sm
   </td>
   <td>Free text of generic, catch-all access and usage rights. Repeatable. Can include clickable links.
   </td>
  </tr>
  <tr>
   <td>License
   </td>
   <td>dct_license_sm
   </td>
   <td>Repeatable (or Single?) URI. Recommended sources https://creativecommons.org/licenses/by/4.0/ or https://opendatacommons.org/
   </td>
  </tr>
  <tr>
   <td>Rights Holder
   </td>
   <td>dct_rightsHolder_sm
   </td>
   <td>A person or organization owning or managing rights over the resource. Probably free text
   </td>
  </tr>
</table>


### New elements for item relations

One of the thorniest issues we tackled was how to define item relations. We identified four new relationships, redefined two, and added a general, catch-all Relation field. The value for each field should be the ID (slug) of the related item.

Currently, GeoBlacklight has an Item Relations widget that displays items identified in the Source field. We recommend that the application be updated to use the same widget for each of these fields. Note that this is additive functionality; the metadata record will still be valid in the current schema, but these relationships will not display in the interface until new development is done.

The new set of Relationship elements are:

<table>
  <tr>
   <td><strong>Label</strong>
   </td>
   <td><strong>URI</strong>
   </td>
   <td><strong>description</strong>
   </td>
  </tr>
  <tr>
   <td>Source
   </td>
   <td>dct_source_sm
   </td>
   <td>For items that have been derived from another item (ex. digitized shapefile from historical map).
   </td>
  </tr>
  <tr>
   <td>Is Part Of
   </td>
   <td>dct_isPartOf_sm
   </td>
   <td>For items that are a subset of another item (ex. page in a book). This value type is changing from free-text in Version 1.0 to an ID (slug) in the new schema.
   </td>
  </tr>
  <tr>
   <td>Member Of
   </td>
   <td>pcdm_memberOf_sm
   </td>
   <td>For items in a collection
   </td>
  </tr>
  <tr>
   <td>Replaces
   </td>
   <td>dct_replaces_sm
   </td>
   <td>To refer to an item that has been deprecated
   </td>
  </tr>
  <tr>
   <td>Is Replaced By
   </td>
   <td>dct_isReplacedBy_sm
   </td>
   <td>To point user to new item
   </td>
  </tr>
  <tr>
   <td>Version
   </td>
   <td>dct_isVersionOf_sm
   </td>
   <td>To indicate that an item is a part of a series of resources that are updated or altered
   </td>
  </tr>
  <tr>
   <td>Relation
   </td>
   <td>dct_relation_sm
   </td>
   <td>For a general purpose relation
   </td>
  </tr>
</table>


### Consistent namespaces for all metadata element URIs

The new version always gives preference to elements found in established schemas over custom fields.

*   <strong><code>dct_ :</code></strong> This signifies that the field is part of the [Dublin Core Metadata Initiative (DCMI) Metadata Terms.](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/) Any Dublin Core fields from the GeoBlacklight Schema 1.0 were updated to use the dct_ namespace.
*   <strong><code>dcat_</code></strong> : Thati signifies that the field is from the [Data Catalog Vocabulary (DCAT) Version 2.](https://www.w3.org/TR/vocab-dcat-2/)
*   <strong><code>pcdm_ </code></strong>: This refers to the [Portland Common Data Model](https://github.com/duraspace/pcdm/wiki), which is a framework for many digital repository systems. We drew from it to establish one of the item relationship fields
*   <strong><code>gbl_</code></strong> : This stands for GeoBlacklight and is for any field that is application-specific or has no analogous term in other schemas.


### Multivalued elements whenever possible

The original schema features several descriptive metadata fields that only accept one value. The new schema expands many of these to multiple. This changes the URI suffix from `_s` to` _sm`. Although it will not affect the GeoBlacklight functionality, this practice may conflict with indexing, as Solr will treat `dct_publisher_s` as a different field than `dct_publisher_sm`.


## How do I convert my Version 1.0 metadata into Aardvark?

Most of the elements from Version 1.0 can be crosswalked directly into Aardvark. The values for these elements are exactly the same; only the URI name has changed.  The following chart shows the mapping from GeoBlacklight version 1.0 into corresponding Aardvark fields. Note that this does not include all fields in either schema - only the ones that can be crosswalked.

<table>
  <tr>
   <td><strong>GBL 1.0</strong>
   </td>
   <td><strong>GBL Aardvark</strong>
   </td>
  </tr>
  <tr>
   <td><code>dc_title_s</code>
   </td>
   <td><code>dct_title_s</code>
   </td>
  </tr>
  <tr>
   <td><code>dc_description_s</code>
   </td>
   <td><code>dct_description_sm</code>
   </td>
  </tr>
  <tr>
   <td><code>dc_language_sm</code>
   </td>
   <td><code>dct_language_sm</code>
   </td>
  </tr>
  <tr>
   <td><code>dc_creator_sm</code>
   </td>
   <td><code>dct_creator_sm</code>
   </td>
  </tr>
  <tr>
   <td><code>dc_publisher_s</code>
   </td>
   <td><code>dct_publisher_sm</code>
   </td>
  </tr>
  <tr>
   <td><code>dct_provenance_s</code>
   </td>
   <td><code>schema_provider_s</code>
   </td>
  </tr>
  <tr>
   <td><code>dc_subject_sm</code>
   </td>
   <td><code>dct_subject_sm</code>
   </td>
  </tr>
  <tr>
   <td><code>dct_temporal_sm</code>
   </td>
   <td><code>dct_temporal_sm</code>
   </td>
  </tr>
  <tr>
   <td><code>dct_issued_s</code>
   </td>
   <td><code>dct_issued_s</code>
   </td>
  </tr>
  <tr>
   <td><code>solr_year_i</code>
   </td>
   <td><code>gbl_indexYear_i</code>
   </td>
  </tr>
  <tr>
   <td><code>dct_spatial_sm</code>
   </td>
   <td><code>dct_spatial_sm</code>
   </td>
  </tr>
  <tr>
   <td><code>solr_geom</code>
   </td>
   <td><code>locn_geometry</code>
   </td>
  </tr>
  <tr>
   <td><code>dc_source_sm</code>
   </td>
   <td><code>dct_source_sm</code>
   </td>
  </tr>
  <tr>
   <td><code>dc_rights_s</code>
   </td>
   <td><code>dct_accessRights_s</code>
   </td>
  </tr>
  <tr>
   <td><code>dc_format_s</code>
   </td>
   <td><code>dct_format_s</code>
   </td>
  </tr>
  <tr>
   <td><code>layer_id_s</code>
   </td>
   <td><code>gbl_wxsIdentifier_s</code>
   </td>
  </tr>
  <tr>
   <td><code>dct_references_s</code>
   </td>
   <td><code>dct_references_s</code>
   </td>
  </tr>
  <tr>
   <td><code>layer_slug_s</code>
   </td>
   <td><code>id</code>
   </td>
  </tr>
  <tr>
   <td><code>dc_identifier_s</code>
   </td>
   <td><code>dct_identifier_sm</code>
   </td>
  </tr>
  <tr>
   <td><code>layer_modified_dt</code>
   </td>
   <td><code>gbl_mdModified_dt</code>
   </td>
  </tr>
  <tr>
   <td><code>geoblacklight_version</code>
   </td>
   <td><code>gbl_mdVersion_s</code>
   </td>
  </tr>
  <tr>
   <td><code>suppressed_b</code>
   </td>
   <td><code>gbl_suppressed_b</code>
   </td>
  </tr>
</table>

The GeoBlacklight community is working to develop tools within GeoCombine that will systematically convert 1.0 metadata into Aardvark. In the meantime, [this python script can be used to batch convert json files.](https://github.com/BTAA-Geospatial-Data-Project/GBL-Schema-Update)


## Will Aardvark work with my GeoBlacklight installation?

You will need to upgrade to at least GeoBlacklight version 3.3 to test out Aardvark. [All previously hardcoded field names were removed in GeoBlacklight version 3.3.](https://github.com/geoblacklight/geoblacklight/pull/1020) This means that field names are defined in the settings.yml file and can be configured to use Aardvark. However, only the fields in the crosswalk will have display, facet, or other functionality enabled by default in version 3.3.

Some of the new fields in Aardvark will be tied to default application functionality beginning with Version 4.0. We plan to include item relation widgets for the new relationships (such as Member Of and Is Version Of) and reorganize the facets to include the new categories (such as Resource Class and Resource Type).
