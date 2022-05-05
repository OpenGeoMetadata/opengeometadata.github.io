---
layout: default
title: WxS Identifier
parent: OGM Aardvark
nav_order: 34
---

## WxS Identifier

| Label                 | WxS Identifier                                                                                                                                                        |
|:----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Order           | 34                                                                                                                                                                    |
| URI                   | `gbl_wxsIdentifier_s`                                                                                                                                                 |
| Obligation            | Conditional                                                                                                                                                           |
| Multiplicity          | 0-1 or 1-1                                                                                                                                                            |
| Field type            | string                                                                                                                                                                |
| Purpose               | To identify the layer or store for a WFS, WMS, or WCS web service so the application can construct the full web service link                                            |
| Entry Guidelines      | Only the layer name is added here. The base service endpoint URLs (e.g. "https://maps-public.geo.nyu.edu/geoserver/sdr/wms") are added to the [References](https://opengeometadata.github.io/docs/aardvarkSchema/references) field. |
| Commentary            | The WxS Indentifer is used to point to specific layers within an OGC geospatial web service. This field is not used for ArcGIS Rest Services.                         |
| Controlled Vocabulary | no                                                                                                                                                                    |
| Example value         | "druid:vr593vj7147"                                                                                                                                                   |
| Element Set           | GBL                                                                                                                                                                   |
| Group                 | Distribution                                                                                                                                                          |
