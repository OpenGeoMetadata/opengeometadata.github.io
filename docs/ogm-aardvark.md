# OpenGeoMetadata (OGM) Aardvark Schema

<div style="float:left; margin-right:5em; line-height:1.1" markdown="1">

#### Descriptive
- ==[Title](#title) (R)==
- [Alternative Title](#alternative-title)
- [Description](#description) (S)
- [Language](#language) (v)
- [Display Note](#display-note)

#### Credits
- [Creator](#creator) (S)
- [Publisher](#publisher) (S)
- [Provider](#provider) (S)

#### Categories
- ==[Resource Class](#resource-class) (R)== (v)
- [Resource Type](#resource-type) (S) (v)
- [Subject](#subject)
- [Theme](#theme) (v)
- [Keyword](#keyword)

#### [Temporal :material-link:](../temporal-fields)
- [Temporal Coverage](#temporal-coverage) (S)
- [Date Issued](#date-issued)
- [Index Year](#index-year) (S)
- [Date Range](#date-range)

</div>
<div style="float:left; margin-right:5em; line-height:1.1" markdown="1">

#### [Spatial :material-link:](../spatial-fields)
- [Spatial Coverage](#spatial-coverage) (S)
- [Geometry](#geometry) (S)
- [Bounding Box](#bounding-box) (S)
- [Centroid](#centroid)
- [Georeferenced](#georeferenced)

#### Relations
- [Relation](#relation)
- [Member Of](#member-of)
- [Is Part Of](#is-part-of)
- [Source](#source)
- [Is Version Of](#is-version-of)
- [Replaces](#replaces)
- [Is Replaced By](#is-replaced-by)

#### Rights
- [Rights](#rights_1) (S)
- [Rights Holder](#rights-holder)
- [License](#license)
- ==[Access Rights](#access-rights) (R)==

</div>
<div style="float:left; line-height:1.1" markdown="1">

#### Object
- [Format](#format) (C) (v)
- [File Size](#file-size)

#### Links
- [References](#references) (S)
- [WxS Identifier](#wxs-identifier)

#### Identifiers
- ==[ID](#id) (R)==
- [Identifier](#identifier) (S)

#### Admin
- ==[Modified](#modified) (R)==
- ==[Metadata Version](#metadata-version) (R)== (v)
- [Suppressed](#suppressed)

----

!!! info "Key" 

	==(R)  = Required==

	(C) = Conditionally Required 
 
	(S) = Suggested  
	
	(v) = Controlled Values

</div>

<br style="clear:left">


## Access Rights
{{ read_csv('ogm-aardvark/access-rights.csv') }}

## Alternative Title
{{ read_csv('ogm-aardvark/alternative-title.csv') }}

## Bounding Box
{{ read_csv('ogm-aardvark/bounding-box.csv') }}

## Centroid
{{ read_csv('ogm-aardvark/centroid.csv') }}

## Creator
{{ read_csv('ogm-aardvark/creator.csv') }}

## Date Issued
{{ read_csv('ogm-aardvark/date-issued.csv') }}

## Date Range
{{ read_csv('ogm-aardvark/date-range.csv') }}

## Description
{{ read_csv('ogm-aardvark/description.csv') }}

## Display Note
{{ read_csv('ogm-aardvark/display-note.csv') }}

## File Size
{{ read_csv('ogm-aardvark/file-size.csv') }}

## Format
{{ read_csv('ogm-aardvark/format.csv') }}

### Format Values

* ArcGRID
* CD-ROM
* DEM
* DVD-ROM
* Feature Class
* Geodatabase
* GeoJPEG
* GeoJSON
* GeoPackage
* GeoPDF
* GeoTIFF
* JPEG
* JPEG2000
* KML
* KMZ
* LAS
* LAZ
* Mixed
* Mixed
* MrSID
* PDF
* PNG
* Pulsewaves
* Raster Dataset
* Shapefile
* SQLite Database
* Tabular Data
* TIFF

## Geometry
{{ read_csv('ogm-aardvark/geometry.csv') }}

## Georeferenced
{{ read_csv('ogm-aardvark/georeferenced.csv') }}

## ID
{{ read_csv('ogm-aardvark/id.csv') }}

## Identifier
{{ read_csv('ogm-aardvark/identifier.csv') }}

## Index Year
{{ read_csv('ogm-aardvark/index-year.csv') }}

## Is Part Of
{{ read_csv('ogm-aardvark/is-part-of.csv') }}

## Is Replaced By
{{ read_csv('ogm-aardvark/is-replaced-by.csv') }}

## Is Version Of
{{ read_csv('ogm-aardvark/is-version-of.csv') }}

## Keyword
{{ read_csv('ogm-aardvark/keyword.csv') }}

## Language
{{ read_csv('ogm-aardvark/language.csv') }}

### Language Values

[:octicons-link-external-24: See Library of Congress for full list.](https://www.loc.gov/standards/iso639-2/php/English_list.php)

{{ read_csv('ogm-aardvark/language-vocabulary.csv') }}

## License
{{ read_csv('ogm-aardvark/license.csv') }}

## Member Of
{{ read_csv('ogm-aardvark/member-of.csv') }}

## Metadata Version
{{ read_csv('ogm-aardvark/metadata-version.csv') }}

## Modified
{{ read_csv('ogm-aardvark/modified.csv') }}

## Provider
{{ read_csv('ogm-aardvark/provider.csv') }}

## Publisher
{{ read_csv('ogm-aardvark/publisher.csv') }}

## References

[References URI Keys](../reference-uris){ .md-button }

{{ read_csv('ogm-aardvark/references.csv') }}

## Relation
{{ read_csv('ogm-aardvark/relation.csv') }}

## Replaces
{{ read_csv('ogm-aardvark/replaces.csv') }}

## Resource Class
{{ read_csv('ogm-aardvark/resource-class.csv') }}

### Resource Class Values

* Collections
* Datasets
* Imagery
* Maps
* Web services
* Websites
* Other

## Resource Type

{{ read_csv('ogm-aardvark/resource-type.csv') }}

### Resource Type Values-LOC

The following table lists terms from the Library of Congress Cartographic Genres. These values will be most applicable to **scanned maps**.

{{ read_csv('ogm-aardvark/resource-type-vocabulary-loc.csv') }}

### Resource Type Values-OGM

The following table lists terms from the OpenGeoMetadata community. They are most applicable to **geospatial data**.

{{ read_csv('ogm-aardvark/resource-type-vocabulary-ogm.csv') }}

## Rights
{{ read_csv('ogm-aardvark/rights.csv') }}

## Rights Holder
{{ read_csv('ogm-aardvark/rights-holder.csv') }}

## Source
{{ read_csv('ogm-aardvark/source.csv') }}

## Spatial coverage
{{ read_csv('ogm-aardvark/spatial-coverage.csv') }}

## Subject
{{ read_csv('ogm-aardvark/subject.csv') }}

## Suppressed
{{ read_csv('ogm-aardvark/suppressed.csv') }}

## Temporal Coverage
{{ read_csv('ogm-aardvark/temporal-coverage.csv') }}

## Theme
{{ read_csv('ogm-aardvark/theme.csv') }}

### Theme Values
{{ read_csv('ogm-aardvark/theme-vocabulary.csv') }}

## Title
{{ read_csv('ogm-aardvark/title.csv') }}

## WxS Identifier
{{ read_csv('ogm-aardvark/wxs-identifier.csv') }}

