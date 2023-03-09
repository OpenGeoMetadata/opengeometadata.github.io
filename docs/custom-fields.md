# Custom fields

If an organization wishes to implement a custom metadata field for their GeoBlacklight instance, the naming schema should reference the organization as follows: `organization_elementName_solrFieldType`.

Examples:

* `b1g_code_s` - Internal code that organizes items by their source collection
* `nyu_addl_dspace_s` - A 5 digit number that is the "internal identifier" for DSpace, the repository software that mints handles for all NYU's items. The internal id must be paired with the handle in order to post metadata and data via the system API.
