---
layout: default
title: Home
nav_order: 1
description: "Documentation about OpenGeoMetadata"
permalink: /
---

# Welcome to OpenGeoMetadata
{: .fs-9 }

A shared repository for geospatial metadata
{: .fs-6 .fw-300 }

[View our GitHub repositories](https://github.com/OpenGeoMetadata){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 } [Read our Wiki](https://github.com/OpenGeoMetadata/metadatarepository/wiki){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## About Us

OpenGeoMetadata is a federated metadata-sharing community. Our core purpose is to facilitate sharing geospatial metadata that uses the GeoBlacklight metadata schema. Contributors are invited to share their metadata via our GitHub organization, which allows other institutions to periodically harvest and ingest the records into their own GeoBlacklight instances for wider exposure.

The initiative was launched in 2015 as a collaboration between MIT, Princeton, and Stanford, and it has grown to include over 20 contributing organizations. It is a sister initiative to [GeoBlacklight](https://geoblacklight.org), an open-source Ruby on Rails software application for discovering geospatial content, and supports that work by providing a space to share GeoBlacklight-compliant metadata.

## How Does It Work?

Each collaborating organization creates its own individual repository within the OpenGeoMetadata organization. This ensures that it has a unique namespace (example: [edu.stanford.purl](https://github.com/OpenGeoMetadata/edu.stanford.purl)) and can manage its own internal users. It also means that enforcement of metadata standards is left up to each organization.

We recommend adopting a standard repository structure. Individual metadata records for each layer are contained within unique directories in a pear tree structure, and a file `layers.json` stored in the main directory links each unique identifier to its directory location. Check out [this example from Stanford](https://github.com/OpenGeoMetadata/edu.stanford.purl/tree/master/bc/899/yk/4538) to see how a typical repository is structured.

To get started as a contributor, visit our [GitHub respositories](https://github.com/OpenGeoMetadata) or our [GitHub wiki](https://github.com/OpenGeoMetadata/metadatarepository/wiki).
<br>
<br>
<br>
*Content from [OpenGeoMetadata](https://www.fgdc.gov/metadata/events/iso-geospatial-metadata-implementation-forum/2015/OpenGeoMetadataPresentation) by Kim Durante and Jack Reed*
