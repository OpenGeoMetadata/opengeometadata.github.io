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

## About
OpenGeoMetadata is a federated metadata-sharing community. The goal of participating in OpenGeoMetadata is to enable other institutions to find and use your institution’s metadata in their own local repositories, increasing the visibility and discoverability of your geospatial assets.

## How OpenGeoMetadata works
Each collaborating institution creates and maintains its own geospatial metadata repository within the [OpenGeoMetadata GitHub organization](https://github.com/opengeometadata). This ensures that each institution has a unique namespace and can manage its own internal users who can collaborate on their metadata, while still enabling machine-harvestable metadata under a common organization. It also means that each institution is responsible for enforcing its own metadata standards.

## Metadata standards
Many different metadata standards and schemas can be shared in OpenGeoMetadata. A common approach is to share JSON files in a lightweight metadata schema (documented on this site) that was designed especially for the discovery platform [GeoBlacklight](https://github.com/geoblacklight). These files can be ingested into any GeoBlacklight instance, and the harvesting process can be done manually or with the help of [GeoCombine](https://github.com/OpenGeoMetadata/GeoCombine), a Ruby-based toolkit designed to automate the harvesting process.

Institutions may prefer to use other geospatial metadata standards in addition to – or instead of – the GeoBlacklight schema, such as ISO 19115 or the FGDC Content Standard for Digital Geospatial Metadata. Traditional library catalogs may use general purpose standards, such as MARC or MODS. Any institution is welcome to maintain an OpenGeoMetadata repository even if they do not use GeoBlacklight.

## History
The initiative was launched in 2015 as a collaboration between MIT, Princeton, and Stanford, and it has grown to include over 20 contributing organizations. It is a sister initiative to [GeoBlacklight](https://geoblacklight.org), an open-source Ruby on Rails software application for discovering geospatial content, and supports that work by providing a space to share GeoBlacklight-compliant metadata.

## Contribute to developing OpenGeoMetadata
Do you have an idea or question about how OpenGeoMetadata is working? Contribute your comments, proposals, and questions here: [OpenGeoMetadata/metadatarepository](https://github.com/OpenGeoMetadata/metadatarepository/issues).
