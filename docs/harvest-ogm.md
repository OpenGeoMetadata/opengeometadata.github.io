Metadata in OpenGeoMetadata can be freely harvested and ingested into other discovery applications. 

## Harvesting with GeoCombine

Many institutions harvest with [GeoCombine](https://github.com/OpenGeoMetadata/GeoCombine), which is bundled with GeoBlacklight. A harvest has three steps:

1. **Clone** the repositories you want into a local directory (`./tmp/opengeometadata` by default, or set `OGM_PATH`):

	```sh
	bundle exec rake geocombine:clone
	```

	Pass a repository name, such as `geocombine:clone[edu.stanford.purl]`, to clone just one.

2. **Pull** updates on later runs:

	```sh
	bundle exec rake geocombine:pull
	```

3. **Index** every record in the directory into Solr:

	```sh
	bundle exec rake geocombine:index
	```

When indexing, GeoCombine reads every `.json` file in the local directory except [repository files](../repository-files) such as `layers.json`. It skips records that are marked Restricted (unless `OGM_SKIP_RESTRICTED=false`) and records in a schema version other than `SCHEMA_VERSION` (OGM Aardvark by default). To leave out particular repositories, list them in `OGM_SKIP_REPOS`, separated by commas. Each record is added under its identifier (`id`, or `layer_slug_s` for GBL 1.0), so re-indexing a record replaces the previous copy. See the [GeoCombine README](https://github.com/OpenGeoMetadata/GeoCombine#readme) for all options.

## Handling withdrawn records

When an institution withdraws a record, it lists the record in a [`withdrawn.json`](../repository-files/#withdrawnjson) file at the root of its repository. A harvester that supports withdrawals, like GeoCombine, reads this file to determine what records need deletion from its index.

Some consequences to be aware of:

* **A missing file is never treated as a withdrawal.** If a record disappears from a repository without a `withdrawn.json` entry, it stays in the index. Records withdrawn before an institution adopted `withdrawn.json` also stay, unless it adds entries for them.
* **A withdrawn record's page returns "not found"** in platforms like GeoBlacklight once its record is deleted. GeoBlacklight does not render a placeholder page or redirect for it.
* **Repositories you stop harvesting don't delete anything.** If you add a repository to `OGM_SKIP_REPOS`, or it is archived, its records stay in your index until you remove them yourself. See [Deleting records from Solr](../index-in-solr/#deleting-records-from-solr).

## Suffixes

Altering suffixes can result in metadata schema incompatibilities across institutions. Any deviations in element names causes Solr to treat the elements as separate fields: for example `dct_subject_s` and `dct_subject_sm` would be stored separately. If GeoBlacklight is set up to display a facet for `dct_subject_s`, it will not pick up values stored in `dct_subject_sm` in the filter. Therefore, if you are gathering metadata from other institutions, make sure to inspect their metadata fields to determine if there will be inconsistencies in your Solr index.
