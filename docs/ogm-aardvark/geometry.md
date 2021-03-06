---
layout: default
title: Geometry
parent: OGM Aardvark
nav_order: 18
---

## Geometry

| Label                 | Geometry                                                                                                        |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------|
| Order           | 18                                                                                                                       |
| URI                   | `locn_geometry`                                                                                                          |
| Obligation            | Recommended                                                                                                              |
| Multiplicity          | 0-1                                                                                                                      |
| Field type            | string                                                                                                                   |
| Purpose               | To display the extent of the resource and to power the map search                                                        |
| Entry Guidelines      | This may be a bounding box or more complex geometry. For a bounding box, it should use the ENVELOPE(w,e,n,s) syntax. For a more complex geometry, it should use the WKT ("well-known text") POLYGON or MULTIPOLYGON syntax. Note that WKT polygon vertices should be defined in counter-clockwise order. |
| Commentary            |  Since this field is not repeatable, multiple polygons should be represented using the WKT "MULTIPOLYGON" syntax. Geometries that span the 180th Meridian, aka the Antimeridian, should be broken up into multiple bounding boxes or polygons for each side of the earth's hemisphere. This is because Solr, the underlying indexer for GeoBlacklight, can not interpret these coordinates correctly and will display the geometry improperly (horizontally flipped).  |
| Controlled Vocabulary | no                                                                                                                       |
| Example value         | Simple bounding box: "ENVELOPE(-111.1, -104.0, 45.0, 40.9)"<br>Bermuda Triangle: "POLYGON((-80 25, -65 18, -64 33, -80 25))"<br>Split bounding box for Alaska: "MULTIPOLYGON (((-179.3 51.1, -129.9 51.1, -129.9 71.5, -179.3 71.5, -179.3 51.1)),((172.3 51.2, 179.9 51.2, 179.9 53.1, 172.3 53.1, 172.3 51.2)))"  |
| Element Set           | LOCN                                                                                                              |
| Group                 | Spatial                                                                                                                  |
