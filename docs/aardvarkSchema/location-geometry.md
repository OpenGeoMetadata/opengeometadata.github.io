---
layout: default
title: Spatial Extent
parent: Aardvark Schema
nav_order: 18
---

## Spatial Extent

| Label                 | Spatial Extent                                                                                                           |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 18                                                                                                                       |
| URI                   | `locn_geometry`                                                                                                          |
| Obligation            | Recommended                                                                                                              |
| Multiplicity          | 0-*                                                                                                                      |
| Field type            | string                                                                                                                   |
| Purpose               | To display the extent of the resource and to power the map search                                                        |
| Entry Guidelines      | This may be a bounding box or more complex geometry. For a bounding box, it should be in this format: ENVELOPE(w,e,n,s). |
| Commentary            | This field can contain any valid WKT or ENVELOPE string.                                                                 |
| Controlled Vocabulary | no                                                                                                                       |
| Example value         | For bounding boxes: "ENVELOPE(-117.312, -115.39, 84.31, 83.1)"<br>For geometries: "POLYGON((1 8, 1 9, 2 9, 2 8, 1 8))"       |
| Element Set           | LOCN                                                                                                              |
| Group                 | Spatial                                                                                                                  |
