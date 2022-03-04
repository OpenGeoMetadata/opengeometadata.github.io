---
layout: default
title: Access Rights
parent: OGM Aardvark
grand_parent: Current Schema
nav_order: 31
---

## Access Rights

| Label                 | Access Rights                                                                                                                                                                                                                                    |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Order           | 31                                                                                                                                                                                                                                               |
| URI                   | `dct_accessRights_s`                                                                                                                                                                                                                             |
| Obligation            | Required                                                                                                                                                                                                                                         |
| Multiplicity          | 1-1                                                                                                                                                                                                                                              |
| Field type            | string                                                                                                                                                                                                                                           |
| Purpose               | To clarify to the user if the resource is public (any user can access) or restricted (a user will need to log in to some kind of authentication protocol) and if the application should provide a web service preview and/or a download function |
| Entry Guidelines      | Only one of two values are allowed: Public or Restricted.                                                                                                                                                                                        |
| Commentary            | This field can be set to "Public", which allows users to view and download an item, or "Restricted", which requires a user to log in to an authentication service.                                                                               |
| Controlled Vocabulary | yes - strict                                                                                                                                                                                                                                     |
| Example value         | "Public"                                                                                                                                                                                                                                         |
| Element Set           | DCMI                                                                                                                                                                                                                                             |
| Group                 | Rights                                                                                                                                                                                                                                           |
