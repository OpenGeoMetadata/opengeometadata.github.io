---
layout: default
title: Bounding Box
parent: OGM Aardvark
nav_order: 19
---

## Bounding Box

| Label                 | Bounding Box                                                                                                             |
|:--------------------- |:------------------------------------------------------------------------------------------------------------------------ |
| Order           | 19                                                                                                                       |
| URI                   | `dcat_bbox`                                                                                                              |
| Obligation            | Recommended                                                                                                              |
| Multiplicity          | 0-1                                                                                                                      |
| Field type            | string                                                                                                                   |
| Purpose               | To support overlap ratio boosting in spatial searches                                                                    |
| Entry Guidelines      | This should be a bounding box in this format: ENVELOPE(w,e,n,s).                                                         |
| Commentary            | If the `locn_geometry` field uses the ENVELOPE syntax, then these fields will be identical.                              |
| Controlled Vocabulary | no                                                                                                                       |
| Example value         | "ENVELOPE(-111.1, -104.0, 45.0, 40.9)"                                                                                   |
| Element Set           | DCAT                                                                                                                     |
| Group                 | Spatial                                                                                                                  |
