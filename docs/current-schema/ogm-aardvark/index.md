---
layout: default
title: OGM Aardvark
parent: Current Schema
nav_order: 2
has_children: true
has_toc: false
permalink: /docs/current-schema/ogm-aardvark
---

# OGM Aardvark

OpenGeoMetadata Aardvark metadata schema (2021)
{: .fs-6 .fw-300 }


## List of Fields

| #  | Label                                                   | URI                    | Obligation  |
|:---|:--------------------------------------------------------|:-----------------------|:------------|
| 01 | **[Title](/title)**                       | `dct_title_s`          | <span class="text-red-300">**Required**</span> |
| 02 | [Alternative Title](/alternative-title)   | `dct_alternative_sm`   | Optional    |
| 03 | [Description](/description)               | `dct_description_sm`   | Recommended |
| 04 | [Language](/language)                     | `dct_language_sm`      | Optional    |
| 05 | [Creator](/creator)                       | `dct_creator_sm`       | Recommended |
| 06 | [Publisher](/publisher)                   | `dct_publisher_sm`     | Recommended |
| 07 | [Provider](/provider)                     | `schema_provider_s`    | Recommended |
| 08 | **[Resource Class](/resource-class)**     | `gbl_resourceClass_sm` | <span class="text-red-300">**Required**</span> |
| 09 | [Resource Type](/resource-type)           | `gbl_resourceType_sm`  | Recommended |
| 10 | [Subject](/subject)                       | `dct_subject_sm`       | Optional    |
| 11 | [Theme](/theme)                           | `dcat_theme_sm`        | Optional    |
| 12 | [Keyword](/keyword)                       | `dcat_keyword_sm`      | Optional    |
| 13 | [Temporal Coverage](/temporal-coverage)   | `dct_temporal_sm`      | Recommended |
| 14 | [Date Issued](/date-issued)               | `dct_issued_s`         | Optional    |
| 15 | [Index Year](/index-year)                 | `gbl_indexYear_im`     | Recommended |
| 16 | [Date Range](/date-range)                 | `gbl_dateRange_drsim`  | Optional    |
| 17 | [Spatial Coverage](/spatial-coverage)     | `dct_spatial_sm`       | Recommended |
| 18 | [Geometry](/geometry)                     | `locn_geometry`        | Recommended |
| 19 | [Bounding Box](/bounding-box)             | `dcat_bbox`            | Recommended |
| 20 | [Centroid](/centroid)                     | `dcat_centroid`        | Optional    |
| 21 | [Relation](/relation)                     | `dct_relation_sm`      | Optional    |
| 22 | [Member Of](/member-of)                   | `pcdm_memberOf_sm`     | Optional    |
| 23 | [Is Part Of](/is-part-of)                 | `dct_isPartOf_sm`      | Optional    |
| 24 | [Source](/source)                         | `dct_source_sm`        | Optional    |
| 25 | [Is Version Of](/is-version-of)           | `dct_isVersionOf_sm`   | Optional    |
| 26 | [Replaces](/replaces)                     | `dct_replaces_sm`      | Optional    |
| 27 | [Is Replaced By](/is-replaced-by)         | `dct_isReplacedBy_sm`  | Optional    |
| 28 | [Rights](/rights)                         | `dct_rights_sm`        | Recommended |
| 29 | [Rights Holder](/rights-holder)           | `dct_rightsHolder_sm`  | Optional    |
| 30 | [License](/license)                       | `dct_license_sm`       | Optional    |
| 31 | **[Access Rights](/access-rights)**       | `dct_accessRights_s`   | <span class="text-red-300">**Required**</span> |
| 32 | [Format](/format)                         | `dct_format_s`         | Conditional |
| 33 | [File Size](/file-size)                   | `gbl_fileSize_s`       | Optional    |
| 34 | [WxS Identifier](/wxs-identifier)         | `gbl_wxsIdentifier_s`  | Conditional |
| 35 | [References](/references)                 | `dct_references_s`     | Recommended |
| 36 | **[ID](/id)**                             | `id`                   | <span class="text-red-300">**Required**</span> |
| 37 | [Identifier](/identifier)                 | `dct_identifier_sm`    | Recommended |
| 38 | **[Modified](/modified)**                 | `gbl_mdModified_dt`    | <span class="text-red-300">**Required**</span> |
| 39 | **[Metadata Version](/metadata-version)** | `gbl_mdVersion_s`      | <span class="text-red-300">**Required**</span> |
| 40 | [Suppressed](/suppressed)                 | `gbl_suppressed_b`     | Optional    |
| 41 | [Georeferenced](/georeferenced)           | `gbl_georeferenced_b`  | Optional    |
