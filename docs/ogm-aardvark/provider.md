---
layout: default
title: Provider
parent: OGM Aardvark
nav_order: 7
---

## Provider

| Label                 | Provider                |
|:----------------------|:------------------------|
| URI                   | `schema_provider_s`     |
| Obligation            | Recommended             |
| Multivalued           | false                   |
| Field type            | string                  |
| Purpose               | To clarify which organization is holds the resource or acts as the custodian for the metadata record and to help users understand which resources they can access |
| Entry Guidelines      | The value for this field is ideally be one of the names for each institution that have been coded in the GeoBlacklight application. This will embed the correct icon into the search results and item pages. |
| Commentary            | This field previously was known as "Provenance". If the value matches one of the [SVG images](https://github.com/geoblacklight/geoblacklight/tree/main/app/assets/images/blacklight) in the application, it will display as an icon next to the title. GeoBlacklight organizations are encouraged to submit institutional icons to the project. |
| Controlled Vocabulary | yes - not strict        |
| Example value         | `"University of Minnesota"` |
| Element Set           | schema.org              |
| Group                 | Administrative - entity |
