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

| Aardvark-id     | Label                  | URI                | Obligation  |
|:----------------|:-----------------------|:-------------------|:------------|
| 01 | **[Title](https://opengeometadata.github.io/docs/aardvarkSchema/title)**                       | `dct_title_s`          | <span class="text-red-300">**Required**</span> |
| 02 | [Alternative Title](https://opengeometadata.github.io/docs/aardvarkSchema/alternative-title)   | `dct_alternative_sm`   | Optional    |
| 03 | [Description](https://opengeometadata.github.io/docs/aardvarkSchema/description)               | `dct_description_sm`   | Recommended |
| 04 | [Language](https://opengeometadata.github.io/docs/aardvarkSchema/language)                     | `dct_language_sm`      | Optional    |
| 05 | [Creator](https://opengeometadata.github.io/docs/aardvarkSchema/creator)                       | `dct_creator_sm`       | Recommended |
| 06 | [Publisher](https://opengeometadata.github.io/docs/aardvarkSchema/publisher)                   | `dct_publisher_sm`     | Recommended |
| 07 | [Provider](https://opengeometadata.github.io/docs/aardvarkSchema/provider)                     | `schema_provider_s`    | Recommended |
| 08 | **[Resource Class](https://opengeometadata.github.io/docs/aardvarkSchema/resource-class)**     | `gbl_resourceClass_sm` | <span class="text-red-300">**Required**</span> |
| 09 | [Resource Type](https://opengeometadata.github.io/docs/aardvarkSchema/resource-type)           | `gbl_resourceType_sm`  | Recommended |
| 10 | [Subject](https://opengeometadata.github.io/docs/aardvarkSchema/subject)                       | `dct_subject_sm`       | Optional    |
| 11 | [ISO Topic Category](https://opengeometadata.github.io/docs/aardvarkSchema/iso-topic-category) | `dcat_theme_sm`        | Optional    |
| 12 | [Keyword](https://opengeometadata.github.io/docs/aardvarkSchema/keyword)                       | `dcat_keyword_sm`      | Optional    |
| 13 | [Temporal Coverage](https://opengeometadata.github.io/docs/aardvarkSchema/temporal-coverage)   | `dct_temporal_sm`      | Recommended |
| 14 | [Date Issued](https://opengeometadata.github.io/docs/aardvarkSchema/date-issued)               | `dct_issued_s`         | Optional    |
| 15 | [Index Year](https://opengeometadata.github.io/docs/aardvarkSchema/index-year)                 | `gbl_indexYear_im`     | Recommended |
| 16 | [Date Range](https://opengeometadata.github.io/docs/aardvarkSchema/date-range)                 | `gbl_dateRange_drsim`  | Optional    |
| 17 | [Spatial Coverage](https://opengeometadata.github.io/docs/aardvarkSchema/spatial-coverage)     | `dct_spatial_sm`       | Recommended |
| 18 | [Spatial Extent](https://opengeometadata.github.io/docs/aardvarkSchema/spatial-extent)         | `locn_geometry`        | Recommended |
| 19 | [Centroid](https://opengeometadata.github.io/docs/aardvarkSchema/centroid)                     | `dcat_centroid_ss`     | Optional    |
| 20 | [Relation](https://opengeometadata.github.io/docs/aardvarkSchema/relation)                     | `dct_relation_sm`      | Optional    |
| 21 | [Member Of](https://opengeometadata.github.io/docs/aardvarkSchema/member-of)                   | `pcdm_memberOf_sm`     | Optional    |
| 22 | [Is Part Of](https://opengeometadata.github.io/docs/aardvarkSchema/is-part-of)                 | `dct_isPartOf_sm`      | Optional    |
| 23 | [Source](https://opengeometadata.github.io/docs/aardvarkSchema/source)                         | `dct_source_sm`        | Optional    |
| 24 | [Is Version Of](https://opengeometadata.github.io/docs/aardvarkSchema/is-version-of)           | `dct_isVersionOf_sm`   | Optional    |
| 25 | [Replaces](https://opengeometadata.github.io/docs/aardvarkSchema/replaces)                     | `dct_replaces_sm`      | Optional    |
| 26 | [Is Replaced By](https://opengeometadata.github.io/docs/aardvarkSchema/is-replaced-by)         | `dct_isReplacedBy_sm`  | Optional    |
| 27 | [Rights](https://opengeometadata.github.io/docs/aardvarkSchema/rights)                         | `dct_rights_sm`        | Recommended |
| 28 | [Rights Holder](https://opengeometadata.github.io/docs/aardvarkSchema/rights-holder)           | `dct_rightsHolder_sm`  | Optional    |
| 29 | [License](https://opengeometadata.github.io/docs/aardvarkSchema/license)                       | `dct_license_sm`       | Optional    |
| 30 | **[Access Rights](https://opengeometadata.github.io/docs/aardvarkSchema/access-rights)**       | `dct_accessRights_s`   | <span class="text-red-300">**Required**</span> |
| 31 | [Format](https://opengeometadata.github.io/docs/aardvarkSchema/format)                         | `dct_format_s`         | Conditional |
| 32 | [File Size](https://opengeometadata.github.io/docs/aardvarkSchema/file-size)                   | `gbl_fileSize_s`       | Optional    |
| 33 | [WxS Identifier](https://opengeometadata.github.io/docs/aardvarkSchema/wxs-identifier)         | `gbl_wxsIdentifier_s`  | Conditional |
| 34 | [References](https://opengeometadata.github.io/docs/aardvarkSchema/references)                 | `dct_references_s`     | Recommended |
| 35 | **[ID](https://opengeometadata.github.io/docs/aardvarkSchema/id)**                             | `id`                   | <span class="text-red-300">**Required**</span> |
| 36 | [Identifier](https://opengeometadata.github.io/docs/aardvarkSchema/identifier)                 | `dct_identifier_sm`    | Recommended |
| 37 | **[Modified](https://opengeometadata.github.io/docs/aardvarkSchema/modified)**                 | `gbl_mdModified_dt`    | <span class="text-red-300">**Required**</span> |
| 38 | **[Metadata Version](https://opengeometadata.github.io/docs/aardvarkSchema/metadata-version)** | `gbl_mdVersion_s`      | <span class="text-red-300">**Required**</span> |
| 39 | [Suppressed](https://opengeometadata.github.io/docs/aardvarkSchema/suppressed)                 | `gbl_suppressed_b`     | Optional    |
| 40 | [Georeferenced](https://opengeometadata.github.io/docs/aardvarkSchema/georeferenced)           | `gbl_georeferenced_b`  | Optional    |
