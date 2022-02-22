---
layout: default
title: Spatial Extent
parent: Aardvark Schema
nav_order: 18.5
---

## Spatial Extent

| Label                 | Spatial Extent                                                                                                           |
|:--------------------- |:------------------------------------------------------------------------------------------------------------------------ |
| Aardvark-id           | ?                                                                                                                        |
| URI                   | `dcat_bbox`                                                                                                              |
| Obligation            | Recommended                                                                                                              |
| Multiplicity          | 0-1                                                                                                                      |
| Field type            | string                                                                                                                   |
| Purpose               | To support overlap ratio boosting in spatial searches                                                                    |
| Entry Guidelines      | This should be a bounding box in this format: ENVELOPE(w,e,n,s).                                                         |
| Commentary            |                                                                                                                          |
| Controlled Vocabulary | no                                                                                                                       |
| Example value         | "ENVELOPE(-117.312, -115.39, 84.31, 83.1)"                                                                               |
| Element Set           | DCAT                                                                                                                     |
| Group                 | Spatial                                                                                                                  |
