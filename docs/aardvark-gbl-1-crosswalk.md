The following chart shows the full Aardvark schema and which GBL 1.0 fields can be directly mapped.

## Crosswalk table

{{ read_csv('tables/ogm-gbl1.csv') }}


## Elements without a crosswalk

Most of the elements from GBL 1.0 can be crosswalked directly into OGM Aardvark. The values for these elements are the same - only the field name has changed or the field has been converted to an array.  

However, there are three elements in GBL 1.0 that do not directly translate into OGM Aardvark. While they have been replaced with similar fields in OGM Aardvark, the **values themselves** would need to be altered during crosswalking.

**Type (`dc_type_s`)**

* GBL 1.0 Description: This single-valued GBL 1.0 field observes the Dublin Core controlled vocabulary for Type, including Dataset, Image, Collection, Interactive Resource, or Physical Object.
* Similar Aardvark element: This has been replaced in Aardvark with the multi-valued [Resource Class](../ogm-aardvark/#resource-class), which uses a custom controlled vocabulary of Collections, Datasets, Imagery, Maps, Web services, and/or Other.

**Geometry Type (`layer_geom_type_s`)**

* GBL 1.0 Description: This single-valued GBL 1.0 field differentiates between vector (Point, Line, Polygon), raster (Raster, Image), non-spatial formats (Table), or a combination (Mixed).
* Similar Aardvark element: This has been replaced in Aardvark with the multi-valued [Resource Type](../ogm-aardvark/#resource-type), which uses a controlled vocabulary drawn from Library of Congress cartographic genres and GIS geometries.

**Is Part Of (`dct_isPartOf_sm`)**

* GBL 1.0 Description: This multi-valued GBL 1.0 plain text field is for writing out the name of a collection. Example: `dct_isPartOf_sm:"Village Maps of India"`
* Similar Aardvark element: The field name is the same in Aardvark, but it is now a non-literal field. The value must be one or more IDs that reference another record within the system. Example: `dct_isPartOf_sm:"princeton-z603r079s"`
