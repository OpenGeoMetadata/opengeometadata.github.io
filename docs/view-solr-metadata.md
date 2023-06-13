# View Solr Metadata in GeoBlacklight

GeoBlacklight can display the raw metadata for a published item by appending one of the following extensions to the end of an item's show page URL:

### `url.xml`

* Produces a Dublin Core XML document in the [OAI_DC schema](https://www.openarchives.org/OAI/2.0/oai_dc.xsd).
* The fields for this document can be adjusted in the `solr_document.rb`, which is found here: `app/models/solr_document.rb`.

!!! example

	[https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677.xml](https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677.xml)

### `url.json`

Depending on your version, this will produce either:

* A nested JSON document of the metadata that appears on the item page (this document can be harvested by the [JSON:API](https://jsonapi.org/) protocol), OR

* A full metadata file for the item as a flat JSON document (up to GeoBlacklight version 1.9).

!!! example

	[https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677.json](https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677.json)


### `url/raw`

* Only available for GeoBlacklight versions 2.0+.
* Displays the full metadata file for the item as a flat JSON document.

!!! example

	[https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677/raw](https://geo.btaa.org/catalog/145055E1-87EF-4D13-B138-4DC3907F3677/raw)


!!! note "Chart of viewing options"

    === "GBL versions 2.0 and beyond"

        * `url.xml`: Dublin Core XML document
        * `url.json`: nested JSON document of only the metadata that appears on the item page
        * `url/raw`: flat JSON document of all metadata associated with the item



    === "GBL < versions 1.9"

        * `url.xml`: Dublin Core XML document
        * `url.json`: flat JSON document of all metadata associated with the item
