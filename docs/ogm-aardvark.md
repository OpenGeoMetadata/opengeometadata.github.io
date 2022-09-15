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


## Fields by Group

<div style="float:left; margin-right:5em; line-height:1.1" markdown="1">

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

### Temporal
- [Temporal Coverage](ogm-aardvark/temporal-coverage) (S)
- [Date Issued](ogm-aardvark/date-issued)
- [Index Year](ogm-aardvark/index-year) (S)
- [Date Range](ogm-aardvark/date-range)

</div>
<div style="float:left; margin-right:5em; line-height:1.1" markdown="1">

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

### Rights
- [Rights](ogm-aardvark/rights) (S)
- [Rights Holder](ogm-aardvark/rights-holder)
- [License](ogm-aardvark/license)
- [Access Rights](ogm-aardvark/access-rights) (R)

</div>
<div style="float:left; line-height:1.1" markdown="1">

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

----

(R) = Required  
(C) = Conditionally Required  
(S) = Suggested  

</div>

<br style="clear:left">

## Fields in Alphabetical Order

| Label                                                   | URI                    | Obligation  |
|:--------------------------------------------------------|:-----------------------|:------------|
| **[Access Rights](ogm-aardvark/access-rights)**       | `dct_accessRights_s`   | <span class="text-red-300">**Required**</span> |
| [Alternative Title](ogm-aardvark/alternative-title)   | `dct_alternative_sm`   | optional    |
| [Bounding Box](ogm-aardvark/bounding-box)             | `dcat_bbox`            | suggested |
| [Centroid](ogm-aardvark/centroid)                     | `dcat_centroid`        | optional    |
| [Creator](ogm-aardvark/creator)                       | `dct_creator_sm`       | suggested |
| [Date Issued](ogm-aardvark/date-issued)               | `dct_issued_s`         | optional    |
| [Date Range](ogm-aardvark/date-range)                 | `gbl_dateRange_drsim`  | optional    |
| [Description](ogm-aardvark/description)               | `dct_description_sm`   | suggested |
| [File Size](ogm-aardvark/file-size)                   | `gbl_fileSize_s`       | optional    |
| [Format](ogm-aardvark/format)                         | `dct_format_s`         | Conditional |
| [Geometry](ogm-aardvark/geometry)                     | `locn_geometry`        | suggested |
| [Georeferenced](ogm-aardvark/georeferenced)           | `gbl_georeferenced_b`  | optional    |
| **[ID](ogm-aardvark/id)**                             | `id`                   | <span class="text-red-300">**Required**</span> |
| [Identifier](ogm-aardvark/identifier)                 | `dct_identifier_sm`    | suggested |
| [Index Year](ogm-aardvark/index-year)                 | `gbl_indexYear_im`     | suggested |
| [Is Part Of](ogm-aardvark/is-part-of)                 | `dct_isPartOf_sm`      | optional    |
| [Is Replaced By](ogm-aardvark/is-replaced-by)         | `dct_isReplacedBy_sm`  | optional    |
| [Is Version Of](ogm-aardvark/is-version-of)           | `dct_isVersionOf_sm`   | optional    |
| [Keyword](ogm-aardvark/keyword)                       | `dcat_keyword_sm`      | optional    |
| [Language](ogm-aardvark/language)                     | `dct_language_sm`      | optional    |
| [License](ogm-aardvark/license)                       | `dct_license_sm`       | optional    |
| [Member Of](ogm-aardvark/member-of)                   | `pcdm_memberOf_sm`     | optional    |
| **[Metadata Version](ogm-aardvark/metadata-version)** | `gbl_mdVersion_s`      | <span class="text-red-300">**Required**</span> |
| **[Modified](ogm-aardvark/modified)**                 | `gbl_mdModified_dt`    | <span class="text-red-300">**Required**</span> |
| [Provider](ogm-aardvark/provider)                     | `schema_provider_s`    | suggested |
| [Publisher](ogm-aardvark/publisher)                   | `dct_publisher_sm`     | suggested |
| [References](ogm-aardvark/references)                 | `dct_references_s`     | suggested |
| [Relation](ogm-aardvark/relation)                     | `dct_relation_sm`      | optional    |
| [Replaces](ogm-aardvark/replaces)                     | `dct_replaces_sm`      | optional    |
| **[Resource Class](ogm-aardvark/resource-class)**     | `gbl_resourceClass_sm` | <span class="text-red-300">**Required**</span> |
| [Resource Type](ogm-aardvark/resource-type)           | `gbl_resourceType_sm`  | suggested |
| [Rights Holder](ogm-aardvark/rights-holder)           | `dct_rightsHolder_sm`  | optional    |
| [Rights](ogm-aardvark/rights)                         | `dct_rights_sm`        | suggested |
| [Source](ogm-aardvark/source)                         | `dct_source_sm`        | optional    |
| [Spatial Coverage](ogm-aardvark/spatial-coverage)     | `dct_spatial_sm`       | suggested |
| [Subject](ogm-aardvark/subject)                       | `dct_subject_sm`       | optional    |
| [Suppressed](ogm-aardvark/suppressed)                 | `gbl_suppressed_b`     | optional    |
| [Temporal Coverage](ogm-aardvark/temporal-coverage)   | `dct_temporal_sm`      | suggested |
| [Theme](ogm-aardvark/theme)                           | `dcat_theme_sm`        | optional    |
| **[Title](ogm-aardvark/title)**                       | `dct_title_s`          | <span class="text-red-300">**Required**</span> |
| [WxS Identifier](ogm-aardvark/wxs-identifier)         | `gbl_wxsIdentifier_s`  | conditional |
