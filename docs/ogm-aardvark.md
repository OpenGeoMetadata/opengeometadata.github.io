---
layout: default
title: OGM Aardvark
parent: Current Schema
nav_order: 1
has_children: true
has_toc: false
---

# OGM Aardvark

OpenGeoMetadata Aardvark metadata schema (2021)
{: .fs-6 .fw-300 }


## List of Fields

| #  | Label                                                   | URI                    | Obligation  |
|:---|:--------------------------------------------------------|:-----------------------|:------------|
| 01 | **[Title](ogm-aardvark/title)**                       | `dct_title_s`          | <span class="text-red-300">**Required**</span> |
| 02 | [Alternative Title](ogm-aardvark/alternative-title)   | `dct_alternative_sm`   | Optional    |
| 03 | [Description](ogm-aardvark/description)               | `dct_description_sm`   | Recommended |
| 04 | [Language](ogm-aardvark/language)                     | `dct_language_sm`      | Optional    |
| 05 | [Creator](ogm-aardvark/creator)                       | `dct_creator_sm`       | Recommended |
| 06 | [Publisher](ogm-aardvark/publisher)                   | `dct_publisher_sm`     | Recommended |
| 07 | [Provider](ogm-aardvark/provider)                     | `schema_provider_s`    | Recommended |
| 08 | **[Resource Class](ogm-aardvark/resource-class)**     | `gbl_resourceClass_sm` | <span class="text-red-300">**Required**</span> |
| 09 | [Resource Type](ogm-aardvark/resource-type)           | `gbl_resourceType_sm`  | Recommended |
| 10 | [Subject](ogm-aardvark/subject)                       | `dct_subject_sm`       | Optional    |
| 11 | [Theme](ogm-aardvark/theme)                           | `dcat_theme_sm`        | Optional    |
| 12 | [Keyword](ogm-aardvark/keyword)                       | `dcat_keyword_sm`      | Optional    |
| 13 | [Temporal Coverage](ogm-aardvark/temporal-coverage)   | `dct_temporal_sm`      | Recommended |
| 14 | [Date Issued](ogm-aardvark/date-issued)               | `dct_issued_s`         | Optional    |
| 15 | [Index Year](ogm-aardvark/index-year)                 | `gbl_indexYear_im`     | Recommended |
| 16 | [Date Range](ogm-aardvark/date-range)                 | `gbl_dateRange_drsim`  | Optional    |
| 17 | [Spatial Coverage](ogm-aardvark/spatial-coverage)     | `dct_spatial_sm`       | Recommended |
| 18 | [Geometry](ogm-aardvark/geometry)                     | `locn_geometry`        | Recommended |
| 19 | [Bounding Box](ogm-aardvark/bounding-box)             | `dcat_bbox`            | Recommended |
| 20 | [Centroid](ogm-aardvark/centroid)                     | `dcat_centroid`        | Optional    |
| 21 | [Relation](ogm-aardvark/relation)                     | `dct_relation_sm`      | Optional    |
| 22 | [Member Of](ogm-aardvark/member-of)                   | `pcdm_memberOf_sm`     | Optional    |
| 23 | [Is Part Of](ogm-aardvark/is-part-of)                 | `dct_isPartOf_sm`      | Optional    |
| 24 | [Source](ogm-aardvark/source)                         | `dct_source_sm`        | Optional    |
| 25 | [Is Version Of](ogm-aardvark/is-version-of)           | `dct_isVersionOf_sm`   | Optional    |
| 26 | [Replaces](ogm-aardvark/replaces)                     | `dct_replaces_sm`      | Optional    |
| 27 | [Is Replaced By](ogm-aardvark/is-replaced-by)         | `dct_isReplacedBy_sm`  | Optional    |
| 28 | [Rights](ogm-aardvark/rights)                         | `dct_rights_sm`        | Recommended |
| 29 | [Rights Holder](ogm-aardvark/rights-holder)           | `dct_rightsHolder_sm`  | Optional    |
| 30 | [License](ogm-aardvark/license)                       | `dct_license_sm`       | Optional    |
| 31 | **[Access Rights](ogm-aardvark/access-rights)**       | `dct_accessRights_s`   | <span class="text-red-300">**Required**</span> |
| 32 | [Format](ogm-aardvark/format)                         | `dct_format_s`         | Conditional |
| 33 | [File Size](ogm-aardvark/file-size)                   | `gbl_fileSize_s`       | Optional    |
| 34 | [WxS Identifier](ogm-aardvark/wxs-identifier)         | `gbl_wxsIdentifier_s`  | Conditional |
| 35 | [References](ogm-aardvark/references)                 | `dct_references_s`     | Recommended |
| 36 | **[ID](ogm-aardvark/id)**                             | `id`                   | <span class="text-red-300">**Required**</span> |
| 37 | [Identifier](ogm-aardvark/identifier)                 | `dct_identifier_sm`    | Recommended |
| 38 | **[Modified](ogm-aardvark/modified)**                 | `gbl_mdModified_dt`    | <span class="text-red-300">**Required**</span> |
| 39 | **[Metadata Version](ogm-aardvark/metadata-version)** | `gbl_mdVersion_s`      | <span class="text-red-300">**Required**</span> |
| 40 | [Suppressed](ogm-aardvark/suppressed)                 | `gbl_suppressed_b`     | Optional    |
| 41 | [Georeferenced](ogm-aardvark/georeferenced)           | `gbl_georeferenced_b`  | Optional    |
