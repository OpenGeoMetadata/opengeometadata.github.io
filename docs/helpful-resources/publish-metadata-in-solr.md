---
layout: default
title: How to Publish Metadata in Solr
parent: Helpful Resources
nav_order: 3
---

# How to Publish Metadata in Solr
{: .no_toc }

subtitle
{: .fs-6 .fw-300 }

---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Publishing Metadata in Solr

Metadata for GeoBlacklight instances is stored and indexed in Solr.

### Adding Metadata Records to Solr
{: .no_toc }

The Solr application identifies each metadata record as a “document.” The process of adding documents to Solr is called “indexing.” If you have access to your Solr Dashboard panel, you can add records manually by pasting them into the Documents pane. However, it is more practical to use a process for batch adding, updating, and deleting the records. Most of the available processes are in the form of command-line scripts. See the Tools and Resources page for examples.
