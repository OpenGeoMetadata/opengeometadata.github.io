---
layout: default
title: Format
parent: Aardvark Schema
nav_order: 32
---

## Format

| Label                 | Format                                                                                                                                                                                                                                                                                        |
|:----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 32                                                                                                                                                                                                                                                                                            |
| URI                   | `dct_format_s`                                                                                                                                                                                                                                                                                |
| Obligation            | Conditional                                                                                                                                                                                                                                                                                   |
| Multiplicity          | 0-1 or 1-1                                                                                                                                                                                                                                                                                    |
| Field type            | string                                                                                                                                                                                                                                                                                        |
| Purpose               | To display to the user the name of the file type as a text string in the download button                                                                                                                                                                                                      |
| Entry Guidelines      | Required if the download URL is configured as a single key:value pair.                                                                                                                                                                                                                        |
| Commentary            | A long list of formats is available here. The most important thing to remember is that this field is required for download functionality if using a single-value string for downloads (pre-GeoBlacklight version 3.0). See the [Multiple Downloads guide](https://github.com/geoblacklight/geoblacklight/wiki/multiple-download-links) for more details. |
| Controlled Vocabulary | yes - not strict                                                                                                                                                                                                                                                                              |
| Example value         | "Shapefile"                                                                                                                                                                                                                                                                                   |
| Element Set           | DCMI                                                                                                                                                                                                                                                                                          |
| Group                 | Distribution                                                                                                                                                                                                                                                                                  |
