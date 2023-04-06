---
hide:
  - toc
---

# ID

| Label                 | ID       |
|:----------------------|:---------|
| URI                   | `id` |
| Obligation            | Required |
| Multivalued           | false |
| Field type            | string |
| Purpose               | To provide a unique alpha-numeric ID for the item that will act as the primary key in Solr and to create a unique landing page for the item |
| Entry Guidelines      | This string must be a globally unique value. The value should be alpha-numeric characters separated by dashes. |
| Commentary            | This field makes up the URL for the resource in GeoBlacklight. It is visible to the user and is used to create permalinks. The value should be alpha-numeric characters separated by dashes. If having a readable slug is desired, it is common to use the form `institution-keyword1-keyword2`. It should also be globally unique across all institutions in *your* GeoBlacklight index. |
| Controlled Vocabulary | no |
| Example value         | `"princeton-rv042w38t"` |
| Element Set           | GBL |
| Group                 | Administrative |
