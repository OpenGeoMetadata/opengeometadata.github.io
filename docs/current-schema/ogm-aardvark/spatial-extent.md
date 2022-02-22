---
layout: default
title: Spatial Extent
parent: Aardvark Schema
nav_order: 18
---

## Spatial Extent

| Label                 | Spatial Extent                                                                                                           |
|:--------------------- |:------------------------------------------------------------------------------------------------------------------------ |
| Aardvark-id           | 18                                                                                                                       |
| URI                   | `locn_geometry`                                                                                                          |
| Obligation            | Recommended                                                                                                              |
| Multiplicity          | 0-*                                                                                                                      |
| Field type            | string                                                                                                                   |
| Purpose               | To display the extent of the resource and to power the map search                                                       |
| Entry Guidelines      | This may be a bounding box or more complex geometry. For a bounding box, it should be in this format: ENVELOPE(w,e,n,s). |
| Commentary            | This field can support bounding boxes or complex geometries.                                                             |
| Controlled Vocabulary | no                                                                                                                       |
| Example value         | For bounding boxes: "ENVELOPE(-97.251,-90.9229,49.3788,43.4649)"<br>For geometries:                                      |
| Element Set           | LOCN/DCAT                                                                                                                |
| Group                 | Spatial                                                                                                                  |
