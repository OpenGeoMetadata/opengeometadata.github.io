---
layout: default
title: About OGM Aardvark
nav_exclude: true

---

# About OGM Aardvark
{: .no_toc }

Details about the OpenGeoMetadata metadata schema, OGM Aardvark
{: .fs-6 .fw-300 }


* based on [Dublin Core](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/), with custom elements added for spatial values
* designed for discovery - to help users _find_ items
* not designed for complete technical documentation, such as a GIS dataset's processing history
* includes elements for external links, such as downloads, web services, or supplemental metadata
* requires records to be formatted as JSON files
{: .feature}

OGM Aardvark is a discovery metadata schema for geospatial resources. It was intentionally developed with cross-application in mind and can be used to describe geospatial assets of all kinds.

It is also the newest metadata application profile schema for GeoBlacklight. Launched in 2021, it replaces the GeoBlacklight metadata schema version 1.0 ([GBL 1.0](gbl-1.0)). Compared to GBL 1.0, Aardvark incorporates additional fields for better descriptions of a wider range of resources, as well as syntactical updates in order to improve interoperability between institutions and between schemas. For GeoBlacklight users, it is the recommended schema for installations starting with GeoBlacklight version 4.0.

For more information, see the [Upgrade Guide.](upgrading)

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

## Will Aardvark work with my GeoBlacklight installation?

You will need to upgrade to at least GeoBlacklight version 3.3 to test out Aardvark. All previously hardcoded field names were removed in GeoBlacklight version 3.3 (see [this pull request](https://github.com/geoblacklight/geoblacklight/pull/1020) for more information). This means that field names are defined in the `settings.yml` file and can be configured to use Aardvark. However, only the fields in the crosswalk will have display, facet, or other functionality enabled by default in version 3.3.

Some of the new fields in Aardvark will be tied to default application functionality beginning with Version 4.0. We plan to include item relation widgets for the new relationships (such as **Member Of** and **Is Version Of**) and reorganize the facets to include the new categories (such as Resource Class and Resource Type).
