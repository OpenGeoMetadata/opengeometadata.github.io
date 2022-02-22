---
layout: default
title: Date Issued
parent: OGM Aardvark
grand_parent: Current Schema
nav_order: 14
---

## Date Issued

| Label                 | Date Issued                                                                                                                                                                                                                                                                                              |
|:----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 14                                                                                                                                                                                                                                                                                                       |
| URI                   | `dct_issued_s`                                                                                                                                                                                                                                                                                           |
| Obligation            | Optional                                                                                                                                                                                                                                                                                                 |
| Multiplicity          | 0-1                                                                                                                                                                                                                                                                                                      |
| Field type            | string                                                                                                                                                                                                                                                                                                   |
| Purpose               | To provide the user with the date when an item was published, and for administrators to determine the age of the resource                                                                                                                                                                                |
| Entry Guidelines      | A single year is the preferred format. For more precise dates, use the ISO format without the time value: YYYY-MM-DD or YYYY-MM.                                                                                                                                                                         |
| Commentary            | Although the field is optional, it is often useful when a clear [Temporal Coverage](https://opengeometadata.github.io/docs/aardvarkSchema/temporal-coverage) value is not present. For example, one may want to preserve a dataset with an uncertain lineage, but there is an indicator on a data portal on the date of last update. In most cases, the 4-digit year is sufficient. |
| Controlled Vocabulary | no                                                                                                                                                                                                                                                                                                       |
| Example value         | "1999"                                                                                                                                                                                                                                                                                                   |
| Element Set           | DCMI                                                                                                                                                                                                                                                                                                     |
| Group                 | Temporal                                                                                                                                                                                                                                                                                                 |
