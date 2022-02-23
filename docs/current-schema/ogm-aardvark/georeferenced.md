---
layout: default
title: Georeferenced
parent: OGM Aardvark
grand_parent: Current Schema
nav_order: 41
---

## Georeferenced

| Label                 | Georeferenced                                                                                                                                                                                                          |
|:----------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 41                                                                                                                                                                                                                     |
| URI                   | `gbl_georeferenced_b`                                                                                                                                                                                                  |
| Obligation            | Optional                                                                                                                                                                                                               |
| Multiplicity          | 0-1                                                                                                                                                                                                                    |
| Field type            | string boolean                                                                                                                                                                                                         |
| Purpose               | To indicate whether or not a scanned map or other imagery has a georeferenced version                                                                                                                                  |
| Entry Guidelines      | Only one of two values are allowed: true or false.                                                                                                                                                                     |
| Commentary            | This field can be a shortcut for users to find georeferenced maps. Administrators can also employ the [Source](https://opengeometadata.github.io/docs/aardvarkSchema/source) field to link a paper map with its scan (e.g. a TIFF) and its georeferenced version (e.g. a GeoTIFF). |
| Controlled Vocabulary | yes - strict                                                                                                                                                                                                           |
| Example value         | false                                                                                                                                                                                                                  |
| Element Set           | GBL                                                                                                                                                                                                                    |
| Group                 | Administrative                                                                                                                                                                                                         |
