---
layout: default
title: Geometry
parent: Aardvark Schema
nav_order: 18
---

## Geometry

| Label                 | Geometry                                                                                                        |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 18                                                                                                                       |
| URI                   | `locn_geometry`                                                                                                          |
| Obligation            | Recommended                                                                                                              |
| Multiplicity          | 0-1                                                                                                                      |
| Field type            | string                                                                                                                   |
| Purpose               | To display the extent of the resource and to power the map search                                                        |
| Entry Guidelines      | This may be a bounding box or more complex geometry. For a bounding box, it should be in this format: ENVELOPE(w,e,n,s). |
| Commentary            | This field can contain any valid WKT or ENVELOPE string.                                                                 |
| Controlled Vocabulary | no                                                                                                                       |
| Example value         | For bounding boxes: "ENVELOPE(-117.312, -115.39, 84.31, 83.1)"<br>For geometries: "POLYGON((1 8, 1 9, 2 9, 2 8, 1 8))"<br>or "MULTIPOLYGON (((30 20, 45 40, 10 40, 30 20)),((15 5, 40 10, 10 20, 5 10, 15 5)))"  |
| Element Set           | LOCN                                                                                                              |
| Group                 | Spatial                                                                                                                  |
