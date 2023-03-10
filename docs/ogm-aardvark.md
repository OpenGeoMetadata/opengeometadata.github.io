---
hide:

  - toc

---

# OpenGeoMetadata (OGM) Aardvark Schema
<!--

[About OGM Aardvark](about-ogm-aardvark.md){.md-button} [How to Upgrade from GBL 1.0](upgrading.md){.md-button}
-->

## Fields by Group

<div style="float:left; margin-right:5em; line-height:1.1" markdown="1">

### Descriptive
- ==[Title](ogm-aardvark/title.md) (R)==
- [Alternative Title](ogm-aardvark/alternative-title.md)
- [Description](ogm-aardvark/description.md) (S)
- [Language](ogm-aardvark/language.md)
- [Display Note](ogm-aardvark/display-note.md)

### Credits
- [Creator](ogm-aardvark/creator.md) (S)
- [Publisher](ogm-aardvark/publisher.md) (S)
- [Provider](ogm-aardvark/provider.md) (S)

### Categories
- ==[Resource Class](ogm-aardvark/resource-class.md) (R)==
- [Resource Type](ogm-aardvark/resource-type.md) (S)
- [Subject](ogm-aardvark/subject.md)
- [Theme](ogm-aardvark/theme.md)
- [Keyword](ogm-aardvark/keyword.md)

### [Temporal :material-link:](../temporal-fields)
- [Temporal Coverage](ogm-aardvark/temporal-coverage.md) (S)
- [Date Issued](ogm-aardvark/date-issued.md)
- [Index Year](ogm-aardvark/index-year.md) (S)
- [Date Range](ogm-aardvark/date-range.md)

</div>
<div style="float:left; margin-right:5em; line-height:1.1" markdown="1">

### [Spatial :material-link:](../spatial-fields)
- [Spatial Coverage](ogm-aardvark/spatial-coverage.md) (S)
- [Geometry](ogm-aardvark/geometry.md) (S)
- [Bounding Box](ogm-aardvark/bounding-box.md) (S)
- [Centroid](ogm-aardvark/centroid.md)
- [Georeferenced](ogm-aardvark/georeferenced.md)

### Relations
- [Relation](ogm-aardvark/relation.md)
- [Member Of](ogm-aardvark/member-of.md)
- [Is Part Of](ogm-aardvark/is-part-of.md)
- [Source](ogm-aardvark/source.md)
- [Is Version Of](ogm-aardvark/is-version-of.md)
- [Replaces](ogm-aardvark/replaces.md)
- [Is Replaced By](ogm-aardvark/is-replaced-by.md)

### Rights
- [Rights](ogm-aardvark/rights.md) (S)
- [Rights Holder](ogm-aardvark/rights-holder.md)
- [License](ogm-aardvark/license.md)
- ==[Access Rights](ogm-aardvark/access-rights.md) (R)==

</div>
<div style="float:left; line-height:1.1" markdown="1">

### Object
- [Format](ogm-aardvark/format.md) (C)
- [File Size](ogm-aardvark/file-size.md)

### Links
- [References](ogm-aardvark/references.md) (S)
- [WxS Identifier](ogm-aardvark/wxs-identifier.md)

### Identifiers
- ==[ID](ogm-aardvark/id.md) (R)==
- [Identifier](ogm-aardvark/identifier.md) (S)

### Admin
- ==[Modified](ogm-aardvark/modified.md) (R)==
- ==[Metadata Version](ogm-aardvark/metadata-version.md) (R)==
- [Suppressed](ogm-aardvark/suppressed.md)

----

</div>

<br style="clear:left">


!!! info "Key" 

	==(R) = Required== 

	(C) = Conditionally Required 
 
	(S) = Suggested  


## Fields in a Sortable Table


{{ read_csv('tables/ogm-aardvark-fields.csv') }}
