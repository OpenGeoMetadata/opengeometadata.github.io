---
hide:
  - toc
---

# OpenGeoMetadata (OGM) Aardvark Schema

!!! info "Key" 

	==(R)  = Required==

	(C) = Conditionally Required 
 
	(S) = Suggested  

## Fields by Group

<div style="float:left; margin-right:5em; line-height:1.1" markdown="1">

### Descriptive
- ==[Title](title.md) (R)==
- [Alternative Title](alternative-title.md)
- [Description](description.md) (S)
- [Language](language.md)
- [Display Note](display-note.md)

### Credits
- [Creator](creator.md) (S)
- [Publisher](publisher.md) (S)
- [Provider](provider.md) (S)

### Categories
- ==[Resource Class](resource-class.md) (R)==
- [Resource Type](resource-type.md) (S)
- [Subject](subject.md)
- [Theme](theme.md)
- [Keyword](keyword.md)

### [Temporal :material-link:](../temporal-fields)
- [Temporal Coverage](temporal-coverage.md) (S)
- [Date Issued](date-issued.md)
- [Index Year](index-year.md) (S)
- [Date Range](date-range.md)

</div>
<div style="float:left; margin-right:5em; line-height:1.1" markdown="1">

### [Spatial :material-link:](../spatial-fields)
- [Spatial Coverage](spatial-coverage.md) (S)
- [Geometry](geometry.md) (S)
- [Bounding Box](bounding-box.md) (S)
- [Centroid](centroid.md)
- [Georeferenced](georeferenced.md)

### Relations
- [Relation](relation.md)
- [Member Of](member-of.md)
- [Is Part Of](is-part-of.md)
- [Source](source.md)
- [Is Version Of](is-version-of.md)
- [Replaces](replaces.md)
- [Is Replaced By](is-replaced-by.md)

### Rights
- [Rights](rights.md) (S)
- [Rights Holder](rights-holder.md)
- [License](license.md)
- ==[Access Rights](access-rights.md) (R)==

</div>
<div style="float:left; line-height:1.1" markdown="1">

### Object
- [Format](format.md) (C)
- [File Size](file-size.md)

### Links
- [References](references.md) (S)
- [WxS Identifier](wxs-identifier.md)

### Identifiers
- ==[ID](id.md) (R)==
- [Identifier](identifier.md) (S)

### Admin
- ==[Modified](modified.md) (R)==
- ==[Metadata Version](metadata-version.md) (R)==
- [Suppressed](suppressed.md)

----

</div>

<br style="clear:left">



## Fields in a Sortable Table

{{ read_csv('../tables/ogm-aardvark-fields.csv') }}