---
layout: default
title: Get Started
nav_order: 2
---

# Get Started with OpenGeoMetadata
{: .no_toc }

Make it easy for others to find and use your geospatial metadata
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## How OpenGeoMetadata works

The goal of participating in OpenGeoMetadata is to enable other institutions to find and use your institution’s metadata in their own local repositories, increasing the visibility and discoverability of your geospatial assets.

Each collaborating institution creates and maintains its own geospatial metadata repository within the [OpenGeoMetadata organization](https://github.com/opengeometadata). This ensures that each institution has a unique namespace and can manage its own internal users who can collaborate on their metadata, while still enabling machine-harvestable metadata under a common organization. It also means that each institution is responsible for enforcing its own metadata standards.

**What metadata schema can we use?**

Many different metadata standards and schemas can be shared in OpenGeoMetadata. A common approach is to share JSON files in a lightweight metadata schema (documented on this site) that was designed especially for the discovery platform [GeoBlacklight](https://github.com/geoblacklight). These files can be ingested into any GeoBlacklight instance, and the harvesting process can be done manually or with the help of [GeoCombine](https://github.com/OpenGeoMetadata/GeoCombine), a Ruby-based toolkit designed to automate the harvesting process. Note that GeoCombine will harvest all metadata records in an OpenGeoMetadata repository that end with the extension `.json`, regardless of how the records are structured.

Institutions may prefer to use other geospatial metadata standards in addition to – or instead of – the GeoBlacklight schema, such as ISO 19115 or the FGDC Content Standard for Digital Geospatial Metadata. Traditional library catalogs may use general purpose standards, such as MARC or MODS. Any institution is welcome to maintain an OpenGeoMetadata repository even if they do not use GeoBlacklight.

## Nominate a team member to become an organization owner

To get started, identify one member from your institution who will be added to the OpenGeoMetadata organization as an owner. Owners are able to create, enable, and manage rights for their own institution's team (e.g., add collaborators, contributors, and reviewers).

Submit a request to join OpenGeoMetadata as an owner by commenting on this issue in our GitHub repo: [Add members to OpenGeoMetadata group #8](https://github.com/OpenGeoMetadata/metadatarepository/issues/8).

## Choose a unique namespace for your repository

Participating institutions are able to create their own unique namespace. This ensures that each institution maintains and is responsible for unique identifiers that correspond with items or layers in its collection.

* The most common format is to list the domain (.edu, .org, .uk) and then the institution’s name: `edu.institution`.
* An institution using unique identifiers with a linked persistent URL, like [ARK](https://en.wikipedia.org/wiki/Archival_Resource_Key), may want to name their repository with a suffix: `edu.institution.arks`.
* Institutions or collaborative organizations can also choose to adopt their own name for an OpenGeoMetadata repository: `big-ten`.

Here are some examples of each of the following conventions:
* Princeton: [edu.princeton.arks](https://github.com/OpenGeoMetadata/edu.princeton.arks)
* Stanford: [edu.stanford.purl](https://github.com/OpenGeoMetadata/edu.stanford.purl)
* New York University: [edu.nyu](https://github.com/OpenGeoMetadata/edu.nyu)
* Big Ten Academic Alliance: [big-ten](https://github.com/OpenGeoMetadata/big-ten)

## Select a directory structure for your repository

Metadata files in GitHub can be organized within directories (i.e., folders) using various structures.

### Flat
{: .no_toc }

For an organization with a small number of records (e.g., 250 records), a basic, flat directory structure within a repository is acceptable. A separate directory should be created for each layer or item described, then named according to the layer's unique identifier. Each directory should contain the metadata for that layer, in whichever standardized format an institution deems appropriate. The following is an example of one directory per item:

```
layer123/
layer124/
layer125/
```

### Categorical
{: .no_toc }

Some institutions may want to organize their records into logical groupings. For example, folders could be named for the Resource Class (i.e., Datasets, Maps), Collection, Date of Accession, or other attribute. In the following example, an institution has divided records by their collection:

```
Datasets/
Hist_Aerials/
Indexes/
Maps/
State_Fed_Orthoimagery/
```

### Hashed
{: .no_toc }

Institutions that have a large number of records (e.g., greater than several thousand) may enhance repository performance by dividing the records into a hashed directory. This involves creating nested subdirectories, typically by using an item’s ID to programmatically name them. In the following example, the item’s ID is on the left and the set of nested folders is on the right:

```
bb338jh0716: bb/338/jh/0716
bb509gh7292: bb/509/gh/7292
bc899yk4538: bc/899/yk/4538
```

Institutions may choose to use a combination of structures, such as hashed directories within categorical folders.
{: .note}

A hashed directory structure makes it easy to include additional materials and documentation related to an individual resource. For example, a directory might contain metadata in multiple geospatial metadata formats, as well as auxiliary files like preview images. See the [edu.stanford.purl](https://github.com/OpenGeoMetadata/edu.stanford.purl/tree/master/bc/899/yk/4538) repository for an example:
```
/bc/899/yk/4538/geoblacklight.json
                iso19110.xml
                iso19139.html
                iso19139.xml
                mods.xml
                preview.jpg
```

## Determine the file-naming rules for your metadata

There are two main approaches to naming metadata files.

### Naming by item ID
{: .no_toc }

Each record has a unique filename based on the item’s ID. This allows multiple records to be stored in the same directory. See the [edu.harvard](https://github.com/OpenGeoMetadata/edu.harvard) repository for an example:

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
{: .no_toc }

All records use the same filename pattern, such as `*/geoblacklight.json` or `*/fgdc.json`. This requires each layer to have its own folder in a hashed directory structure.

**Optional: layers.json**

Adopting this file-naming approach can make it difficult for end-users to find the relevant metadata files for an item of interest. Including a `layers.json` file in the main repository folder allows for easy mapping of layers to their location within an organization's repository (e.g., `Layer-Id : Folder`). See the [edu.stanford.purl](https://github.com/OpenGeoMetadata/edu.stanford.purl/blob/master/layers.json) repository for an example:

```
{
  "druid:bb338jh0716": "bb/338/jh/0716",
  "druid:bb509gh7292": "bb/509/gh/7292",
  "druid:bc899yk4538": "bc/899/yk/4538",
  ...
}
```

## Document your repository

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

## Contribute to developing OpenGeoMetadata

Do you have an idea or question about how OpenGeoMetadata is working? Contribute your comments, proposals, and questions here: [OpenGeoMetadata/metadatarepository](https://github.com/OpenGeoMetadata/metadatarepository/issues).
