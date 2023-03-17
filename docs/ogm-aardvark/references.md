---
hide:
  - toc
---

# References

| Label                 | References |
|:----------------------|:-----------|
| URI                   | `dct_references_s` |
| Obligation            | Suggested |
| Multivalued           | false |
| Field type            | string (serialized JSON) |
| Purpose               | To provide external URLs for accessing or describing the resource |
| Entry Guidelines      | This field defines external services and references using the CatInterOp approach. The field value is a serialized JSON array of key/value pairs, with keys representing namespace URI's and values the URL. [See the Configuring External Links page for detailed information about configuring this field.](../configuring-external-links.md)|
| Commentary            | All of the external links for the resource are added to This field as a serialized JSON array of key/value pairs. The download key/value pair is unique, because the value can be an array.                      |
| Controlled Vocabulary | yes - see [Reference URIs](../reference-uris.md)|
| Example value         | ```"{\"http://schema.org/url\":\"http://purl.stanford.edu/bm662dm5913\",```<br>```\"http://schema.org/downloadUrl\":\"http://stacks.stanford.edu/file/druid:bm662dm5913/data.zip\"}"```                      |
| Element Set           | DCMI |
| Group                 | Distribution |


