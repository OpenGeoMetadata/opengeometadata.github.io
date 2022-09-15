---
layout: default
title: Upgrade Guide
nav_order: 4
has_toc: false
parent: Helpful Resources

---

# Upgrade Guide for converting Metadata from GBL 1.0 to OGM Aardvark
{: .no_toc }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Full crosswalk table

Most of the elements from GBL 1.0 can be crosswalked directly into OGM Aardvark. The values for these elements are the same - only the URI name has changed or the field has been converted to an array.  

The following chart shows the full Aardvark schema and which GBL 1.0 fields can be directly mapped.

|  # |       Label       |        GBL 1.0           |      OGM Aardvark      |                Note               |
|:---|:------------------|:-------------------------|:-----------------------|:----------------------------------|
| 01 |       Title       | `dc_title_s`             | `dct_title_s`          |           new namespace           |
| 02 | Alternative Title |                          | `dct_alternative_sm`   |             new field             |
| 03 |    Description    | `dc_description_s`       | `dct_description_sm`   |new namespace; single to multi-valued|
| 04 |      Language     | `dc_language_s` or `_sm` | `dct_language_sm`      |new namespace; single to multi-valued|
| 05 |      Creator      | `dc_creator_sm`          | `dct_creator_sm`       |           new namespace           |
| 06 |     Publisher     | `dc_publisher_s`         | `dct_publisher_sm`     |new namespace; single to multi-valued|
| 07 |      Provider     | `dct_provenance_s`       | `schema_provider_s`    |            new URI name           |
| 08 |   Resource Class  |                          | `gbl_resourceClass_sm` |             new field             |
| 09 |   Resource Type   |                          | `gbl_resourceType_sm`  |             new field             |
| 10 |      Subject      | `dc_subject_sm`          | `dct_subject_sm`       |           new namespace           |
| 11 |       Theme       |                          | `dcat_theme_sm`        |             new field             |
| 12 |      Keyword      |                          | `dcat_keyword_sm`      |             new field             |
| 13 | Temporal Coverage | `dct_temporal_sm`        | `dct_temporal_sm`      |             no change             |
| 14 |    Date Issued    | `dct_issued_s`           | `dct_issued_s`         |             no change             |
| 15 |     Index Year    | `solr_year_i`            | `gbl_indexYear_im`     |new URI name; single to multi-valued|
| 16 |     Date Range    |                          | `gbl_dateRange_drsim`  |             new field             |
| 17 |  Spatial Coverage | `dct_spatial_sm`         | `dct_spatial_sm`       |             no change             |
| 18 |      Geometry     | `solr_geom`              | `locn_geometry`        |             new field             |
| 19 |    Bounding Box   | `solr_geom`              | `dcat_bbox`            |             new field             |
| 20 |      Centroid     |                          | `dcat_centroid`        |             new field             |
| 21 |      Relation     |                          | `dct_relation_sm`      |             new field             |
| 22 |     Member Of     |                          | `pcdm_memberOf_sm`     |             new field             |
| 23 |     Is Part Of    |                          | `dct_isPartOf_sm`      |new value type (see [Elements without a crosswalk](#elements-without-a-crosswalk))|
| 24 |       Source      | `dc_source_sm`           | `dct_source_sm`        |           new namespace           |
| 25 |      Version      |                          | `dct_isVersionOf_sm`   |             new field             |
| 26 |      Replaces     |                          | `dct_replaces_sm`      |             new field             |
| 27 |   Is Replaced By  |                          | `dct_isReplacedBy_sm`  |             new field             |
| 28 |       Rights      |                          | `dct_rights_sm`        |             new field             |
| 29 |   Rights Holder   |                          | `dct_rightsHolder_sm`  |             new field             |
| 30 |      License      |                          | `dct_license_sm`       |             new field             |
| 31 |   Access Rights   | `dc_rights_s`            | `dct_accessRights_s`   |            new URI name           |
| 32 |       Format      | `dc_format_s`            | `dct_format_s`         |           new namespace           |
| 33 |     File Size     |                          | `gbl_fileSize_s`       |             new field             |
| 34 |   WxS Identifier  | `layer_id_s`             | `gbl_wxsIdentifier_s`  |            new URI name           |
| 35 |     References    | `dct_references_s`       | `dct_references_s`     |             no change             |
| 36 |         ID        | `layer_slug_s`           | `id`                   |            new URI name           |
| 37 |     Identifier    | `dc_identifier_s`        | `dct_identifier_sm`    |new namespace; single to multi-valued |
| 38 |      Modified     | `layer_modified_dt`      | `gbl_mdModified_dt`    |            new URI name           |
| 39 |  Metadata Version | `geoblacklight_version`  | `gbl_mdVersion_s`      |            new URI name           |
| 40 |     Suppressed    | `suppressed_b`           | `gbl_suppressed_b`     |           new namespace           |
| 41 |   Georeferenced   |                          | `gbl_georeferenced_b`  |             new field             |

## Elements without a crosswalk


There are three elements in GBL 1.0 that do not directly translate into OGM Aardvark. While they have been replaced with similar fields in OGM Aardvark, the **values themselves** would need to be altered during crosswalking.

**Type (dc_type_s)**
* GBL 1.0 Description: This single-valued GBL 1.0 field observes the Dublin Core controlled vocabulary for Type, including Dataset, Image, Collection, Interactive Resource, or Physical Object.
* Similar Aardvark element: This has been replaced in Aardvark with the multi-valued [Resource Class](ogm-aardvark/resource-class), which uses a custom controlled vocabulary of Collections, Datasets, Imagery, Maps, Web services, and/or Other.

**Geometry Type (layer_geom_type_s)**
* GBL 1.0 Description: This single-valued GBL 1.0 field differentiates between vector (Point, Line, Polygon), raster (Raster, Image), non-spatial formats (Table), or a combination (Mixed).
* Similar Aardvark element: This has been replaced in Aardvark with the multi-valued [Resource Type](ogm-aardvark/resource-type), which uses a controlled vocabulary drawn from Library of Congress cartographic genres and GIS geometries.

**Is Part Of (dct_isPartOf_sm)**
* GBL 1.0 Description: This multi-valued GBL 1.0 plain text field is for writing out the name of a collection. Example: `dct_isPartOf_sm:"Village Maps of India"`
* Similar Aardvark element: The URI is the same in Aardvark, but it is now a non-literal field. The value must be one or more IDs that reference another record within the system. Example: `dct_isPartOf_sm:"princeton-z603r079s"`

------
## Tools and techniques for upgrading

The following tools include three options for upgrading GeoBlacklight 1.0 metadata into OGM Aardvark.  The figures include references to Solr, the search index that powers a GeoBlacklight instance.

### Option 1: Re-run the metadata pipeline with a new crosswalk

<figure>
  <img
  src="/../assets/images/transform-option1.png"
  alt="metadata-pipline">
  <figcaption align = "center">Fig.1 - Metadata pipeline showing a conversion from standards metadata</figcaption>
</figure>

**Scenario** 

* you have geospatial resources with structured metadata files in an official standard, such as ISO 19139, FGDC, MODS, or MARC
* your organization already has a metadata pipeline process that converts these structures files to GeoBlacklight 1.0

**How does it work?** 

This option involves updating your local transformation workflow that extracts values from standards-based metadata files.

* For institutions that utilize an XSLT for the transformation, [GeoCombine repository has XSL files](https://github.com/OpenGeoMetadata/GeoCombine/tree/main/lib/xslt).

* For institutions that use custom tools or Python scripts, refer to this working crosswalk document to update the code (to be added). It shows crosswalks between OGM Aardvark, GBL 1.0, FGDC, and ISO.

**Considerations**

* This process may require extra institutional support, particularly if the transformation process is part of a larger framework or connected to a repository.
* Community developed XSLs are still a work in progress

-----

### Option 2: Programmatically convert the JSON files

<figure>
  <img
  src="/../assets/images/transform-option2.png"
  alt="convert-jsons">
  <figcaption align = "center">Fig.2 - Programmatic transformation process using Geoblacklight 1.0 Metadata JSONs</figcaption>
</figure>


**Scenario** 
* your resources only have GeoBlacklight 1.0 metadata (no structured metadata files in an official standard)
* you want to test your environment with the new Aardvark schema 

**How does it work?**

1. Gather GBL 1.0 metadata JSON files on your desktop
2. Use a script or tool to convert the files batch convert GBL 1.0 json files to OGM Aardvark
3. Re-index the resulting Aardvark JSON files into your application (GeoBlacklight)

Currently, the OpenGeoMetadata community has two tools that can do batch conversions:


* [gbl2aardvark](https://kgjenkins.github.io/gbl2aardvark/): A web hosted interface (recommended tool).

	* Users can upload GeoBlacklight 1.0 metadata files to this tool and it will return a downloadable JSON in the OGM Aardvark schema.  
	* In addition to direct crosswalks, this tool will also populate the `Resource Class` and `Resource Type` based upon the `Type` and `Geometry Type` fields from version 1.0. It will also generate new collection level records based upon the value in the Is Part Of fields. 
	* Any fields that do not properly convert will be flagged with the phrase "EDIT ME --" 
	* When reindexing to Solr with a single JSON file representing multiple records, use Solr's "Document Type"="File Upload" option.
	* [See the GitHub documentation for more information](https://github.com/kgjenkins/gbl2aardvark)

* a standalone Python script: [https://github.com/OpenGeoMetadata/gbl-1_to_aardvark](https://github.com/OpenGeoMetadata/gbl-1_to_aardvark).
   * This command line script with perform a straight conversion of field names. 
   * It features an editable crosswalk file to customize the transformation.
   * The non-crosswalkable elements listed above (Type, Geometry Type, and Is Part Of) do not have direct crosswalks and will be copied as is into the new Aardvark JSONs.

**Considerations**

* this option represents the fastest method, but is not a long term solution and may result in incomplete metadata

* this option will not include some fields that are new in OGM Aardvark, such as Rights or License. To take advantange of those fields, use Option 1 or 3.

-----
### Option 3: Conversion with manual remediation

<figure>
  <img
  src="/../assets/images/transform-option3.png"
  alt="manual-remediation">
  <figcaption align = "center">Fig.3 - Transformation process that includes manual remediation</figcaption>
</figure>


**Scenario**

* you have GBL 1.0 metadata files
* you want to minimize data loss and corrupted output values
* you have staff time available for manual work

**How does it work?**

This technique combines automatic conversions and manual edits:

1. Convert your GBL 1.0 metadata files to a CSV. (This Python script will convert a batch of JSONs to a CSV file: https://github.com/geobtaa/workflows/blob/main/editing/json2csv.py)


2. Manually augment and adjust column names and values using spreadsheet functions.


3. Convert your spreadsheet to OGM Aardvark JSONs. (This Python script will convert CSVs to Aardvark JSONS: https://github.com/jhu-library-applications/geoportal/tree/main/aardvark)



**Considerations**

* This option is more likely to produce normalized, consistent values than Options 1 or 2.
* This option may be require extra dedicated staff time
* It could be adjusted to work with the extracted metadata from standards files 