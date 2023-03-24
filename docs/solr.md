## Unique keys

Metadata for GeoBlacklight instances is stored and indexed in Solr, which uses a "Unique Key Field" as the identifier for each document. The OGM Aardvark schema was designed with `id` as the Unique Key Field (in GBL 1.0, this field was called `layer_slug_s`). Each item must have a unique key.

## Suffixes

Altering suffixes can result in metadata schema incompatibilities across institutions. Any deviations in element names causes Solr to treat the elements as separate fields: for example `dct_subject_s` and `dct_subject_sm` would be stored separately. If GeoBlacklight is set up to display a facet for `dct_subject_s`, it will not pick up values stored in `dct_subject_sm` in the filter. Therefore, if you are gathering metadata from other institutions, make sure to inspect their metadata fields to determine if there will be inconsistencies in your Solr index.