---
layout: default
title: ID
parent: Aardvark Schema
nav_order: 35
---

## ID

| Label                 | ID                                                                                                                                                                                                           |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Aardvark-id           | 35                                                                                                                                                                                                           |
| URI                   | `id`                                                                                                                                                                                                         |
| Obligation            | Required                                                                                                                                                                                                     |
| Multiplicity          | 1-1                                                                                                                                                                                                          |
| Field type            | string                                                                                                                                                                                                       |
| Purpose               | To provide a unique alpha-numeric ID for the item that will act as the primary key in Solr and to create a unique landing page for the item                                                                  |
| Entry Guidelines      | This string must be a globally unique value. The value should be alpha-numeric characters separated by dashes.                                                                                               |
| Commentary            | The ID makes up the URL for the resource in GeoBlacklight. If having a readable slug is desired, it is common to use the form, institution-keyword1-keyword2 (words or characters are separated by hyphens). |
| Controlled Vocabulary | no                                                                                                                                                                                                           |
| Example value         | "princeton-rv042w38t"                                                                                                                                                                                        |
| Element Set           | GBL                                                                                                                                                                                                          |
| Group                 | Administrative                                                                                                                                                                                               |
