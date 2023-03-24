---
hide:
  - toc
---

# Georeferenced

| Label                 | Georeferenced |
|:----------------------|:--------------|
| URI                   | `gbl_georeferenced_b` |
| Obligation            | Optional |
| Multivalued           | false |
| Field type            | boolean or string |
| Purpose               | To indicate whether or not a scanned map or other imagery has a georeferenced version |
| Entry Guidelines      | Only one of two values are allowed: true or false. |
| Commentary            | This field can be a shortcut for users to find georeferenced maps. Administrators can also employ the [Source](source) field to link a paper map with its scan (e.g. a TIFF) and its georeferenced version (e.g. a GeoTIFF). |
| Controlled Vocabulary | yes - strict |
| Example value         | `false` or `"false"` |
| Element Set           | GBL |
| Group                 | Administrative |
