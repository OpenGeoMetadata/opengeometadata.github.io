# Spatial fields

[OGM Aardvark](../ogm-aardvark) has five different fields in the "spatial" group:

- [Spatial Coverage](ogm-aardvark/spatial-coverage.md) (S)
- [Geometry](ogm-aardvark/geometry.md) (S)
- [Bounding Box](ogm-aardvark/bounding-box.md) (S)
- [Centroid](ogm-aardvark/centroid.md)
- [Georeferenced](ogm-aardvark/georeferenced.md)

The first three -- marked with (S) -- are suggested fields that most records should probably have.

**Spatial Coverage** is a text field that contains one or more place names that describe the extent of an item.  This field is used for text searches.

The next two fields, **Geometry** and **Bounding Box**, describe the geometry of the extent.  Both can be simple bounding boxes in the form `ENVELOPE(-111.1, -104.0, 40.5, 40.9)`.  The functional difference is that **Geometry** is used to power the map search (does the item intersect the query bounding box?) and also to display the extent in the search results map, whereas **Bounding Box** is only used to enable overlap ratio boosting as part of the overall relevance ranking algorithm.

The **Geometry** field also supports more complex geometries (using the `POLYGON(...)` or `MULTIPOLYGON(...)` syntax) such as polygons that more accurately represent a non-rectangular extent, or multi-polygons that can be used to better represent extents that span the 180th meridian.  (In order to keep small record sizes, these should still be relatively simple geometries, rather than high-resolution detailed boundaries.)

**Centroid** is a completely optional field that is only used in some customized GBL instances to display search results as a set of points on the map.

**Georeferenced** is a boolean field (true/false) that is used to indicate whether a digital image, for example, has been [georeferenced](https://gistbok.ucgis.org/bok-topics/georeferencing-and-georectification).

More details can be found in the documentation for each field.