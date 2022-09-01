---
layout: default
title: OGM Aardvark
nav_order: 3
has_children: true
has_toc: false
---

# OGM Aardvark

OpenGeoMetadata Aardvark metadata schema (2021)
{: .fs-6 .fw-300 }

[About OGM Aardvark](about-ogm-aardvark){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[How to Upgrade from GBL 1.0](upgrading){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }


## List of Fields
<div style="columns:3; margin-bottom:1em; line-height:1.1">

(R) = Required \
(C) = Conditionally Required \
(S) = Suggested \

### Descriptive
- [Title](ogm-aardvark/title) (R)
- [Alternative Title](ogm-aardvark/alternative-title)
- [Description](ogm-aardvark/description) (S)
- [Language](ogm-aardvark/language)

### Credits
- [Creator](ogm-aardvark/creator) (S)
- [Publisher](ogm-aardvark/publisher) (S)
- [Provider](ogm-aardvark/provider) (S)

### Categories
- [Resource Class](ogm-aardvark/resource-class) (R)
- [Resource Type](ogm-aardvark/resource-type) (S)
- [Subject](ogm-aardvark/subject)
- [Theme](ogm-aardvark/theme)
- [Keyword](ogm-aardvark/keyword)

<div style="break-inside:avoid">

### Temporal
- [Temporal Coverage](ogm-aardvark/temporal-coverage) (S)
- [Date Issued](ogm-aardvark/date-issued)
- [Index Year](ogm-aardvark/index-year) (S)
- [Date Range](ogm-aardvark/date-range)

</div>

### Spatial
- [Spatial Coverage](ogm-aardvark/spatial-coverage) (S)
- [Geometry](ogm-aardvark/geometry) (S)
- [Bounding Box](ogm-aardvark/bounding-box) (S)
- [Centroid](ogm-aardvark/centroid)
- [Georeferenced](ogm-aardvark/georeferenced)


### Relations
- [Relation](ogm-aardvark/relation)
- [Member Of](ogm-aardvark/member-of)
- [Is Part Of](ogm-aardvark/is-part-of)
- [Source](ogm-aardvark/source)
- [Is Version Of](ogm-aardvark/is-version-of)
- [Replaces](ogm-aardvark/replaces)
- [Is Replaced By](ogm-aardvark/is-replaced-by)

<div style="break-inside:avoid">

### Rights
- [Rights](ogm-aardvark/rights) (S)
- [Rights Holder](ogm-aardvark/rights-holder)
- [License](ogm-aardvark/license)
- [Access Rights](ogm-aardvark/access-rights) (R)

</div>

### Object
- [Format](ogm-aardvark/format) (C)
- [File Size](ogm-aardvark/file-size)

### Links
- [References](ogm-aardvark/references) (S)
- [WxS Identifier](ogm-aardvark/wxs-identifier)

### Identifiers
- [ID](ogm-aardvark/id) (R)
- [Identifier](ogm-aardvark/identifier) (S)

### Admin
- [Modified](ogm-aardvark/modified) (R)
- [Metadata Version](ogm-aardvark/metadata-version) (R)
- [Suppressed](ogm-aardvark/suppressed)

</div>



## Table of Fields

| Group  | Label                                                   | URI                    | Obligation  |
|:---|:--------------------------------------------------------|:-----------------------|:------------|
| Descriptive | **[Title](ogm-aardvark/title)**                       | `dct_title_s`          | <span class="text-red-300">**Required**</span> |
| Descriptive | [Alternative Title](ogm-aardvark/alternative-title)   | `dct_alternative_sm`   | Optional    |
| Descriptive | [Description](ogm-aardvark/description)               | `dct_description_sm`   | Recommended |
| Descriptive | [Language](ogm-aardvark/language)                     | `dct_language_sm`      | Optional    |
| Credits | [Creator](ogm-aardvark/creator)                       | `dct_creator_sm`       | Recommended |
| Credits | [Publisher](ogm-aardvark/publisher)                   | `dct_publisher_sm`     | Recommended |
| Credits | [Provider](ogm-aardvark/provider)                     | `schema_provider_s`    | Recommended |
| Categories | **[Resource Class](ogm-aardvark/resource-class)**     | `gbl_resourceClass_sm` | <span class="text-red-300">**Required**</span> |
| Categories | [Resource Type](ogm-aardvark/resource-type)           | `gbl_resourceType_sm`  | Recommended |
| Categories | [Subject](ogm-aardvark/subject)                       | `dct_subject_sm`       | Optional    |
| Categories | [Theme](ogm-aardvark/theme)                           | `dcat_theme_sm`        | Optional    |
| Categories | [Keyword](ogm-aardvark/keyword)                       | `dcat_keyword_sm`      | Optional    |
| Temporal | [Temporal Coverage](ogm-aardvark/temporal-coverage)   | `dct_temporal_sm`      | Recommended |
| Temporal | [Date Issued](ogm-aardvark/date-issued)               | `dct_issued_s`         | Optional    |
| Temporal | [Index Year](ogm-aardvark/index-year)                 | `gbl_indexYear_im`     | Recommended |
| Temporal | [Date Range](ogm-aardvark/date-range)                 | `gbl_dateRange_drsim`  | Optional    |
| Spatial | [Spatial Coverage](ogm-aardvark/spatial-coverage)     | `dct_spatial_sm`       | Recommended |
| Spatial | [Geometry](ogm-aardvark/geometry)                     | `locn_geometry`        | Recommended |
| Spatial | [Bounding Box](ogm-aardvark/bounding-box)             | `dcat_bbox`            | Recommended |
| Spatial | [Centroid](ogm-aardvark/centroid)                     | `dcat_centroid`        | Optional    |
| Spatial | [Georeferenced](ogm-aardvark/georeferenced)           | `gbl_georeferenced_b`  | Optional    |
| Relations | [Relation](ogm-aardvark/relation)                     | `dct_relation_sm`      | Optional    |
| Relations | [Member Of](ogm-aardvark/member-of)                   | `pcdm_memberOf_sm`     | Optional    |
| Relations | [Is Part Of](ogm-aardvark/is-part-of)                 | `dct_isPartOf_sm`      | Optional    |
| Relations | [Source](ogm-aardvark/source)                         | `dct_source_sm`        | Optional    |
| Relations | [Is Version Of](ogm-aardvark/is-version-of)           | `dct_isVersionOf_sm`   | Optional    |
| Relations | [Replaces](ogm-aardvark/replaces)                     | `dct_replaces_sm`      | Optional    |
| Relations | [Is Replaced By](ogm-aardvark/is-replaced-by)         | `dct_isReplacedBy_sm`  | Optional    |
| Rights | [Rights](ogm-aardvark/rights)                         | `dct_rights_sm`        | Recommended |
| Rights | [Rights Holder](ogm-aardvark/rights-holder)           | `dct_rightsHolder_sm`  | Optional    |
| Rights | [License](ogm-aardvark/license)                       | `dct_license_sm`       | Optional    |
| Rights | **[Access Rights](ogm-aardvark/access-rights)**       | `dct_accessRights_s`   | <span class="text-red-300">**Required**</span> |
| Object | [Format](ogm-aardvark/format)                         | `dct_format_s`         | Conditional |
| Object | [File Size](ogm-aardvark/file-size)                   | `gbl_fileSize_s`       | Optional    |
| Objct | [WxS Identifier](ogm-aardvark/wxs-identifier)         | `gbl_wxsIdentifier_s`  | Conditional |
| Links | [References](ogm-aardvark/references)                 | `dct_references_s`     | Recommended |
| Identifiers | **[ID](ogm-aardvark/id)**                             | `id`                   | <span class="text-red-300">**Required**</span> |
| Identifiers | [Identifier](ogm-aardvark/identifier)                 | `dct_identifier_sm`    | Recommended |
| Admin | **[Modified](ogm-aardvark/modified)**                 | `gbl_mdModified_dt`    | <span class="text-red-300">**Required**</span> |
| Admin | **[Metadata Version](ogm-aardvark/metadata-version)** | `gbl_mdVersion_s`      | <span class="text-red-300">**Required**</span> |
| Admin | [Suppressed](ogm-aardvark/suppressed)                 | `gbl_suppressed_b`     | Optional    |
