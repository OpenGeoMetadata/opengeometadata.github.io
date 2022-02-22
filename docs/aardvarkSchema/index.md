---
layout: default
title: Aardvark Schema
nav_order: 4
has_children: true
has_toc: false
permalink: /docs/aardvarkSchema
---

# Aardvark Schema

Details about the Aardvark GeoBlacklight Metadata Schema (2021)
{: .fs-6 .fw-300 }


## List of Fields

| #  | Label                                                   | URI                    | Obligation  |
|:---|:--------------------------------------------------------|:-----------------------|:------------|
| 01 | **[Title](aardvarkSchema/title)**                       | `dct_title_s`          | <span class="text-red-300">**Required**</span> |
| 02 | [Alternative Title](aardvarkSchema/alternative-title)   | `dct_alternative_sm`   | Optional    |
| 03 | [Description](aardvarkSchema/description)               | `dct_description_sm`   | Recommended |
| 04 | [Language](aardvarkSchema/language)                     | `dct_language_sm`      | Optional    |
| 05 | [Creator](aardvarkSchema/creator)                       | `dct_creator_sm`       | Recommended |
| 06 | [Publisher](aardvarkSchema/publisher)                   | `dct_publisher_sm`     | Recommended |
| 07 | [Provider](aardvarkSchema/provider)                     | `schema_provider_s`    | Recommended |
| 08 | **[Resource Class](aardvarkSchema/resource-class)**     | `gbl_resourceClass_sm` | <span class="text-red-300">**Required**</span> |
| 09 | [Resource Type](aardvarkSchema/resource-type)           | `gbl_resourceType_sm`  | Recommended |
| 10 | [Subject](aardvarkSchema/subject)                       | `dct_subject_sm`       | Optional    |
| 11 | [Theme](aardvarkSchema/theme)                           | `dcat_theme_sm`        | Optional    |
| 12 | [Keyword](aardvarkSchema/keyword)                       | `dcat_keyword_sm`      | Optional    |
| 13 | [Temporal Coverage](aardvarkSchema/temporal-coverage)   | `dct_temporal_sm`      | Recommended |
| 14 | [Date Issued](aardvarkSchema/date-issued)               | `dct_issued_s`         | Optional    |
| 15 | [Index Year](aardvarkSchema/index-year)                 | `gbl_indexYear_im`     | Recommended |
| 16 | [Date Range](aardvarkSchema/date-range)                 | `gbl_dateRange_drsim`  | Optional    |
| 17 | [Spatial Coverage](aardvarkSchema/spatial-coverage)     | `dct_spatial_sm`       | Recommended |
| 18 | [Geometry](aardvarkSchema/geometry)                     | `locn_geometry`        | Recommended |
| 19 | [Bounding Box](aardvarkSchema/bounding-box)             | `dcat_bbox`            | Recommended |
| 20 | [Centroid](aardvarkSchema/centroid)                     | `dcat_centroid`        | Optional    |
| 21 | [Relation](aardvarkSchema/relation)                     | `dct_relation_sm`      | Optional    |
| 22 | [Member Of](aardvarkSchema/member-of)                   | `pcdm_memberOf_sm`     | Optional    |
| 23 | [Is Part Of](aardvarkSchema/is-part-of)                 | `dct_isPartOf_sm`      | Optional    |
| 24 | [Source](aardvarkSchema/source)                         | `dct_source_sm`        | Optional    |
| 25 | [Is Version Of](aardvarkSchema/is-version-of)           | `dct_isVersionOf_sm`   | Optional    |
| 26 | [Replaces](aardvarkSchema/replaces)                     | `dct_replaces_sm`      | Optional    |
| 27 | [Is Replaced By](aardvarkSchema/is-replaced-by)         | `dct_isReplacedBy_sm`  | Optional    |
| 28 | [Rights](aardvarkSchema/rights)                         | `dct_rights_sm`        | Recommended |
| 29 | [Rights Holder](aardvarkSchema/rights-holder)           | `dct_rightsHolder_sm`  | Optional    |
| 30 | [License](aardvarkSchema/license)                       | `dct_license_sm`       | Optional    |
| 31 | **[Access Rights](aardvarkSchema/access-rights)**       | `dct_accessRights_s`   | <span class="text-red-300">**Required**</span> |
| 32 | [Format](aardvarkSchema/format)                         | `dct_format_s`         | Conditional |
| 33 | [File Size](aardvarkSchema/file-size)                   | `gbl_fileSize_s`       | Optional    |
| 34 | [WxS Identifier](aardvarkSchema/wxs-identifier)         | `gbl_wxsIdentifier_s`  | Conditional |
| 35 | [References](aardvarkSchema/references)                 | `dct_references_s`     | Recommended |
| 36 | **[ID](aardvarkSchema/id)**                             | `id`                   | <span class="text-red-300">**Required**</span> |
| 37 | [Identifier](aardvarkSchema/identifier)                 | `dct_identifier_sm`    | Recommended |
| 38 | **[Modified](aardvarkSchema/modified)**                 | `gbl_mdModified_dt`    | <span class="text-red-300">**Required**</span> |
| 39 | **[Metadata Version](aardvarkSchema/metadata-version)** | `gbl_mdVersion_s`      | <span class="text-red-300">**Required**</span> |
| 40 | [Suppressed](aardvarkSchema/suppressed)                 | `gbl_suppressed_b`     | Optional    |
| 41 | [Georeferenced](aardvarkSchema/georeferenced)           | `gbl_georeferenced_b`  | Optional    |
