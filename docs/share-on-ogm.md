[View our GitHub repositories](https://github.com/OpenGeoMetadata){ .md-button }

Contributors are invited to share their metadata via our GitHub organization, which allows other institutions to periodically harvest and ingest the records into their own catalogs for wider exposure. Follow the steps below to get started.

## 1. Submit a request

Submit a request to set up a new repository for your organization
To get started, identify one member from your institution who will be added to the OpenGeoMetadata organization as an owner. Owners are able to create, enable, and manage rights for their own institution's team (e.g., add collaborators, contributors, and reviewers).

Submit a request to join OpenGeoMetadata as an owner by commenting on this issue in our GitHub repo: [Add members to OpenGeoMetadata group #8](https://github.com/OpenGeoMetadata/metadatarepository/issues/8).

## 2. Choose a name

Choose a unique namespace for your repository. Participating institutions are able to create their own unique namespace. This ensures that each institution maintains and is responsible for unique identifiers that correspond with items or layers in its collection.

- The most common format is to list the domain (.edu, .org, .uk) and then the institution’s name: `edu.institution`.
- An institution using unique identifiers with a linked persistent URL, like [ARK](https://en.wikipedia.org/wiki/Archival_Resource_Key), may want to name their repository with a suffix: `edu.institution.arks`.
- Providers with very large collections can break them up into separate repositories and add a suffix, e.g. `gov.usgs.tnm` and `gov.usgs.htmc` for two different sets of public data offered by USGS.

Here are some examples of each of the following conventions:

- Princeton: [edu.princeton.arks](https://github.com/OpenGeoMetadata/edu.princeton.arks)
- Stanford: [edu.stanford.purl](https://github.com/OpenGeoMetadata/edu.stanford.purl)
- New York University: [edu.nyu](https://github.com/OpenGeoMetadata/edu.nyu)
- Big Ten Academic Alliance: [geobtaa](https://github.com/OpenGeoMetadata/geobtaa)
- USDA NAIP imagery: [gov.udsa.naip](https://github.com/OpenGeoMetadata/gov.usda.naip)

Note that these are conventions and not strict rules; any name valid on GitHub is allowed.

## 3. Select a structure

Select a directory structure for your repository. Metadata files in GitHub can be organized within directories (i.e., folders) using various structures.

### Flat

For an organization with a small number of records (e.g., 250 records), a basic, flat directory structure within a repository is acceptable. A separate directory should be created for each layer or item described, then named according to the layer's unique identifier. Each directory should contain the metadata for that layer, in whichever standardized format an institution deems appropriate. The following is an example of one directory per item:

```
layer123/
layer124/
layer125/
```

### Categorical

Some institutions may want to organize their records into logical groupings. For example, folders could be named for the Resource Class (i.e., Datasets, Maps), Collection, Date of Accession, or other attribute. With this structure, multiple layer files could be placed in the same directory, providing they have unique filenames. In the following example, an institution has divided records by their collection:

```
Datasets/
Hist_Aerials/
Indexes/
Maps/
State_Fed_Orthoimagery/
```

### Hashed

Institutions that have a large number of records (e.g., greater than several thousand) may enhance repository performance by dividing the records into a hashed directory. This involves creating nested subdirectories, typically by using an item’s ID to programmatically name them. In the following example, the item’s ID is on the left and the set of nested folders is on the right:

```
bb338jh0716: bb/338/jh/0716
bb509gh7292: bb/509/gh/7292
bc899yk4538: bc/899/yk/4538
```

A hashed directory structure makes it easy to include additional materials and documentation related to an individual resource. For example, a directory might contain metadata in multiple geospatial metadata formats, as well as auxiliary files like preview images.

```
/bc/899/yk/4538/geoblacklight.json
                iso19110.xml
                iso19139.html
                iso19139.xml
                mods.xml
                preview.jpg
```

These structures are also easier to browse online, because GitHub will truncate the number of displayed items in a directory when it exceeds a few thousand.

!!! note

    Institutions may choose to use a combination of structures, such as hashed directories within categorical folders.

## 4. Determine file names

Determine the file-naming rules for your metadata. There are two main approaches to naming metadata files: naming by the item's ID or naming by the file's metadata standard.

### Naming by item ID

Each record has a unique filename based on the item’s ID. This allows multiple records to be stored in the same directory.

```
/HGL4/json/CAMBRIDGE09_ADDRESSBLOCKS.json
           CAMBRIDGE09_ADDRESSPOINTS.json
           CAMBRIDGE09_BIKEFACILITIES.json
           CAMBRIDGE09_BIKERACKS.json
           CAMBRIDGE09_BLOCKGROUPS1990.json
           CAMBRIDGE09_BLOCKGROUPS2000.json
           ...
```

### Naming by metadata standard

All records use the same filename pattern, such as `*/geoblacklight.json` or `*/fgdc.json`. This requires each layer to have its own folder.

**Optional: layers.json**

Adopting the file-naming by metadata standard approach can make it difficult for end-users to find the relevant metadata files for an item of interest. Including a `layers.json` file in the main repository folder allows for easy mapping of layers to their location within an organization's repository (e.g., `Layer-Id : Folder`). See the [edu.stanford.purl](https://github.com/OpenGeoMetadata/edu.stanford.purl/blob/master/layers.json) repository for an example:

```
{
  "druid:bb338jh0716": "bb/338/jh/0716",
  "druid:bb509gh7292": "bb/509/gh/7292",
  "druid:bc899yk4538": "bc/899/yk/4538",
  ...
}
```

!!! note

    Harvesters should harvest all of the JSON-format records found in a repository that match the target schema version, regardless of the subdirectory structure.

## 5. Document your repository

In order to help other institutions find and use the metadata your institution is contributing, the `ReadMe.md` file should describe basic information about the repository’s file structure, metadata version and customizations, update frequency, and so on. See the [edu.nyu](https://github.com/OpenGeoMetadata/edu.nyu) repository for an example.

You may use the following template to structure your `ReadMe.md`:

```
# Repository Title

Description and link to your institution’s GeoBlacklight instance.

## File Structure

Information about how the repository is structured.

## Our Metadata

Information about your metadata:
* GeoBlacklight metadata version (1.0 or Aardvark)
* Custom fields
* Any other metadata formats that are included in the repository (e.g. ISO 19139, ISO 19110, MODS)
* How often the repository is updated
* How metadata is validated, if applicable

## How to Contribute

Contact information; whether or not your repository is open for metadata contributions and enhancements.
```

## 6. Opt-in to sharing

Many OGM institutions use [GeoCombine](https://github.com/OpenGeoMetadata/GeoCombine), a Ruby-based toolkit designed to automate the harvesting process. As of version v0.10.0 of GeoCombine, repositories must opt-in to harvesting by declaring their supported OGM schema version(s). This helps GeoCombine skip harvesting of any repository that offers no records in the user's desired schema version, substantially speeding up the harvest process. Repositories that opt-in by declaring a supported schema will be automatically harvested by GeoCombine the next time the tool is run.

To opt-in to metadata sharing, [add custom properties](https://docs.github.com/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization#adding-custom-properties) to your repository indicating the metadata schema(s) used:

- [`Aardvark`](https://github.com/orgs/OpenGeoMetadata/repositories?q=props.supported_schemas%3AAardvark) - includes metadata in the [OGM Aardvark schema](https://opengeometadata.org/ogm-aardvark)
- [`1.0`](https://github.com/orgs/OpenGeoMetadata/repositories?q=props.supported_schemas%3A1.0) - includes metadata in the (deprecated) [GeoBlacklight 1.0 schema](https://opengeometadata.org/gbl-1.0/)

### Additional tags

You can also add corresponding [topics](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/classifying-your-repository-with-topics) to your repository to publicly indicate its purpose. Some topics you might consider adding include:

- `ogm-aardvark` - indicates that the repository contains metadata in the [OGM Aardvark schema](https://opengeometadata.org/ogm-aardvark)
- `gbl-1.0` - indicates that the repository contains metadata in the [GeoBlacklight 1.0 schema](https://opengeometadata.org/gbl-1.0/)
- `fgdc` - indicates that the repository contains metadata in the [FGDC schema](https://www.fgdc.gov/metadata/csdgm-standard)
- `iso19139` - indicates that the repository contains metadata in the [ISO 19139 schema](https://www.iso.org/standard/67253.html)

Finally, consider also adding an open license to your metadata repository, such as [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/).
