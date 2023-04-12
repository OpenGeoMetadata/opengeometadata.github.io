---
hide:
---

!!! warning

	This is a legacy format. The GeoBlacklight Community recommends using [OGM Aardvark](../ogm-aardvark) for GeoBlacklight versions 4.0 and higher.

---


| Label 					                	| URL                    | Required | Recommended |
|:----------------------------------|:-----------------------|:--------:|:-----------:|
| [Identifier](#identifier)					| `dc_identifier_s`      | X        |             |
| [Rights](#rights)					    		| `dc_rights_s`          | X        |             |
| [Title](#title)						      	| `dc_title_s`           | X        |             |
| [Provenance](#provenance)					| `dct_provenance_s`     | X        |             |
| [Schema Version](#schema-version) | `geoblacklight_version`| X        |             |
| [Slug](#slug)							      	| `layer_slug_s`         | X        |             |
| [Bounding Box](#bounding-box)	  	| `solr_geom`            | X        |             |
| [Solr Year](#solr-year)			  		| `solr_year_i`          |          | X           |
| [Creator](#creator)					    	| `dc_creator_sm`        |          | X           |
| [Description](#description)				| `dc_description_s`     |          | X           |
| [Format](#format)							    | `dc_format_s`          |          | X           |
| [Language](#language)					  	| `dc_language_sm`       |          |             |
| [Publisher](#publisher)		      	| `dc_publisher_s`       |          |             |
| [Source](#source)						    	| `dc_source_sm`         |          |             |
| [Subject](#subject)					    	| `dc_subject_sm`        |          | X           |
| [Type](#type)								      | `dc_type_s`            |          |             |
| [Is Part Of](#is-part-of)					| `dct_isPartOf_sm`      |          |             |
| [Date Issued](#date-issued)				| `dct_issued_s`         |          |             |
| [References](#references)					| `dct_references_s`     |          | X           |
| [Spatial Coverage](#spatial-coverage)		| `dct_spatial_sm` |          | X           |
| [Temporal Coverage](#temporal-coverage)	| `dct_temporal_sm`|          |             |
| [Geometry Type](#geometry-type)	  | `layer_geom_type_s`    |          | X           |
| [Layer ID](#layer-id)					   	| `layer_id_s`           |          |             |
| [Modified Date](#modified-date)	  | `layer_modified_dt`    |          | X           |
| [Suppressed](#suppressed)			    | `suppressed_b`         |          |             |



## Identifier

| Label							    | Identifier|
|:----------------------|:-----------|
| uri					  	    	| `dc_identifier_s`|
| Required				  		| yes|
| Type							    | string|
| Description					  | Unique identifier for layer as a URI. It should be globally unique across all institutions, assumed not to be end-user visible|
| Entry Guidelines			| This is usually in the form of http://institution/id |
| Controlled Vocabulary	| no|
| Element Set					  | Dublin Core Metadata Element Set|
| Example						    | "http://purl.stanford.edu/vr593vj7147"|
| Commentary            |This field is required, but it is not displayed in the interface. It may be identical to the `layer_slug_s` field, or it may be related to or derived from the `layer_id_s`. This value is ideally a persistent identifier or permalink (such as a [PURL (https://en.wikipedia.org/wiki/Persistent_uniform_resource_locator) or [Handle](https://en.wikipedia.org/wiki/Handle_System)).|


## Rights

| Label							| Rights|
|:----------------------|:-----------|
| uri							| `dc_rights_s`|
| Required						| yes|
| Type							| string|
| Description					| Signals access in the geoportal and is indicated by a padlock icon. Users need to sign in to download restricted items|
| Entry Guidelines				| Choose either Public or Restricted|
| Controlled Vocabulary			| "Public" or "Restricted"|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "Public"|
| Commentary |This field can be set to "Public", which allows users to view and download an item, or "Restricted", which requires a user to log in to an authentication service. If there are additional licenses or rights associated with a resource, administrators will have to create a custom field in the local Solr schema.|

## Title

| Label							| Title|
|:----------------------|:-----------|
| uri							| `dc_title_s`|
| Required						| yes|
| Type							| string|
| Description					| The name of the resource|
| Entry Guidelines				| Titles should include place names and dates when available.|
| Controlled Vocabulary			| no|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "Roads: Minneapolis, Minnesota, 2010"|
| Commentary |The title is the most prominent metadata field that users see when browsing or scanning search results. Since many datasets are created with ambiguous or non-unique titles, it may be worth the effort to improve or enhance them. The ideal sequence of a title is something akin to Topic of Layer: Place, Year. Putting the year at the end of a title produces better search results, since titles are left-anchored.|

## Provenance

| Label							| Provenance|
|:----------------------|:-----------|
| uri							| `dct_provenance_s`|
| Required						| yes|
| Type							| string|
| Description					| The name of the institution that holds the resource or acts as the custodian for the metadata record|
| Entry Guidelines				| The value for this field should be one of the agreed upon shortened names for each institution. This will embed the correct icon into the search results and item pages.|
| Controlled Vocabulary			| This repository contains the insitutions that have shared icons: [https://github.com/geoblacklight/geoblacklight-icons](https://github.com/geoblacklight/geoblacklight-icons)|
| Element Set					| DCMI Metadata Terms|
| Example						| "Stanford"|
| Commentary |This field indicates the institution that contributed the resource. The current community of practice is for this field to hold the name of the university or institution that has created the GeoBlacklight metadata record and/or hosts the dataset. Projects are encouraged to submit their institutional icon to the GeoBlacklight Icons repository to display with the resource.|

## Schema Version

| Label							| Schema Version|
|:----------------------|:-----------|
| uri							| `geoblacklight_version`	|
| Required						| yes|
| Type							| string|
| Description					| Indicates which version of the GeoBlacklight schema is in use|
| Entry Guidelines				| Only current value is "1.0"|
| Controlled Vocabulary			| no|
| Element Set					| GeoBlacklight|
| Example						| "1.0"|
| Commentary | "1.0" is the current version of the GeoBlacklight schema.|

## Slug

| Label							| Slug|
|:----------------------|:-----------|
| uri							| `layer_slug_s`|
| Required						| yes|
| Type							| string|
| Description					| This is a string appended to the base URL of a GeoBlacklight installation to create a unique landing page for each resource. It is visible to the user and serves the purpose of forming a persistent URL for each catalog item.|
| Entry Guidelines				| This string must be a globally unique value. The value should be alpha-numeric characters separated by dashes.|
| Controlled Vocabulary			| no|
| Element Set					| GeoBlacklight|
| Example						| "stanford-andhra-pradesh-village-boundaries"|
| Commentary |The slug makes up the URL for the resource in GeoBlacklight. If having a readable slug is desired, it is common to use the form, institution-keyword1-keyword2 (words or characters are separated by hyphens).|

## Bounding Box

| Label 						| Bounding Box|
|:----------------------|:-----------|
| uri							| `solr_geom`|
| Required						| yes|
| Type							| string|
| Description					| The rectangular extents of the resource. Note that this field is indexed as a Solr spatial (RPT) field|
| Entry Guidelines				| Bounding box of the layer as a ENVELOPE WKT (from the CQL standard) using coordinates in (West, East, North, South) order. The pattern is: ENVELOPE(.*,.*,.*,.*)|
| Controlled Vocabulary			| no|
| Element Set					| GeoBlacklight|
| Example						| "ENVELOPE(76.76, 84.76, 19.91, 12.62)"|
| Commentary |The rectangular bounding box is to aid searching with the map interface. Although accuracy is encouraged, it may not always be necessary to to have precise bounding coordinates. The field functions to facilitate discovery more than to indicate exact extents.|

## Solr Year

| Label 						| Solr Year|
|:----------------------|:-----------|
| uri							| `solr_year_i`|
| Required						| no|
| Type							| integer|
| Description					| A four digit integer representing a year of temporal coverage or date issued for the resource. This field is used to populate the Year facet and the optional [Blacklight Range Limit gem](https://github.com/projectblacklight/blacklight_range_limit)|
| Entry Guidelines				| This field must be an integer.|
| Controlled Vocabulary			| no|
| Element Set					| GeoBlacklight|
| Example						| "1982"|
| Commentary |This field is a four digit integer that must be inferred by the temporal coverage or date issued of the resource. If a single record spans multiple years, choose the earliest year for the `solr_year_i` field.|

## Creator

| Label							| Creator|
|:----------------------|:-----------|
| uri 							| `dc_creator_sm`|
| Required						| no|
| Type							| array|
| Description					| The person(s) or organization that created the resource|
| Entry Guidelines				| This may be an individual or an organization. If available, it should match with the Library of Congress Name Authority File.|
| Controlled Vocabulary			| The suggested controlled vocabulary is the [Library of Congress Name Authority File](http://id.loc.gov/authorities/names.html).|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "George Washington", "Thomas Jefferson"|
| Commentary |The `dc_creator_sm` field is best reserved for instances in which an individual person has collected, produced, or generated analyses of data (as opposed to an agency releasing a data product or resource). See also the comments on `dc_publisher_sm`.|

## Description

| Label| Description|
|:----------------------|:-----------|
| uri							| `dc_description_s`|
| Required						| no|
| Type							| string|
| Description					| At minimum, this is a reiteration of the title in sentence format. Other relevant information, such as data creation methods, data sources, and special licenses, may also be included.|
| Entry Guidelines				| This is a plain text field.|
| Controlled Vocabulary			| no|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "This polygon shapefile represents boundaries of election districts in New York City. It was harvested from the NYC Open Data Portal."|
| Commentary |The `dc_description_s` field is the second most prominent value that users see when search or browsing for items. Although not required, it is strongly recommended. If the description is minimal or lacking, it can be improved by concatenating available metadata fields, such as title, date, format, and place. This is a plain text field, so html code is not supported here unless the application is customized. It is recommended to assume that discovery happens in multiple contexts (i.e., GeoBlacklight metadata may be integrated into other discovery environments), so descriptions should use complete sentences that signpost what the data object is, even though that is evident within GeoBlacklight itself.|

## Format

| Label							| Format|
|:----------------------|:-----------|
| uri							| `dc_format_s`|
| Required						| yes, if download link is included AND if download URL is configured as a single key:value pair|
| Type							| string|
| Description					| This indicates the file format of the data. If a download link is included, this value displays on the item page in the button under the download widget|
| Entry Guidelines				| Choose from set values (see Format list)|
| Controlled Vocabulary			| [Format Controlled Vocabulary](format-values)|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "Shapefile"|
| Commentary | The most important thing to remember about the `dc_format_s` field is that it is required for Download functionality if using a single value string for downloads. (pre-GeoBlacklight version 3.0). [See the Multiple Downloads guide for more details](more-about-references#how-to-configure-multiple-download-links)|

## Language

| Label							| Language|
|:----------------------|:-----------|
| uri							| `dc_language_sm`|
| Required						| no|
| Type							| array|
| Description					| Indicates the language of the data or map|
| Entry Guidelines				| Spell out language (in English) instead of using the ISO 639-1 code (e.g.,“French” instead of “fra”).|
| Controlled Vocabulary			| no|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "English"|
| Commentary | This field is intended to indicate the language of the dataset, map, and/or supporting documentation. The most common practice in this community is to spell the name language out in English (e.g., "French").|

## Publisher

| Label							| Publisher|
|:----------------------|:-----------|
| uri							| `dc_publisher_s`|
| Required						| no|
| Type							| array|
| Description					| The organization that made the original resource available|
| Entry Guidelines				| This should always be an organization.|
| Controlled Vocabulary			| The suggested controlled vocabulary is the [Library of Congress Name Authority File](http://id.loc.gov/authorities/names.html).|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "ML InfoMap (Firm)"|
| Commentary |The distinction between `dc_publisher_s` and `dc_creator_sm` for data is often vague. Publishers should be the administrative body or organization that made the original resource available, regardless of who compiled or produced the data.|

## Source

| Label							| Source|
|:----------------------|:-----------|
| uri							| `dc_source_sm`|
| Required						| no|
| Type							| array|
| Description					| This is used to indicate parent/child relationships between data layers and activates the Data Relations widget in GeoBlacklight|
| Entry Guidelines				| This is only added to the child records. Enter the `layer_slug_s` of the parent record(s) into this field.|
| Controlled Vocabulary			| no|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "stanford-vr593vj7147"|
| Commentary |The `dc_source_sm` field exists to indicate parent-child relationships between records. Common uses include: individual sheets within a map series that can point to a Shapefile that serves as an index map, individual Shapefile layers that have been derived from a Geodatabase that can point to the record for the GeoDatabase, or collection-level and related individual layer records. [See Using the Data Relations Widget](https://geoblacklight.org/guides.html#using-the-data-relations-widget) for more information.|

## Subject

| Label							| Subject|
|:----------------------|:-----------|
| uri							| `dc_subject_sm`|
| Required						| no|
| Type							| array|
| Description					| These are theme or topic keywords|
| Entry Guidelines				| These should be consistent and chosen from a controlled vocabulary. Use sentence style capitalization, where only the first word of a phrase is capitalized.
| Controlled Vocabulary			| Recommended thesauri are [ISO Topic Categories](https://www2.usgs.gov/science/about/thesaurus-full.php?thcode=15) and Library of Congress Subject Headings.|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "Census", "Human settlements"|
| Commentary |This field is indexed as a facet by default for GeoBlacklight applications, and it can become unwieldy when aggregating metadata records from multiple sources. Controlled vocabularies for GIS data have typically been expressed as ISO Topic Categories and localized thesauri, while scanned maps are typically described with Library of Congress Subject Headings. Even within these vocabularies, localized spellings and abbreviations will result in considerable variations between institutions. Institutions are encouraged to observe what terms are commonly in use and, at the very least, strive for internal consistency with controlled vocabularies and spellings. This facilitates easier metadata sharing across projects, such as the repositories in [OpenGeoMetadata](https://github.com/OpenGeoMetadata). Some institutions choose to create custom keyword fields to hold local, unnormalized values. It is recommended not to use Library of Congress Subject Headings to indicate the geography or spatial coverage of a dataset; instead, use the `dct_spatial_sm` field for this.|

## Type

| Label							| Type|
|:----------------------|:-----------|
| uri							| `dc_type_s`|
| Required						| no|
| Type							| string|
| Description					| This is a general element to indicate the larger genre of the resource|
| Entry Guidelines				| Choose from Dublin Core Type values|
| Controlled Vocabulary			| [Type Controlled Vocabulary](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#section-7)|
| Element Set					| Dublin Core Metadata Element Set|
| Example						| "Dataset"|
| Commentary | The `dc_type_s` field is optional, but it can be useful for categorizing between datasets, scanned maps, and collections. The GeoBlacklight 1.0 schema observes the Dublin Core controlled vocabulary for [Type](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#section-7)|

## Is Part Of

| Label							| Is Part Of|
|:----------------------|:-----------|
| uri							| `dct_isPartOf_sm`|
| Required						| no|
| Type							| array|
| Description					| Holding entity for the layer, such as the title of a collection|
| Entry Guidelines				| Plain text that is indexed in the Collections facet|
| Controlled Vocabulary			| no|
| Element Set					| [DCMI Metadata Terms](http://dublincore.org/documents/dcmi-terms/)|
| Example						| "Village Maps of India"|
| Commentary | The `dct_isPartOf_sm` field is most often used as a way to group collections arbitrarily. Such groupings often have meaning within local institutions and can be shorthand for keeping like items together. For example, the value could mark all of the items in a single data submission, all of the items that pertain to a class that is working with GIS data, or all of the items harvested from a specific Open Data portal.|

## Date Issued

| Label							| Date Issued|
|:----------------------|:-----------|
| uri							| `dct_issued_s`|
| Required						| no|
| Type							| string|
| Description					| This is the publication date for the resource|
| Entry Guidelines				| Use any date format, such as the XML Schema dateTime format (YYYY-MM-DDThh:mm:ssZ)|
| Controlled Vocabulary			| no|
| Element Set					| [DCMI Metadata Terms](http://dublincore.org/documents/dcmi-terms/)|
| Example						| "2015-01-01"|
| Commentary | Although the `dct_issued_s` field is optional, it is often useful when a clear Temporal Coverage value is not present. For example, one may want to preserve a dataset with an uncertain lineage, but there is an indicator on a data portal on the date of last update.|

## References

| Label							| References|
|:----------------------|:-----------|
| uri							| `dct_references_s`|
| Required						| no|
| Type							| string|
| Description					| This element is a hash of key/value pairs for different types of external links. It integrates external services and references using the CatInterOp approach|
| Entry Guidelines				| See [External References](https://opengeometadata.org/docs/more-about-references|
| Controlled Vocabulary			| [References URIs](more-about-references#reference-uris)|
| Element Set					| DCMI Metadata Terms|
| Example						|`"dct_references_s": "{\"http://schema.org/url\":\"http://purl.stanford.edu/bm662dm5913\",\"http://schema.org/downloadUrl\":\"http://stacks.stanford.edu/file/druid:bm662dm5913/data.zip\"}"`|
| Commentary | All of the external links for the resource are added to the `dct_references_s` field as a serialized JSON array of key/value pairs. The download key/value pair is unique, because the value can be an array. [See this Multiple Downloads guide for more information.](more-about-references#how-to-configure-multiple-download-links)|

## Spatial Coverage

| Label							| Spatial Coverage|
|:----------------------|:-----------|
| uri							| `dct_spatial_sm`|
| Required						| no|
| Type							| array|
| Description					| This field is for place name keywords|
| Entry Guidelines				| Place name text strings should be specified out to the nation level. It is typical for the place name to represent the largest extent the data layer represents.|
| Controlled Vocabulary			| Recommended thesaurus is [GeoNames](https://www.geonames.org/)|
| Element Set					| DCMI Metadata Terms|
| Example						| "Philadelphia, Pennsylvania, United States"|
| Commentary | It is recommended to have at least one place name for each layer that corresponds to the logical extent of the area of that layer. Adding additional place names that fall within the layer should be done only if they are topically relevant to the content of the data. If a long list of place names is desired in the metadata for search purposes, a customized hidden field is recommended.|

## Temporal Coverage

| Label							| Temporal Coverage|
|:----------------------|:-----------|
| uri							| `dct_temporal_sm`|
| Required						| no|
| Type							| array|
| Description					| This represents the "Ground Condition" of the resource, meaning the time period data was collected or is intended to represent. Displays on the item page in the Year value|
| Entry Guidelines				| This is a text string and can indicate uncertainty|
| Controlled Vocabulary			| no|
| Element Set					| DCMI Metadata Terms|
| Example						| "2007-2009"|
| Commentary |The `dct_temporal_sm` field is multi-valued, so multiple strings can be used to indicate the time period the resource depicts, when the data was collected, and/or when the resources was created. Examples include: “1910?”, “1800-1805”, “before 2000”. If a single dataset spans multiple years, one can add each intervening year as a discrete value (e.g., 2007,2008,2009,2010). However, a common convention is to include only the first and last year (e.g., 2007,2010 for a dataset encompassing the span of time between 2007 and 2010).|

## Geometry Type

| Label							| Geometry Type|
|:----------------------|:-----------|
| uri							| `layer_geom_type_s`|
| Required						| no|
| Type							| string|
| Description					| This element shows up as Data type in GeoBlacklight, and each value has an associated icon|
| Entry Guidelines				| Choose from set values (see Controlled Vocabulary Lists)|
| Controlled Vocabulary			| [Geometry Type Controlled Vocabulary](../1.0-geometry-type/)|
| Element Set					| GeoBlacklight|
| Example						| "Polygon"|
| Commentary |This field helps to differentiate between vector (Point, Line, Polygon), raster (Raster, Image), nonspatial formats (table), or a combination (Mixed). If processing metadata from a geospatial web server, this value may be programmatically determined. However, in many cases, it must be manually determined. The field is tied to icons for the resource, and provides the user with visual clues to the item. However, if the element is troublesome or unnecessary for a particular institution, it can be omitted.|

## Layer ID

| Label							| Layer ID|
|:----------------------|:-----------|
| uri							| `layer_id_s`|
| Required						| no|
| Type							| string|
| Description					| Indicates the layer id for any WMS or WFS web services listed in the `dct_references_s` field|
| Entry Guidelines				| Only the layer name is added here. The base service endpoint URLs (e.g. "https://maps-public.geo.nyu.edu/geoserver/sdr/wms") are added to the `dct_references_s` field.|
| Controlled Vocabulary			| no|
| Element Set					| GeoBlacklight|
| Example						| "druid:vr593vj7147"|
| Commentary |The Layer ID is used to point to specific layers within a geospatial web service. This field is not used for ArcGIS Rest Services.|

## Modified Date

| Label							| Modified Date|
|:----------------------|:-----------|
| uri							| `layer_modified_dt`|
| Required						| no|
| Type							| date-time|
| Description					| Last modification date for the metadata record|
| Entry Guidelines				| Use the XML Schema dateTime format (YYYY-MM-DDThh:mm:ssZ)|
| Controlled Vocabulary			| no|
| Element Set					| GeoBlacklight|
| Example						| "2015-01-01T12:00:00Z"|
| Commentary | This value should indicate when the metadata (not the resource itself) was last modified.|

## Suppressed

| Label							| Suppressed|
|:----------------------|:-----------|
| uri							| `suppressed_b`|
| Required						| no|
| Type							| boolean|
| Description					| If set to True, the record will not appear in search results. If is still accessible from the Data Relations widget and via direct URL.|
| Entry Guidelines				| Values can be True or False|
| Controlled Vocabulary			| yes|
| Element Set					| GeoBlacklight|
| Example						| "True"|
| Commentary | This field is useful for multipart items with identical metadata, such as pages in an atlas or series.|
