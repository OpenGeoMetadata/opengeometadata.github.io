---
layout: default
title: Aardvark Schema
nav_order: 3
has_children: true
permalink: /docs/aardvarkSchema
---

# Aardvark Schema

Overview of the GeoBlacklight Metadata Schema, Version Aardvark
{: .fs-6 .fw-300 }


## List of Fields

| Aardvark-id | Label                            | URI                    | Obligation  |
|:---|:------------------------------------------|:-----------------------|:------------|
| 01 | **[Title](https://opengeometadata.github.io/docs/aardvarkSchema/title)** | `dct_title_s` | Required |
| 02 | [Alternative Title](#alternative-title)   | `dct_alternative_sm`   | Optional    |
| 03 | [Description](#description)              | `dct_description_sm`   | Recommended |
| 04 | [Language](#language)                    | `dct_language_sm`      | Optional    |
| 05 | [Creator](#creator)                      | `dct_creator_sm`       | Recommended |
| 06 | [Publisher](#publisher)                  | `dct_publisher_sm`     | Recommended |
| 07 | [Provider](#provider)                    | `schema_provider_s`    | Recommended |
| 08 | **[Resource Class](#resource-class)**    | `gbl_resourceClass_sm` | Required    |
| 09 | [Resource Type](#resource-type)          | `gbl_resourceType_sm`  | Recommended |
| 10 | [Subject](#subject)                       | `dct_subject_sm`       | Optional    |
| 11 | [ISO Topic Category](#iso-topic-category) | `dcat_theme_sm`        | Optional    |
| 12 | [Keyword](#keyword)                       | `dcat_keyword_sm`      | Optional    |
| 13 | [Temporal Coverage](#temporal-coverage)   | `dct_temporal_sm`      | Recommended |
| 14 | [Date Issued](#date-issued)               | `dct_issued_s`         | Optional    |
| 15 | [Index Year](#index-year)                 | `gbl_indexYear_im`     | Recommended |
| 16 | [Date Range](#date-range)                 | `gbl_dateRange_drsim`  | Optional    |
| 17 | [Spatial Coverage](#spatial-coverage)     | `dct_spatial_sm`       | Recommended |
| 18 | [Spatial Extent](#spatial-extent)         | `locn_geometry`        | Recommended |
| 19 | [Centroid](#centroid)                     | `dcat_centroid_ss`     | Optional    |
| 20 | [Relation](#relation)                     | `dct_relation_sm`      | Optional    |
| 21 | [Member Of](#member-of)                   | `pcdm_memberOf_sm`     | Optional    |
| 22 | [Is Part Of](#is-part-of)                 | `dct_isPartOf_sm`      | Optional    |
| 23 | [Source](#source)                         | `dct_source_sm`        | Optional    |
| 24 | [Is Version Of](#is-version-of)           | `dct_isVersionOf_sm`   | Optional    |
| 25 | [Replaces](#replaces)                     | `dct_replaces_sm`      | Optional    |
| 26 | [Is Replaced By](#is-replaced-by)         | `dct_isReplacedBy_sm`  | Optional    |
| 27 | [Rights](#rights)                         | `dct_rights_sm`        | Recommended |
| 28 | [Rights Holder](#rights-holder)           | `dct_rightsHolder_sm`  | Optional    |
| 29 | [License](#license)                       | `dct_license_sm`       | Optional    |
| 30 | **[Access Rights](#access-rights)**       | `dct_accessRights_s`   | Required    |
| 31 | [Format](#format)                         | `dct_format_s`         | Conditional |
| 32 | [File Size](#file-size)                   | `gbl_fileSize_s`       | Optional    |
| 33 | [WxS Identifier](#wxs-identifier)         | `gbl_wxsIdentifier_s`  | Conditional |
| 34 | [References](#references)                 | `dct_references_s`     | Recommended |
| 35 | **[ID](#id)**                             | `id`                   | Required    |
| 36 | [Identifier](#identifier)                 | `dct_identifier_sm`    | Recommended |
| 37 | **[Modified](#modified)**                 | `gbl_mdModified_dt`    | Required    |
| 38 | **[Metadata Version](#metadata-version)** | `gbl_mdVersion_s`      | Required    |
| 39 | [Suppressed](#suppressed)                 | `gbl_suppressed_b`     | Optional    |
| 40 | [Georeferenced](#georeferenced)           | `gbl_georeferenced_b`  | Optional    |




## Keyword

| Label                 | Keyword                                                                                                                                                                                                                       |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 12                                                                                                                                                                                                                            |
| URI                   | `dcat_keyword_sm`                                                                                                                                                                                                               |
| Obligation            | Optional                                                                                                                                                                                                                      |
| Multiplicity          | 0-*                                                                                                                                                                                                                           |
| Field type            | string                                                                                                                                                                                                                        |
| Purpose               | To improve search results with hidden free text tags and to give administrators a field for internal tags                                                                                                                     |
| Entry Guidelines      | Enter tags that will be useful for enhancing searches and interpretation. Keywords will be in the metadata, but will be hidden to the user by default.                                                                        |
| Commentary            | These may be used for administrative purposes or to facilitate text seaching without cluttering a facet or interface. They may be helpful for grouping items by an accession code or for alternate spellings of common terms. |
| Controlled Vocabulary | no                                                                                                                                                                                                                            |
| Example value         | covid19                                                                                                                                                                                                                       |
| Element Set           | DCAT                                                                                                                                                                                                                          |
| Group                 | Categories                                                                                                                                                                                                                    |


## Temporal Coverage

| Label                 | Temporal Coverage                                                                                                                                                                                                                                                    |
|:-----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 13                                                                                                                                                                                                                                                                   |
| URI                   | `dct_temporal_sm`                                                                                                                                                                                                                                                      |
| Obligation            | Recommended                                                                                                                                                                                                                                                          |
| Multiplicity          | 0-*                                                                                                                                                                                                                                                                  |
| Field type            | string                                                                                                                                                                                                                                                               |
| Purpose               | To provide the user with a free text description of the time period or ranges of what is depicted in the resource                                                                                                                                                    |
| Entry Guidelines      | This is a text string and can indicate uncertainty                                                                                                                                                                                                                   |
| Commentary            | The `dct_temporal_sm` field is multi-valued, so multiple strings can be used to indicate the time period the resource depicts, when the data was collected, and/or when the resources was created. Examples include: “approximately 1910”, “1800-1805”, “before 2000”. |
| Controlled Vocabulary | no                                                                                                                                                                                                                                                                   |
| Example value         | 1980-1995                                                                                                                                                                                                                                                            |
| Element Set           | DCMI                                                                                                                                                                                                                                                                 |
| Group                 | Temporal                                                                                                                                                                                                                                                             |

## Date Issued

| Label                 | Date Issued                                                                                                                                                                                                                                                                                                           |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 14                                                                                                                                                                                                                                                                                                                    |
| URI                   | `dct_issued_s`                                                                                                                                                                                                                                                                                                          |
| Obligation            | Optional                                                                                                                                                                                                                                                                                                              |
| Multiplicity          | 0-1                                                                                                                                                                                                                                                                                                                   |
| Field type            | string                                                                                                                                                                                                                                                                                                                |
| Purpose               | To provide the user of when an item was published and for administrators to determine the age of the resource                                                                                                                                                                                                         |
| Entry Guidelines      | A single year is the preferred format. For more precide dates, use the ISO format without the time value: YYYY-MM-DD or YYYY-MM.                                                                                                                                                                                      |
| Commentary            | Although the `dct_issued_s` field is optional, it is often useful when a clear Temporal Coverage value is not present. For example, one may want to preserve a dataset with an uncertain lineage, but there is an indicator on a data portal on the date of last update. In most cases, the 4 digit year is sufficient. |
| Controlled Vocabulary | no                                                                                                                                                                                                                                                                                                                    |
| Example value         | 1999                                                                                                                                                                                                                                                                                                                  |
| Element Set           | DCMI                                                                                                                                                                                                                                                                                                                  |
| Group                 | Temporal                                                                                                                                                                                                                                                                                                              |

## Index Year

| Label                 | Index Year                                                    |
|:-----------------------|:---------------------------------------------------------------|
| Aardvark-id           | 15                                                            |
| URI                   | `gbl_indexYear_im`                                              |
| Obligation            | Recommended                                                   |
| Multiplicity          | 1-*                                                           |
| Field type            | integer                                                       |
| Purpose               | To power time sliders widgets that rely on integers for dates |
| Entry Guidelines      | Enter one or more 4 digit integers                            |
| Commentary            |                                                               |
| Controlled Vocabulary | no                                                            |
| Example value         | 1980,1981,1982                                                |
| Element Set           | GBL                                                           |
| Group                 | Temporal                                                      |

## Date Range

| Label                 | Date Range                                                                                         |
|:-----------------------|:----------------------------------------------------------------------------------------------------|
| Aardvark-id           | 16                                                                                                 |
| URI                   | `gbl_dateRange_drsim`                                                                                |
| Obligation            | Optional                                                                                           |
| Multiplicity          | 0-*                                                                                                |
| Field type            | date-range                                                                                         |
| Purpose               | To power other time widgets that use a date range                                                  |
| Entry Guidelines      | Enter a start date and end date in the Solr daterange field convention: [YYYY to YYYY]             |
| Commentary            | This field is not yet supported by GeoBlacklight, but the application can be customized to use it. |
| Controlled Vocabulary | no                                                                                                 |
| Example value         | [1980 TO 1995]                                                                                     |
| Element Set           | GBL                                                                                                |
| Group                 | Temporal                                                                                           |


## Spatial Coverage

| Label                 | Spatial Coverage                                                                                                                                                                                       |
|:-----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 17                                                                                                                                                                                                     |
| URI                   |`dct_spatial_sm`                                                                                                                                                                                         |
| Obligation            | Recommended                                                                                                                                                                                            |
| Multiplicity          | 0-*                                                                                                                                                                                                    |
| Field type            | string                                                                                                                                                                                                 |
| Purpose               | To provide the user with a list of searchable and selectable place names                                                                                                                               |
| Entry Guidelines      | Place name text strings should be specified out to the nation level. It is typical for the place name to represent the largest extent the data layer represents. Our recommended thesaurus is GeoNames |
| Commentary            | It is recommended to have at least one place name for each layer that corresponds to the logical extent of the area of that layer.                                                                     |
| Controlled Vocabulary | no                                                                                                                                                                                        |
| Example value         | Philadelphia, Pennsylvania, United States                                                                                                                                                              |
| Element Set           | DCMI                                                                                                                                                                                                   |
| Group                 | Spatial                                                                                                                                                                                                |

## Spatial Extent

| Label                 | Spatial Extent                                                                                                         |
|:--------------------- |:---------------------------------------------------------------------------------------------------------------------- |
| Aardvark-id           | 18                                                                                                                     |
| URI                   | `locn_geometry`                                                                                                         |
| Obligation            | Recommended                                                                                                            |
| Multiplicity          | 0-*                                                                                                                   |
| Field type            | string                                                                                                                 |
| Purpose               | To display the extent of the resource and to power the map search. This may be a bounding box or more complex geometry |
| Entry Guidelines      | For a bounding box, it should be in this format: ENVELOPE(w,e,n,s)                                                     |
| Commentary            | This field can support bounding boxes or complex geometries.                                                           |
| Controlled Vocabulary | no                                                                                                                     |
| Example value         | For bounding boxes: ENVELOPE(-97.251,-90.9229,49.3788,43.4649)<br>For geometries:                                      |
| Element Set           | LOCN/DCAT                                                                                                              |
| Group                 | Spatial                                                                                                                |

## Centroid

| Label                 | Centroid                                                                                    |
|:-----------------------|:---------------------------------------------------------------------------------------------|
| Aardvark-id           | 19                                                                                          |
| URI                   | `dcat_centroid_ss`                                                                            |
| Obligation            | Optional                                                                                    |
| Multiplicity          | 0-1                                                                                         |
| Field type            | string                                                                                      |
| Purpose               | To display the center point of a resource or otherwise a geotagged point on a map           |
| Entry Guidelines      | Enter two decimal degree coordinates separated by a comma in this order: longitude,latitude |
| Commentary            | This field is currently only supported by customizations to the GeoBlacklight application.  |
| Controlled Vocabulary | no                                                                                          |
| Example value         | 46.4218,-94.087                                                                             |
| Element Set           | DCAT                                                                                        |
| Group                 | Spatial                                                                                     |

## Relation

| Label                 | Relation                                                             |
|:-----------------------|:----------------------------------------------------------------------|
| Aardvark-id           | 20                                                                   |
| URI                   | `dct_relation_sm`                                                      |
| Obligation            | Optional                                                             |
| Multiplicity          | 0-*                                                                  |
| Field type            | string                                                               |
| Purpose               | To link items with a general, unspecified relationship to each other |
| Entry Guidelines      | Enter only the ID of the related item(s)                             |
| Commentary            |                                                                      |
| Controlled Vocabulary | no                                                                   |
| Example value         |                                                                      |
| Element Set           | DCMI                                                                 |
| Group                 | Relations                                                            |

## Member Of

| Label                 | Member Of                                                                                        |
|:-----------------------|:--------------------------------------------------------------------------------------------------|
| Aardvark-id           | 21                                                                                               |
| URI                   | `pcdm_memberOf_sm`                                                                                 |
| Obligation            | Optional                                                                                         |
| Multiplicity          | 0-*                                                                                              |
| Field type            | string                                                                                           |
| Purpose               | To link items that are part of a collection                                                      |
| Entry Guidelines      | Make a collection record to group records together. Enter the ID of the Collection level record. |
| Commentary            |                                                                                                  |
| Controlled Vocabulary | no                                                                                               |
| Example value         |                                                                                                  |
| Element Set           | PCDM                                                                                             |
| Group                 | Relations                                                                                        |

## Is Part Of

| Label                 | Is Part Of                                                                                        |
| :--------------------- | :------------------------------------------------------------------------------------------------- |
| Aardvark-id           | 22                                                                                                |
| URI                   | `dct_isPartOf_sm`                                                                                 |
| Obligation            | Optional                                                                                          |
| Multiplicity          | 0-\*                                                                                              |
| Field type            | string                                                                                            |
| Purpose               | To link items that are a subset of another item (ex. page in a book)                              |
| Entry Guidelines      | <br><br>Make a parent record to group records together. Enter the ID of the parent record(s).<br> |
| Commentary            |                                                                                                   |
| Controlled Vocabulary | no                                                                                                |
| Example value         |                                                                                                   |
| Element Set           | DCMI                                                                                              |
| Group                 | Relations                                                                                         |


## Source

| Label                 | Source                                                                                               |
|:-----------------------|:------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 23                                                                                                   |
| URI                   | `dct_source_sm`                                                                                        |
| Obligation            | Optional                                                                                             |
| Multiplicity          | 0-*                                                                                                  |
| Field type            | string                                                                                               |
| Purpose               | To link items that have been derived from another item (ex. digitized shapefile from historical map) |
| Entry Guidelines      | Enter the ID of the item(s) that the resource was derived from                                       |
| Commentary            |                                                                                                      |
| Controlled Vocabulary | no                                                                                                   |
| Example value         |                                                                                                      |
| Element Set           | DCMI                                                                                                 |
| Group                 |                                                                                                      |


## Is Version Of

| Label                 | Version                                                                                                                                        |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 24                                                                                                                                             |
| URI                   | `dct_isVersionOf_sm`                                                                                                                             |
| Obligation            | Optional                                                                                                                                       |
| Multiplicity          | 0-*                                                                                                                                            |
| Field type            | string                                                                                                                                         |
| Purpose               | To indicate that an item is part of a series of resources that are updated or altered and to provide a link to a different variant or adaption |
| Entry Guidelines      | Enter the ID of the most recent related record OR create a parent record to group versions together.                                           |
| Commentary            |                                                                                                                                                |
| Controlled Vocabulary | no                                                                                                                                             |
| Example value         |                                                                                                                                                |
| Element Set           | DCMI                                                                                                                                           |
| Group                 | Relations                                                                                                                                      |


## Replaces

| Label                 | Replaces                                                                                                                                                                                                                                                                                                        |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 25                                                                                                                                                                                                                                                                                                              |
| URI                   | `dct_replaces_sm`                                                                                                                                                                                                                                                                                                 |
| Obligation            | Optional                                                                                                                                                                                                                                                                                                        |
| Multiplicity          | 0-*                                                                                                                                                                                                                                                                                                             |
| Field type            | string                                                                                                                                                                                                                                                                                                          |
| Purpose               | To point user to deprecated item                                                                                                                                                                                                                                                                                |
| Entry Guidelines      | Enter the ID of the deprecated related item(s)                                                                                                                                                                                                                                                                  |
| Commentary            | Replaces and Is Replaced By can be used for a revised version of a research dataset where the original is needed for reference. For example, if the original dataset has already been cited somewhere, it can be retained in a repository with a clear indication that it has been superceded by a new version. |
| Controlled Vocabulary | no                                                                                                                                                                                                                                                                                                              |
| Example value         |                                                                                                                                                                                                                                                                                                                 |
| Element Set           | DCMI                                                                                                                                                                                                                                                                                                            |
| Group                 | Relations                                                                                                                                                                                                                                                                                                       |


#Is Replaced By

| Label                 | Is Replaced By                                                                                                                                                                                                                                                                                                  |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 26                                                                                                                                                                                                                                                                                                              |
| URI                   | `dct_isReplacedBy_sm`                                                                                                                                                                                                                                                                                             |
| Obligation            | Optional                                                                                                                                                                                                                                                                                                        |
| Multiplicity          | 0-*                                                                                                                                                                                                                                                                                                             |
| Field type            | string                                                                                                                                                                                                                                                                                                          |
| Purpose               | To point user to new item                                                                                                                                                                                                                                                                                       |
| Entry Guidelines      | Enter the ID of the related item(s) that should be used instead.                                                                                                                                                                                                                                                |
| Commentary            | Replaces and Is Replaced By can be used for a revised version of a research dataset where the original is needed for reference. For example, if the original dataset has already been cited somewhere, it can be retained in a repository with a clear indication that it has been superceded by a new version. |
| Controlled Vocabulary | no                                                                                                                                                                                                                                                                                                              |
| Example value         |                                                                                                                                                                                                                                                                                                                 |
| Element Set           | DCMI                                                                                                                                                                                                                                                                                                            |
| Group                 | Relations                                                                                                                                                                                                                                                                                                       |


## Rights

| Label                 | Rights                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 27                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| URI                   | `dct_rights_sm`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Obligation            | Recommended                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Multiplicity          | 0-*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Field type            | string                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Purpose               | To provide a free text field for rights information, such as usage, access, or copyright                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Entry Guidelines      | Enter free text of generic, catch-all access and usage rights. It can include clickable links; all access and usage rights.                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Commentary            | This field is intended to be flexible to accommodate different types of rights and disclaimers. Users are encouraged to adopt one of the rightsstatements.org statements.                                                                                                                                                                                                                                                                                                                                                                                 |
| Controlled Vocabulary | no                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Example value         | All data is copyrighted by China Data Center and/or its suppliers. Derived works that include the source data must be merged with other value-added data in such a way that the derived work cannot be converted back to the original source data format. This data is licensed by UC Berkeley for research, educational, and other non-commercial use by authorized users, which include persons affiliated with UC Berkeley and walk-in users who must access the data in person at the library. https://rightsstatements.org/page/InC/1.0/?language=en |
| Element Set           | DCMI                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Group                 | Rights                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |


## Rights Holder

| Label                 | Rights Holder                                                                                                                                                                                                              |
|:-----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 28                                                                                                                                                                                                                         |
| URI                   | `dct_rightsHolder_sm`                                                                                                                                                                                                        |
| Obligation            | Optional                                                                                                                                                                                                                   |
| Multiplicity          | 0-*                                                                                                                                                                                                                        |
| Field type            | string                                                                                                                                                                                                                     |
| Purpose               | To clarify which person or organization owns or controls the rights for this version of the item                                                                                                                           |
| Entry Guidelines      | Enter the name of the person or organization. If applicable, the suggested controlled vocabulary is the Library of Congress Name Authority File                                                                            |
| Commentary            | This can be used for instances in which an an organization owns a digital copy of an analog resource or otherwise controls access. This is different that Provider, which refers more to the resource or metadata steward. |
| Controlled Vocabulary | no                                                                                                                                                                                                                         |
| Example value         | Johns Hopkins University Libraries                                                                                                                                                                                         |
| Element Set           | DCMI                                                                                                                                                                                                                       |
| Group                 | Rights                                                                                                                                                                                                                     |


## License

| Label                 | License                                                                                                                                     |
|:-----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 29                                                                                                                                          |
| URI                   | `dct_license_sm`                                                                                                                              |
| Obligation            | Optional                                                                                                                                    |
| Multiplicity          | 0-*                                                                                                                                         |
| Field type            | string                                                                                                                                      |
| Purpose               | To provide URI links to specific, known licenses                                                                                            |
| Entry Guidelines      | Enter only a URI. Recommended sources are https://creativecommons.org or https://opendatacommons.org/                                       |
| Commentary            | This field is only for URIs of known licenses. Do not enter a rightsstatement.org statement here, because those belong in the Rights field. |
| Controlled Vocabulary | no                                                                                                                                          |
| Example value         | https://creativecommons.org/licenses/by/4.0/                                                                                                |
| Element Set           | DCMI                                                                                                                                        |
| Group                 | Rights                                                                                                                                      |


## Access Rights

| Label                 | Access Rights                                                                                                                                                                                                                                    |
|:-----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 30                                                                                                                                                                                                                                               |
| URI                   | `dct_accessRights_s`                                                                                                                                                                                                                               |
| Obligation            | Required                                                                                                                                                                                                                                         |
| Multiplicity          | 1-1                                                                                                                                                                                                                                              |
| Field type            | string                                                                                                                                                                                                                                           |
| Purpose               | To clarify to the user if the resource is public (any user can access) or restricted (a user will need to log in to some kind of authentication protocol) and if the application should provide a web service preview and/or a download function |
| Entry Guidelines      | Only one of two values are allowed: Public or Restricted                                                                                                                                                                                         |
| Commentary            | This field can be set to "Public", which allows users to view and download an item, or "Restricted", which requires a user to log in to an authentication service.                                                                               |
| Controlled Vocabulary | yes - strict                                                                                                                                                                                                                                     |
| Example value         | Public                                                                                                                                                                                                                                           |
| Element Set           | DCMI                                                                                                                                                                                                                                             |
| Group                 | Rights                                                                                                                                                                                                                                           |


## Format

| Label                 | Format                                                                                                                                                                                                                                                                                        |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 31                                                                                                                                                                                                                                                                                            |
| URI                   | `dct_format_s`                                                                                                                                                                                                                                                                                  |
| Obligation            | Conditional                                                                                                                                                                                                                                                                                   |
| Multiplicity          | 0-1 or 1-1                                                                                                                                                                                                                                                                                    |
| Field type            | string                                                                                                                                                                                                                                                                                        |
| Purpose               | To display to the user the name of the file type as a text string in the Download button                                                                                                                                                                                                      |
| Entry Guidelines      | if download URL is configured as a single key:value pair                                                                                                                                                                                                                                      |
| Commentary            | A long list of formats is available here. The most important thing to remember about the dc_format_s field is that it is required for Download functionality if using a single value string for downloads. (pre-GeoBlacklight version 3.0). See the Multiple Downloads guide for more details |
| Controlled Vocabulary | yes-not strict                                                                                                                                                                                                                                                                                |
| Example value         | Shapefile                                                                                                                                                                                                                                                                                     |
| Element Set           | DCMI                                                                                                                                                                                                                                                                                          |
| Group                 | Distribution                                                                                                                                                                                                                                                                                  |


## File Size

| Label                 | File Size                                                                                                                                                   |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 32                                                                                                                                                          |
| URI                   | `gbl_fileSize_s`                                                                                                                                              |
| Obligation            | Optional                                                                                                                                                    |
| Multiplicity          | 0-1                                                                                                                                                         |
| Field type            | string                                                                                                                                                      |
| Purpose               | To inform the user of the size of the file download                                                                                                         |
| Entry Guidelines      | Enter the size in megabytes                                                                                                                                 |
| Commentary            | This field is intended to give users a sense of how large the data or image they are interested in downloading, and serves to alert users about huge files. |
| Controlled Vocabulary | no                                                                                                                                                          |
| Example value         | 25.96 MB                                                                                                                                                    |
| Element Set           | GBL                                                                                                                                                         |
| Group                 | Distribution                                                                                                                                                |


## WxS Identifier
| Label                 | WxS Identifier                                                                                                                                                        |
|:----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 33                                                                                                                                                                    |
| URI                   | `gbl_wxsIdentifier_s`                                                                                                                                                   |
| Obligation            | Conditional                                                                                                                                                           |
| Multiplicity          | 0-1 or 1-1                                                                                                                                                            |
| Field type            | string                                                                                                                                                                |
| Purpose               | To identify the layer or store for a WFS, WMS, or WCS web service so the application can construct the full web service link                                          |
| Entry Guidelines      | Only the layer name is added here. The base service endpoint URLs (e.g. "https://maps-public.geo.nyu.edu/geoserver/sdr/wms") are added to the dct_references_s field. |
| Commentary            | The WxS Indentifer is used to point to specific layers within an OGC geospatial web service. This field is not used for ArcGIS Rest Services.                         |
| Controlled Vocabulary | no                                                                                                                                                                    |
| Example value         | druid:vr593vj7147                                                                                                                                                     |
| Element Set           | GBL                                                                                                                                                                   |
| Group                 | Distribution                                                                                                                                                          |


## References

| Label                 | References                                                                                                                                                                                                                       |
|:-----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 34                                                                                                                                                                                                                               |
| URI                   | `dct_references_s`                                                                                                                                                                                                                 |
| Obligation            | Recommended                                                                                                                                                                                                                      |
| Multiplicity          | 0-1                                                                                                                                                                                                                              |
| Field type            | string JSON                                                                                                                                                                                                                      |
| Purpose               | To provide external URLs for accessing or describing the resource                                                                                                                                                                |
| Entry Guidelines      | The field dct_references_s defines external services and references using the CatInterOp approach. The field value is a serialized JSON array of key/value pairs, with keys representing XML namespace URI's and values the URL. |
| Commentary            | All of the external links for the resource are added to the dct_references_s field as a serialized JSON array of key/value pairs. The download key/value pair is unique, because the value can be an array.                      |
| Controlled Vocabulary | no                                                                                                                                                                                                                               |
| Example value         | "dct_references_s": "{\"http://schema.org/url\":\"http://purl.stanford.edu/bm662dm5913\",\"http://schema.org/downloadUrl\":\"http://stacks.stanford.edu/file/druid:bm662dm5913/data.zip\"}"                                      |
| Element Set           | DCMI                                                                                                                                                                                                                             |
| Group                 | Distribution                                                                                                                                                                                                                     |


## ID

| Label                 | ID                                                                                                                                                                                                           |
|:-----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 35                                                                                                                                                                                                           |
| URI                   | `id`                                                                                                                                                                                                           |
| Obligation            | Required                                                                                                                                                                                                     |
| Multiplicity          | 1-1                                                                                                                                                                                                          |
| Field type            | string                                                                                                                                                                                                       |
| Purpose               | To provide a unique alpha-numberic ID for the item that will act as the primary key in Solr and to create a unique landing page for the item                                                                 |
| Entry Guidelines      | This string must be a globally unique value. The value should be alpha-numeric characters separated by dashes.                                                                                               |
| Commentary            | The ID makes up the URL for the resource in GeoBlacklight. If having a readable slug is desired, it is common to use the form, institution-keyword1-keyword2 (words or characters are separated by hyphens). |
| Controlled Vocabulary | no                                                                                                                                                                                                           |
| Example value         | princeton-rv042w38t                                                                                                                                                                                          |
| Element Set           | GBL                                                                                                                                                                                                          |
| Group                 | Administrative                                                                                                                                                                                               |


## Identifier

| Label                 | Identifier                                                                                                                                                                                                                                                                                                                                                                                               |
|:-----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 36                                                                                                                                                                                                                                                                                                                                                                                                       |
| URI                   | `dct_identifier_sm`                                                                                                                                                                                                                                                                                                                                                                                        |
| Obligation            | Recommended                                                                                                                                                                                                                                                                                                                                                                                              |
| Multiplicity          | 0-*                                                                                                                                                                                                                                                                                                                                                                                                      |
| Field type            | string                                                                                                                                                                                                                                                                                                                                                                                                   |
| Purpose               | To provide a general purpose field for identifiers                                                                                                                                                                                                                                                                                                                                                       |
| Entry Guidelines      | This may include a DOI, catalog number, and/or other system number                                                                                                                                                                                                                                                                                                                                       |
| Commentary            | This field is not displayed in the interface. At least one value would ideally a persistent identifier or permalink (such as a [PURL (https://en.wikipedia.org/wiki/Persistent_uniform_resource_locator) or Handle (https://en.wikipedia.org/wiki/Handle_System). Additional values can be for other identifiers used by the resource, such as the call number, OCLC number, or other system identifier. |
| Controlled Vocabulary | no                                                                                                                                                                                                                                                                                                                                                                                                       |
| Example value         | 5864 .L7 E635 1998 .G7                                                                                                                                                                                                                                                                                                                                                                                   |
| Element Set           | DCMI                                                                                                                                                                                                                                                                                                                                                                                                     |
| Group                 | Administrative                                                                                                                                                                                                                                                                                                                                                                                           |


## Modified

| Label                 | Modified                                                                                  |
|:-----------------------|:-------------------------------------------------------------------------------------------|
| Aardvark-id           | 37                                                                                        |
| URI                   | `gbl_mdModified_dt`                                                                         |
| Obligation            | Required                                                                                  |
| Multiplicity          | 0-1                                                                                       |
| Field type            | date-time                                                                                 |
| Purpose               | To inform administrators of when the metadata was last touched                            |
| Entry Guidelines      | Use the XML Schema dateTime format (YYYY-MM-DDThh:mm:ssZ)                                 |
| Commentary            | This value should indicate when the metadata (not the resource itself) was last modified. |
| Controlled Vocabulary | no                                                                                        |
| Example value         | 2015-01-01T12:00:00Z                                                                      |
| Element Set           | GBL                                                                                       |
| Group                 | Administrative                                                                            |


## Metadata Version

| Label                 | Metadata Version                                                                 |
|:-----------------------|:----------------------------------------------------------------------------------|
| Aardvark-id           | 38                                                                               |
| URI                   | `gbl_mdVersion_s`                                                                  |
| Obligation            | Required                                                                         |
| Multiplicity          | 1-1                                                                              |
| Field type            | string                                                                           |
| Purpose               | To clarify which GeoBlacklight metadata schema is being used                     |
| Entry Guidelines      | Enter the string: Aardvark                                                       |
| Commentary            | There have been two metadata schema versions for GeoBlacklight: 1.0 and Aardvark |
| Controlled Vocabulary | yes -strict                                                                      |
| Example value         | Aardvark                                                                         |
| Element Set           | GBL                                                                              |
| Group                 | Administrative                                                                   |


## Suppressed

| Label                 | Suppressed                                                                                                                                                                              |
|:-----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 39                                                                                                                                                                                      |
| URI                   | `gbl_suppressed_b`                                                                                                                                                                        |
| Obligation            | Optional                                                                                                                                                                                |
| Multiplicity          | 0-1                                                                                                                                                                                     |
| Field type            | string boolean                                                                                                                                                                          |
| Purpose               | To hide items from users in the search results. If set to True, the record will not appear in search results. It is still accessible from the Data Relations widget and via direct URL. |
| Entry Guidelines      | Only one of two values are allowed: true or false                                                                                                                                       |
| Commentary            | This field is useful for multipart items with identical metadata, such as pages in an atlas or series.                                                                                  |
| Controlled Vocabulary | yes -strict                                                                                                                                                                             |
| Example value         | true                                                                                                                                                                                    |
| Element Set           | GBL                                                                                                                                                                                     |
| Group                 | Administrative                                                                                                                                                                          |


## Georeferenced

| Label                 | Georeferenced                                                                                                                                                                                                       |
|:-----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 40                                                                                                                                                                                                                  |
| URI                   | `gbl_georeferenced_b`                                                                                                                                                                                                 |
| Obligation            | Optional                                                                                                                                                                                                            |
| Multiplicity          | 0-1                                                                                                                                                                                                                 |
| Field type            | string boolean                                                                                                                                                                                                      |
| Purpose               | To indicate whether or not a scanned map or other imagery has a georeferenced version                                                                                                                               |
| Entry Guidelines      | Only one of two values are allowed: true or false                                                                                                                                                                   |
| Commentary            | This field can be a shortcut for users to find georeferenced maps. Administrators can also employ the Source field to link a paper map with its scane (e.g. a TIFF) and its georeferenced version (e.g. a GEOTIFF.) |
| Controlled Vocabulary | yes -strict                                                                                                                                                                                                         |
| Example value         | false                                                                                                                                                                                                               |
| Element Set           | GBL                                                                                                                                                                                                                 |
| Group                 | Administrative                                                                                                                                                                                                      |

---------------------------------------------
## Controlled Vocabularies

### Resource Class Vocabulary

| Collections  |
| Datasets     |
| Maps         |
| Web Services |
| Websites     |
| Other        |

### Resource Type Vocabulary

| term                                                       | source |
| ---------------------------------------------------------- | ------ |
| LiDAR                                                      | GBL    |
| Line data                                                  | GBL    |
| Mesh data                                                  | GBL    |
| Multi-spectral data                                        | GBL    |
| Oblique photographs                                        | GBL    |
| Point cloud data                                           | GBL    |
| Point data                                                 | GBL    |
| Polygon data                                               | GBL    |
| Raster data                                                | GBL    |
| Satellite imagery                                          | GBL    |
| Table data                                                 | GBL    |
| Aerial photographs                                         | LOC    |
| Aerial views                                               | LOC    |
| Aeronautical charts                                        | LOC    |
| Armillary spheres                                          | LOC    |
| Astronautical charts                                       | LOC    |
| Astronomical models                                        | LOC    |
| Atlases                                                    | LOC    |
| Bathymetric maps                                           | LOC    |
| Block diagrams                                             | LOC    |
| Bottle-charts                                              | LOC    |
| Cadastral maps                                             | LOC    |
| Cartographic materials                                     | LOC    |
| Cartographic materials for people with visual disabilities | LOC    |
| Celestial charts                                           | LOC    |
| Celestial globes                                           | LOC    |
| Census data                                                | LOC    |
| Children's atlases                                         | LOC    |
| Children's maps                                            | LOC    |
| Comparative maps                                           | LOC    |
| Composite atlases                                          | LOC    |
| Digital elevation models                                   | LOC    |
| Digital maps                                               | LOC    |
| Early maps                                                 | LOC    |
| Ephemerides                                                | LOC    |
| Ethnographic maps                                          | LOC    |
| Fire insurance maps                                        | LOC    |
| Flow maps                                                  | LOC    |
| Gazetteers                                                 | LOC    |
| Geological cross-sections                                  | LOC    |
| Geological maps                                            | LOC    |
| Globes                                                     | LOC    |
| Gores (Maps)                                               | LOC    |
| Gravity anomaly maps                                       | LOC    |
| Index maps                                                 | LOC    |
| Linguistic atlases                                         | LOC    |
| Loran charts                                               | LOC    |
| Manuscript maps                                            | LOC    |
| Mappae mundi                                               | LOC    |
| Mental maps                                                | LOC    |
| Meteorological charts                                      | LOC    |
| Military maps                                              | LOC    |
| Mine maps                                                  | LOC    |
| Miniature maps                                             | LOC    |
| Nautical charts                                            | LOC    |
| Outline maps                                               | LOC    |
| Photogrammetric maps                                       | LOC    |
| Photomaps                                                  | LOC    |
| Physical maps                                              | LOC    |
| Pictorial maps                                             | LOC    |
| Plotting charts                                            | LOC    |
| Portolan charts                                            | LOC    |
| Quadrangle maps                                            | LOC    |
| Relief models                                              | LOC    |
| Remote-sensing maps                                        | LOC    |
| Road maps                                                  | LOC    |
| Statistical maps                                           | LOC    |
| Stick charts                                               | LOC    |
| Strip maps                                                 | LOC    |
| Thematic maps                                              | LOC    |
| Topographic maps                                           | LOC    |
| Tourist maps                                               | LOC    |
| Upside-down maps                                           | LOC    |
| Wall maps                                                  | LOC    |
| World atlases                                              | LOC    |
| World maps                                                 | LOC    |
| Worm's-eye views                                           | LOC    |
| Zoning maps                                                | LOC    |


### ISO Topic Category Vocabulary
| Term                                    | Definition (from NOAA)                                                                                                                                                                                                                                                                                                                  |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Farming                                 | rearing of animals and/or cultivation of plants Examples: agriculture, irrigation, aquaculture, plantations, herding, pests and diseases affecting crops and livestock                                                                                                                                                                  |
| Biota                                   | flora and/or fauna in natural environment Examples: wildlife, vegetation, biological sciences, ecology, wilderness, sealife, wetlands, habitat                                                                                                                                                                                          |
| Boundaries                              | legal land descriptions Examples: political and administrative boundaries                                                                                                                                                                                                                                                               |
| Climatology, Meteorology and Atmosphere | processes and phenomena of the atmosphere. Examples: cloud cover, weather, climate, atmospheric conditions, climate change, precipitation                                                                                                                                                                                               |
| Economy                                 | economic activities, conditions and employment. Examples: production, labour, revenue, commerce, industry, tourism and ecotourism, forestry, fisheries, commercial or subsistence hunting, exploration and exploitation of resources such as minerals, oil and gas                                                                      |
| Elevation                               | height above or below sea level Examples: altitude, bathymetry, digital elevation models, slope, derived products                                                                                                                                                                                                                       |
| Environment                             | environmental resources, protection and conservation Examples: environmental pollution, waste storage and treatment, environmental impact assessment, monitoring environmental risk, nature reserves, landscape                                                                                                                         |
| Geoscientific Information               | information pertaining to earth sciences Examples: geophysical features and processes, geology, minerals, sciences dealing with the composition, structure and origin of the earth’s rocks, risks of earthquakes, volcanic activity, landslides, gravity information, soils, permafrost, hydrogeology, erosion                          |
| Health                                  | health, health services, human ecology, and safety Examples: disease and illness, factors affecting health, hygiene, substance abuse, mental and physical health, health services                                                                                                                                                       |
| Imagery and Base Maps                   | base maps Examples: land cover, topographic maps, imagery, unclassified images, annotations                                                                                                                                                                                                                                             |
| Intelligence and Military               | military bases, structures, activities Examples: barracks, training grounds, military transportation, information collection                                                                                                                                                                                                            |
| Inland Waters                           | inland water features, drainage systems and their characteristics Examples: rivers and glaciers, salt lakes, water utilization plans, dams, currents, floods, water quality, hydrographic charts                                                                                                                                        |
| Location                                | positional information and services Examples: addresses, geodetic networks, control points, postal zones and services, place names                                                                                                                                                                                                      |
| Oceans                                  | features and characteristics of salt water bodies (excluding inland waters) Examples: tides, tidal waves, coastal information, reefs                                                                                                                                                                                                    |
| Planning and Cadastral                  | information used for appropriate actions for future use of the land Examples: land use maps, zoning maps, cadastral surveys, land ownership                                                                                                                                                                                             |
| Society                                 | characteristics of society and cultures Examples: settlements, anthropology, archaeology, education, traditional beliefs, manners and customs, demographic data, recreational areas and activities, social impact assessments, crime and justice, census information                                                                    |
| Structure                               | man-made construction Examples: buildings, museums, churches, factories, housing, monuments, shops, towers                                                                                                                                                                                                                              |
| Transportation                          | means and aids for conveying persons and/or goods Examples: roads, airports/airstrips, shipping routes, tunnels, nautical charts, vehicle or vessel location, aeronautical charts, railways                                                                                                                                             |
| Utilities and Communication             | energy, water and waste systems and communications infrastructure and services Examples: hydroelectricity, geothermal, solar and nuclear sources of energy, water purification and distribution, sewage collection and disposal, electricity and gas distribution, data communication, telecommunication, radio, communication networks |
