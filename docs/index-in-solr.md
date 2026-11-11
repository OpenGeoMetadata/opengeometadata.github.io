# Index Metadata in Solr

!!! note

	This page is a work in progress and needs more information.

Metadata records must be indexed in Solr in order to integrate with GeoBlacklight. The Solr application identifies each metadata record as a “document.” The process of adding documents to Solr is called “indexing.”

## Option A: Indexing manually

If you have access to your Solr Dashboard panel, you can add records manually by pasting them into the Documents pane.

## Option B: Indexing via scripts

It is often more practical to use a process for batch adding, updating, and deleting the records. Most of the available processes are in the form of command-line scripts. See the [Metadata Scripts](../scripts) for examples.

## Deleting records from Solr

To delete records, send their identifiers to Solr's update handler, then commit. Use the value of `id` for OGM Aardvark records, or `layer_slug_s` for GBL 1.0 records:

```sh
curl -X POST -H 'Content-Type: application/json' \
  'http://localhost:8983/solr/blacklight-core/update?commit=true' \
  --data-binary '{"delete": ["princeton-rv042w38t", "stanford-bb058zh0946"]}'
```

Deleting an identifier that isn't in the index does nothing, so it is safe to repeat.

!!! warning

	Use caution when deleting by query instead of by identifier. Identifiers can contain characters such as `:` and `-` that have special meaning in a Solr query, and a mistyped query can delete far more than you intended.

If you harvest from OpenGeoMetadata, records that institutions withdraw are listed in their `withdrawn.json` files. See [Handling withdrawn records](../harvest-ogm/#handling-withdrawn-records).
