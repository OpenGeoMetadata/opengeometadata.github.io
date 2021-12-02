---
layout: default
title: Date Range
parent: Aardvark Schema
nav_order: 16
---

## Date Range

| Label                 | Date Range                                                                                         |
|:----------------------|:---------------------------------------------------------------------------------------------------|
| Aardvark-id           | 16                                                                                                 |
| URI                   | `gbl_dateRange_drsim`                                                                              |
| Obligation            | Optional                                                                                           |
| Multiplicity          | 0-*                                                                                                |
| Field type            | date-range                                                                                         |
| Purpose               | To power other time widgets that use a date range                                                  |
| Entry Guidelines      | Enter a start date and end date in the Solr daterange field convention. In JSON, the value should be formatted as a string that includes the brackets, rather than as an array or list containing a string. Incorrect: ["YYYY to YYYY"] - Correct: "[YYYY to YYYY]" |
| Commentary            | This field is not yet supported by GeoBlacklight, but the application can be customized to use it. |
| Controlled Vocabulary | no                                                                                                 |
| Example value         | "[1980 to 1995]"                                                                                     |
| Element Set           | GBL                                                                                                |
| Group                 | Temporal                                                                                           |
