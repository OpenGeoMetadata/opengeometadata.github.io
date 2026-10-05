# **OpenGeoMetadata API Specification**

**Version:** 0.1.0   **Status:** *DRAFT*   **Release Date:** 2025‑07‑08

## **Editors**

* Eric Larson, Big Ten Academic Alliance  
* Karen Majewicz, Big Ten Academic Alliance  
* THIS COULD BE YOU — Please help us with a significant review this spec, and earn a place on this list

## **Contributors**

* THIS COULD BE YOU — Please help us with a general review this spec, and earn a place on this list

Copyright © 2025 Editors and Contributors. Published by OpenGeoMetadata.org under the [CC-BY license](https://creativecommons.org/licenses/by/4.0/), see disclaimer.

---

## **TODOs**

* SEE: [DRAFT OpenGeoMetadata API Pull Request](https://github.com/OpenGeoMetadata/opengeometadata.github.io/pull/114)  
  * OpenGeoMetadata Website  
    * API documentation  
    * JSON-LD profiles  
* Advanced Search  
  * Field level searching  
* Sanity check MCP section

---

## **1\. Introduction**

The **OpenGeoMetadata (OGM) API** is a read‑only web service for programmatically accessing, searching, and retrieving metadata records that conform to the OpenGeoMetadata Aardvark schema ([opengeometadata.org](http://opengeometadata.org)). The API is designed to integrate with applications such as GeoBlacklight and to provide the search and discovery backend infrastructure for geospatial discovery platforms. 

In addition to structured metadata retrieval, the API can drive user interface components — such as field hints, thumbnails, citations, and viewer configurations — that support search, web service previews, and other interactive features within geospatial discovery applications.

This specification deliberately echoes the style and structure of the IIIF specifications ([iiif.io](https://iiif.io/api/image/3.0/?utm_source=chatgpt.com)), providing:

* A small, RESTful surface area with predictable, cache‑friendly URLs  
* Explicit parameter semantics  
* Normative requirements using **MUST**, **SHOULD**, **MAY** as defined by [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119)

The goal of this specification is to enable consistent client and server implementations across the OGM community.

### **1.1 Scope**

* **In scope** – Retrieval of individual records, list endpoints, full‑text and spatial search, simple authentication, usage limits.  
* **Out of scope** – Write operations (create/update/delete), bulk harvesting, or authentication flows beyond API keys (e.g. OAuth 2).

### **1.2 Audience**

* Metadata service providers wishing to expose OGM Aardvark metadata objects  
* Client developers (e.g., GeoBlacklight, FastAPI-based geoportals, desktop GIS plugins)  
* Researchers automating metadata discovery

---

## **2\. Terminology & Conventions**

### **2.1 Terminology**

* **Item** – An individual OpenGeoMetadata Aardvark JSON object, document, or record.  
* **Service Document** – The JSON description of server capabilities (`/v1/service`).  
* **Identifier** – The canonical URI‑safe string that uniquely identifies a record.  
* **Model Context Protocol (MCP)** – A protocol that enables API responses to declare behavioral context using `profile` URIs. These profiles point to machine-readable documents describing how to interpret or interact with the resource, especially useful for generic agents, AI tools, or validators.

### **2.2 Conventions**

* All date/time values **MUST** be RFC 3339 (ISO 8601\) strings.  
* All numeric coordinates **MUST** be WGS‑84 (EPSG 4326\) decimal degrees.

---

## **3\. OGM Aardvark Data Model**

### **3.1 OGM Aardvark JSON**

[OGM Aardvark](https://opengeometadata.org/ogm-aardvark/) ([https://opengeometadata.org/ogm-aardvark](https://opengeometadata.org/ogm-aardvark)) is a lightweight metadata profile for geospatial discovery. Every item is a single JSON object that **MUST** include the following required properties:

| Field | Type | Description |
| :---- | :---- | :---- |
| `id` | string | Stable identifier (slug or UUID). |
| `dct_title_s` | string | Human‑readable title. |
| `gbl_resourceClass_sm` | array of strings | Provides a top level set of categories for classifying the item. |
| `dct_accessRights_s` | string | Only one of two values are allowed: Public or Restricted. |
| `gbl_mdVersion_s` | string | MUST be `Aardvark`. |
| `gbl_mdModified_dt` | string (date‑time) | Last modified timestamp. |
| [Full OGM Aardvark Schema Definition](https://opengeometadata.org/ogm-aardvark/) |  |  |

The obligation for all other fields defined in the canonical Aardvark schema is **MAY**.

#### **3.1.1 JSON Schema**

JSON Schema file for OGM Aardvark records is maintained at [https://opengeometadata.org/schema/geoblacklight-schema-aardvark.json](https://opengeometadata.org/schema/geoblacklight-schema-aardvark.json).

#### **3.1.2 JSON-LD Context**

**TODO: Initial implementation within WIP PR on OGM website:**

JSON-LD context for OGM Aardvark records: [DRAFT PR](https://raw.githubusercontent.com/OpenGeoMetadata/opengeometadata.github.io/18896025536dae80b632aa5b059fb001d3d42c56/docs/context/aardvark.json)

### **3.2 OGM Aardvark CSV**

OGM Aardvark also has a tabular CSV expression with an [Open Knowledge Foundation](https://okfn.org/en/) \> [Frictionless Data](https://frictionlessdata.io/) \> [Table Schema](https://datapackage.org/standard/table-schema/) schema definition. Unlike OGM Aardvark JSON, OGM Aardvark CSV is comprised of two files:

1. Primary — The primary Aardvark metadata elements (primary.csv)  
2. Distributions — The dct\_reference\_s elements (distributions.csv)

#### **3.2.1 Table Schema**

##### **3.2.1.1 CSV File Examples**

These example CSV files use the GeoBlacklight fixture set.

* Primary — [gbl\_fixtures\_primary.csv](https://github.com/OpenGeoMetadata/opengeometadata.github.io/blob/api/docs/schema/gbl_fixtures_primary.csv)  
* Distributions — [gbl\_fixtures\_distributions.csv](https://github.com/OpenGeoMetadata/opengeometadata.github.io/blob/api/docs/schema/gbl_fixtures_distributions.csv)

##### **3.2.1.2 Table Schema Files**

These files can be used to validate the CSV examples against our CSV schema.

* Primary — [ogm\_aardvark\_primary.schema.json](https://github.com/OpenGeoMetadata/opengeometadata.github.io/blob/api/docs/schema/ogm_aardvark_primary.schema.json)  
* Distributions — [ogm\_aardvark\_distributions.schema.json](https://github.com/OpenGeoMetadata/opengeometadata.github.io/blob/api/docs/schema/ogm_aardvark_distributions.schema.json)

---

## **4\. Protocol & Versioning**

* Base URI: `https://opengeometadata.org/api/v1`  
* Content types:  
  * `application/json` (default)  
  * `application/ld+json` (when `Accept` header includes JSON‑LD)  
  * text/csv (when Accept header includes CSV)  
* HTTP 1.1 or HTTP/2 over TLS 1.2+ **MUST** be supported.  
* HTTP/3 **RECOMMENDED**  
* Minor revisions to this spec will increment the *patch* version (e.g., `1.0.1`) and **MUST NOT** introduce breaking changes.

---

## **5\. Authentication (API Keys)**

The API uses simple **apiKey** authentication. Clients **MUST** supply a valid key via one of:

HTTPS header (preferred):

*  X-API-Key: \<key\>  
* Query parameter (fallback): `?api_key=<key>`

Keys are provisioned out‑of‑band by the service operator. A new key **MUST** be a 32‑character URL‑safe random string.

### **5.1 Key Status Endpoint**

| Method | Path | Description |
| :---- | :---- | :---- |
| GET | `/keys/self` | Returns metadata about the calling key (plan, quota, issued at, expires at). |

---

## **6\. Rate Limiting Recommendations**

Servers **MUST** protect shared resources. The following sane defaults are **RECOMMENDED** and **MAY** be adjusted per deployment:

* **Burst:** 100 requests in any 10‑second window  
* **Sustained:** 1, 000 requests per minute  
* **Daily Cap:** 100,000 requests per 24 hours

Implementations on very small servers **MAY** reduce the burst limit to 50 requests per 10‑second window and the sustained limit to 500 requests per minute if monitoring indicates strain.

The server **SHOULD** convey limits using \[RFC 6585\] `429 Too Many Requests` and the headers:

RateLimit-Limit: 1000  
RateLimit-Remaining: 253  
RateLimit-Reset: 42

---

## **7\. Requests (Endpoints)**

JSON-LD context for search requests:

* Future: https://opengeometadata/api/search/1.0/context/request.json  
* Draft PR: [Online here](https://raw.githubusercontent.com/OpenGeoMetadata/opengeometadata.github.io/18896025536dae80b632aa5b059fb001d3d42c56/docs/api/search/1.0/context/request.json)

### **7.1 Service Document**

| Method | Path | Description |
| :---- | :---- | :---- |
| GET | `/service` | Returns API metadata, conformance, contact, and example URLs. |

Example response (abridged):

| {  "@context": "https://opengeometadata.org/ns/service-context.jsonld",  "id": "https://ogm.example.org/api/v1/service",  "type": "Service",  "label": "OGM API Service Document",  "endpoints": {    "item": "/items/{id}",    "search": "/search{?q,page,per\_page,sort,callback}",    "suggestions": "/suggestions{?q}",    "validate": "/validate"  }} |
| :---- |

**TODO** — Should the service endpoint document local schema modifications in a “fields” attribute?

### **7.2 Item Retrieval**

| Method | Path | Notes |
| :---- | :---- | :---- |
| GET | `/items/{id}` | Returns a single Aardvark record. Supports `fields` param for field projection. |

**Parameters**

| Name | Type | Req? | Description |
| :---- | :---- | :---- | :---- |
| `id` | string | ✔️ | Canonical record ID |
| `fields` | string (CSV) |  | Subset of fields to include |
| `pretty` | boolean |  | Pretty‑print JSON (debug only) |

### **7.3 Search**

Supports both GET (simple) and POST (complex) forms.

#### **7.3.1 GET `/search`**

| Parameter | Type | Description |
| :---- | :---- | :---- |
| `q` | string | Full‑text query (default `*:*`). |
| `page` | integer | Current page of results |
| `per_page` | integer | Number of results to return |
| `sort` | string | Sort option (relevance, year\_desc, year\_asc, title\_asc, title\_desc) |
| `callback` | string | JSONP callback name |
| `include_ui` | boolean | Include UI (default true) |
| `fields` | string (CSV) | List of fields to return |
| `facets` | string (CSV) | List of facets to return |
| `filters` | object | Active facet filters |
| `format` | string | Format option (JSON, CSV) |

Example request:

GET /api/v1/search?q=soil+survey\&per\_page=20

#### **7.3.2 POST `/search`**

Accepts a JSON body with the same parameters plus structured filters.

| {  "q": "land cover",  "filters": {    "dct\_provenance\_s": \["Minnesota"\],    "gbl\_resourceClass\_sm": \["Datasets"\]  },  "page": 1,  "per\_page": 50,  "sort": "year\_desc"} |
| :---- |

### **7.4 Geospatial Search**

Support for geospatial queries:

* Bounding Box  
* Distance-Radius  
* Polygon  
* Shape \+ Relation

#### **7.4.1 Bounding Box (bbox)**

GET /search?q=land+cover\\  
\&filters\[geo\]\[type\]=bbox\\  
\&filters\[geo\]\[field\]=location\\  
\&filters\[geo\]\[top\_left\]\[lat\]=45.1\\  
\&filters\[geo\]\[top\_left\]\[lon\]=-94.0\\  
\&filters\[geo\]\[bottom\_right\]\[lat\]=44.7\\  
\&filters\[geo\]\[bottom\_right\]\[lon\]=-92.9\\  
\&limit=50\\  
\&sort=dct\_temporal\_sm%20desc

POST (`application/json`)

| {  "q": "land cover",  "filters": {    "geo": {      "type": "bbox",      "field": "location",      "top\_left":     { "lat": 45.1, "lon": \-94.0 },      "bottom\_right": { "lat": 44.7, "lon": \-92.9 }    }  },  "limit": 50,  "sort": "dct\_temporal\_sm desc"} |
| :---- |

#### **7.4.2 Distance-Radius (`distance`)**

GET /search?q=land+cover\\  
\&filters\[geo\]\[type\]=distance\\  
\&filters\[geo\]\[field\]=location\\  
\&filters\[geo\]\[center\]\[lat\]=44.98\\  
\&filters\[geo\]\[center\]\[lon\]=-93.27\\  
\&filters\[geo\]\[distance\]=25km\\  
\&limit=50

POST

| {  "q": "land cover",  "filters": {    "geo": {      "type": "distance",      "field": "location",      "center":   { "lat": 44.98, "lon": \-93.27 },      "distance": "25km"    }  },  "limit": 50} |
| :---- |

#### **7.4.3 Polygon (`polygon`)**

GET /search?q=land+cover\\  
\&filters\[geo\]\[type\]=polygon\\  
\&filters\[geo\]\[field\]=location\\  
\&filters\[geo\]\[points\]\[0\]\[lat\]=44.9\\  
\&filters\[geo\]\[points\]\[0\]\[lon\]=-93.4\\  
\&filters\[geo\]\[points\]\[1\]\[lat\]=45.2\\  
\&filters\[geo\]\[points\]\[1\]\[lon\]=-93.2\\  
\&filters\[geo\]\[points\]\[2\]\[lat\]=45.0\\  
\&filters\[geo\]\[points\]\[2\]\[lon\]=-92.8

(Add more `points[n]` pairs for polygons with \>3 vertices.)

POST

| {  "q": "land cover",  "filters": {    "geo": {      "type": "polygon",      "field": "location",      "points": \[        { "lat": 44.9, "lon": \-93.4 },        { "lat": 45.2, "lon": \-93.2 },        { "lat": 45.0, "lon": \-92.8 }      \]    }  }} |
| :---- |

#### **7.4.4. Shape (`shape` \+ relation)**

Relation options:

* intersects  
* disjoint  
* within  
* contains

GET /search?q=land+cover\\  
\&filters\[geo\]\[type\]=shape\\  
\&filters\[geo\]\[field\]=location\\  
\&filters\[geo\]\[relation\]=within\\  
\&filters\[geo\]\[shape\]\[type\]=envelope\\  
\&filters\[geo\]\[shape\]\[coordinates\]\[0\]\[0\]=-94\\  
\&filters\[geo\]\[shape\]\[coordinates\]\[0\]\[1\]=46\\  
\&filters\[geo\]\[shape\]\[coordinates\]\[1\]\[0\]=-92\\  
\&filters\[geo\]\[shape\]\[coordinates\]\[1\]\[1\]=44

(Here the shape is a GeoJSON-style envelope; any GeoJSON geometry works.)

POST

| {  "q": "land cover",  "filters": {    "geo": {      "type": "shape",      "field": "location",      "relation": "within",      "shape": {        "type": "envelope",        "coordinates": \[\[\-94, 46\], \[\-92, 44\]\]      }    }  }} |
| :---- |

### **7.5 Suggestions Endpoint**

Endpoint for autocomplete search suggestions.

#### **7.5.1 GET /suggestions?q=minn**

| Parameter | Type | Description |
| :---- | :---- | :---- |
| `q` | string | Full‑text query (default `*:*`). |
| `callback` | string | JSONP callback name |

### **7.6 Validation Endpoint**

**TODO** — How can this validate CSVs via Table Schema

This endpoint allows clients to POST a single metadata record (as a JSON object) and receive a validation report indicating whether it conforms to the OpenGeoMetadata Aardvark schema.

| Method | Path | Description |
| :---- | ----- | ----- |
| POST | /validate | Validate a single Aardvark JSON record |

#### **7.6.1 Request Body**

| {  "data": {    "type": "item",    "attributes": {      "id": "stanford-abc123",      "dct\_title\_s": "Sample Map",      "gbl\_resourceClass\_sm": \["Maps"\],      "dct\_accessRights\_s": "Public",      "gbl\_mdVersion\_s": "Aardvark",      "gbl\_mdModified\_dt": "2025-07-20T18:43:00Z"      // ... other fields ...    }  }} |
| :---- |

* The body MUST be a single JSON object using type: "item" and an attributes map.  
* The record MUST be structured according to the Aardvark profile defined at: [https://opengeometadata.org/schema/geoblacklight-schema-aardvark.json](https://opengeometadata.org/schema/geoblacklight-schema-aardvark.json)

#### **7.6.2 Response**

If the record is valid:

| {  "valid": true,  "errors": \[\],  "warnings": \[\],  "profile": \[    "https://opengeometadata.org/profile/aardvark",    "https://opengeometadata.org/profile/mcp/validate"  \] |
| :---- |

}

If the record is invalid:

| {  "valid": false,  "errors": \[    {      "field": "dct\_title\_s",      "message": "This field is required and must be a string."    },    {      "field": "gbl\_mdVersion\_s",      "message": "Value must be 'Aardvark'."    }  \],  "warnings": \[\],  "profile": \[    "https://opengeometadata.org/profile/aardvark",    "https://opengeometadata.org/profile/mcp/validate"  \]} |
| :---- |

#### **7.6.3 Notes**

* This endpoint is non-mutating — it does not store or alter the record.  
* It is useful for QA tools, CI pipelines, and metadata editors.  
* The server SHOULD use a strict JSON Schema validator and MAY support additional lint rules or MCP profiles.

---

## **8\. Responses**

JSON-LD context for search responses:

* Future: https://opengeometadata/api/search/1.0/context/response.json  
* Draft PR: [Online here](https://raw.githubusercontent.com/OpenGeoMetadata/opengeometadata.github.io/18896025536dae80b632aa5b059fb001d3d42c56/docs/api/search/1.0/context/response.json)

### **8.1 API Standards**

* [OpenAPI / Version v3.1.1](https://spec.openapis.org/oas/v3.1.1.html)  
* [JSON API / Version v1.1](https://jsonapi.org/format/1.1/)  
* [JSON-LD / Version v1.1](https://www.w3.org/TR/json-ld11/)  
* [Model Context Protocol (MCP) / Version 1.0](https://modelcontextprotocol.io/specification/2025-06-18)

### **8.2 Item Response**

GET /api/v1/items/91663ad7f1444494900f7e1cf063bfe5

| {  "jsonapi": {    "version": "1.1",    "profile": \[      "https://opengeometadata.org/profile/aardvark",      "https://opengeometadata.org/profile/ui-hints",      "https://opengeometadata.org/profile/mcp/search"    \]  },  "links": {    "self": "https://api.example.org/v1/items/91663ad7f1444494..."  },  "data": {    "type": "item",    "id":   "91663ad7f1444494900f7e1cf063bfe5",    "attributes": {      "dct\_title\_s":          "Land Cover \[Global\]",      "dct\_alternative\_sm":   \["Land Cover"\],      "dct\_description\_sm":   \["Global land cover type ..."\],      "dct\_language\_sm":      \["eng"\],      "schema\_provider\_s":    "University of Minnesota",      "gbl\_resourceClass\_sm": \["Web services"\],      "dcat\_theme\_sm":        \["Land cover"\],      "dcat\_keyword\_sm":      \["Land Cover","Agriculture","Global",...\],      "dct\_issued\_s":         "2016-11-22",      "gbl\_dateRange\_drsim":  \["\[\* TO \*\]"\],      "locn\_geometry": {        "type": "Polygon",        "coordinates": \[\[\[179,\-75\],\[\-179,\-75\],\[\-179,85\],\[179,85\],\[179,\-75\]\]\]      },      "dcat\_bbox": {        "type": "Polygon",        "coordinates": \[\[\[179,\-75\],\[\-179,\-75\],\[\-179,85\],\[179,85\],\[179,\-75\]\]\]      },      "dct\_accessRights\_s":   "Public",      "gbl\_fileSize\_bytes":   81168384    },    "meta": {      "@context": "https://static.opengeometadata.org/contexts/aardvark-1.0.jsonld",      "@type":    "AardvarkRecord",      "geometry": {        "locn\_geometry":   "ENVELOPE(179,-179,85,-75)",        "dcat\_bbox":       "ENVELOPE(179,-179,85,-75)",        "dcat\_centroid":   "5.0,0.0"      },      "human\_readable": { "file\_size": "77.4 MB" },      "ui": {        "viewer": {          "protocol":  "arcgis\_feature\_layer",          "endpoint":  "https://services.arcgis.com/8df8p0NlLFEShl0r/arcgis/rest/services/Land\_Cover/FeatureServer/0",          "geometry":  { "type": "Polygon", "coordinates": \[\[\[179,\-75\],\[\-179,\-75\],\[\-179,85\],\[179,85\],\[179,\-75\]\]\] }        },        "citation": "U-Spatial. (2016-11-22). Land Cover \[Global\].",         "relationships": {          "member\_of": {            "links": { "related":     ".../item/b0153110-e455-4ced-9114-9b13250a7093" },            "data": \[               { "type": "item",                  "id": "b0153110-e455-4ced-9114-9b13250a7093"}\]         }        }      }    }  }} |
| :---- |

#### **8.2.1 META block**

The META block MAY contain these potential user interface component entries (see 8.5):

| Feature | Key(s) | Description | Example Value(s) |
| :---- | :---- | :---- | :---- |
| Citation | citation | Generic citation format. String. | {"citation": "\[Creator not found\], (1932). A food map of the United States. https://quod.lib.umich.edu/c/clark1ic/x-003289100/39015091916158 (pictorial map)."} |
| Downloads | downloads | Convenience presentation of dct\_references\_s’ downloads. Array of objects. | {"downloads": \[{"label": "Download Shapefile", "url": "https://stacks.stanford.edu/object/cf162mm8787"}\]} |
| Metadata | metadata | Convenience presentation of dct\_references\_s’ metadata entries. Array of objects. | {"metadata": \[{"label": "ISO 19139", "url": "https://web.s3.wisc.edu/rml-gisdata/metadata/Bayfield\_Trails\_2020.xml"}\]} |
| Relationships | relationships | Convenience presentation of OGM Aardvark relationship fields. Nested Objects. | {"relationships": { "member\_of": { "links": { "related":     ".../item/b0153110-e455-4ced-9114-9b13250a7093" }, "data": \[{ "type": "item", "id": "b0153110-e455-4ced-9114-9b13250a7093"}\]}} |
| Viewer | viewer: protocol endpoint geometry | The viewer key contains all the necessary values to display an npm \`@geoblacklight-frontend\` package-driven item viewer. Object. | {"viewer": {"protocol": "iiif\_manifest", "endpoint": "https://quod.lib.umich.edu/cgi/i/image/api/search/clark1ic:003289100","geometry": { "type":"Polygon", "coordinates": \[\[\[\-124.98,49.31\],\[\-67.18,49.31\],\[\-67.18,22.61\],\[\-124.98,22.61\],\[\-124.98,49.31\]\]\] }}} |
| Thumbnail | thumbnail: url alt\_text | Thumbnail object, including URL and Alt Text entries. Object. | {"thumbnail": { "url":  "https://quod.lib.umich.edu/cgi/i/image/api/image/clark1ic:003289100:39015091916158/full/400,/0/default.jpg", "alt-text": "A food map of the United States"}} |

### **8.3 Autosuggestion Response**

GET /api/v1/suggest?q=minn

| {  "jsonapi": {    "version": "1.1",    "profile": \[      "https://opengeometadata.org/profile/aardvark",      "https://opengeometadata.org/profile/ui-hints",      "https://opengeometadata.org/profile/mcp/search"    \]  },  "links": {    "self": "https://api.example.org/v1/suggest?q=minn\&size=5"  },  "meta": {    "query":          "minn",    "took\_ms":        191,    "fuzzy":          true,    "size":           5,    "@context": "https://static.opengeometadata.org/contexts/aardvark-1.0.jsonld",    /\* \--- optional diagnostics, gated by \`debug=true\` \--- \*/    "debug": {      "es\_query":   { /\* redacted for brevity \*/ },      "es\_profile": { /\* only if ?profile=true \*/ }    }  },  "data": \[    {      "type": "suggestion",      "id":   "p16022coll245:1056",      "attributes": {        "label": "(Minneapolis, Minn.?)",        "title": "University of Minnesota : plan of main campus"      },      "meta": { "score": 3 }    },    {      "type": "suggestion",      "id":   "international-boundary-collection",      "attributes": {        "label": "Mina de Oro St",        "title": "International Boundary collection"      },      "meta": { "score": 3 }    }    /\* ...three more suggestion objects ... \*/  \]} |
| :---- |

### **8.4 Search Results Response**

GET /api/v1/search?q=land+cover

| {  "jsonapi": {    "version": "1.1",    "profile": \[      "https://opengeometadata.org/profile/aardvark",      "https://opengeometadata.org/profile/ui-hints",      "https://opengeometadata.org/profile/mcp/search"    \]  },  "links": {    "self":  "https://api.example.org/v1/search?q=land+cover\&page\[number\]=1\&page\[size\]=10",    "first": "https://api.example.org/v1/search?q=land+cover\&page\[number\]=1\&page\[size\]=10",    "prev":  null,    "next":  "https://api.example.org/v1/search?q=land+cover\&page\[number\]=2\&page\[size\]=10",    "last":  "https://api.example.org/v1/search?q=land+cover\&page\[number\]=155\&page\[size\]=10"  },  "meta": {    "query\_time\_ms": {      "search":      958,      "processing":    2185,      "thumbnaill":  2178,      "citation":   0,      "viewer":     6,      "total":              3143    },    "pagination": {      "current": 1,      "next":    2,      "prev":    null,      "total":  155,      "per\_page":     10,      "offset":       0,      "total\_count":  1547    },    "spelling\_suggestions": \[\]  },  "data": \[    {      "type": "document",      "id":   "gm833zf4048",      "attributes": {        "dct\_title\_s":           "Urban Land Cover, Teheran, Iran, 1990",        "dct\_language\_sm":       \["eng"\],        "schema\_provider\_s":     "Stanford",        "gbl\_resourceClass\_sm":  \["Datasets"\],        "dcat\_theme\_sm":         \["Land Cover","Society","Imagery"\],        "dct\_issued\_s":          "2012",        "locn\_geometry":         "ENVELOPE(50.6773354,52.08805,36.2348092,34.8881922)",        "dcat\_bbox":             "ENVELOPE(50.6773354,52.08805,36.2348092,34.8881922)",        "dct\_accessRights\_s":    "Public",        "gbl\_mdmodified\_dt":     "2016-11-17T00:00:00",        "gbl\_mdversion\_s":       "Aardvark"      },      "meta": {        "score": 29.54668,        "ui": {          "viewer": {            "protocol":  "oembed",            "endpoint":  "https://purl.stanford.edu/embed.json?hide\_title=true\&url=https%3A%2F%2Fpurl.stanford.edu%2Fgm833zf4048",            "geometry": {              "type":        "Polygon",              "coordinates": \[\[\[50.6773354,36.2348092\],\[50.6773354,34.8881922\],                               \[52.08805,34.8881922\],\[52.08805,36.2348092\],                               \[50.6773354,36.2348092\]\]\]            }          },          "thumbnail\_url": "https://geowebservices.stanford.edu/geoserver/wms/reflect?FORMAT=image/png\&TRANSPARENT=TRUE\&WIDTH=200\&HEIGHT=200\&LAYERS=druid:gm833zf4048",          "citation":      "Angel, Shlomo ... (2012). Urban Land Cover, Teheran, Iran, 1990\. Lincoln Institute of Land Policy. https://purl.stanford.edu/gm833zf4048 (raster data)",	"ui\_downloads": \[        {          "label": "Download Shapefile",          "url": \[            {              "url": "https://stacks.stanford.edu/object/mf519gg2738",              "label": "Zipped object"            }          \],          "type": "shapefile"        }      \],        },        "@context": "https://static.opengeometadata.org/contexts/aardvark-1.0.jsonld",        "@type":    "AardvarkRecord"      }    }  \],  "included": \[    {      "type": "facet",      "id":   "spatial\_agg",      "attributes": {        "label":   "Spatial",        "buckets": \[          { "label": "Earth (Planet)", "value": "Earth (Planet)", "hits": 1033 },          { "label": "California",     "value": "California",     "hits":   38 }        \]      }    },    {      "type": "facet",      "id":   "resource\_class\_agg",      "attributes": {        "label":   "Resource Class",        "buckets": \[          { "label": "Datasets", "value": "Datasets", "hits": 1513 },          { "label": "Maps",     "value": "Maps",     "hits":   26 }        \]      }    }  \]} |
| :---- |

### **8.5 UI Component Support**

A list of the frontend feature components this OGM API can support. 

See the BTAA proof of concept React UI for an example implementation:  
[https://github.com/geobtaa/rui](https://github.com/geobtaa/rui)

#### **8.5.1 Search**

* Autocomplete  
* Search  
* Map Search  
* Results  
* Result Thumbnails  
* Facets  
* Pagination  
* Per Page  
* Sorting  
* Spelling Suggestions  
* Constraints

#### **8.5.2 Item View**

* Viewer  
* Context  
  * Breadcrumb  
  * Sidebar Map  
  * More Like This  
* Metadata Text  
* Metadata Links  
* Citation  
* Downloads  
* Relationships

---

## **9\. Parameter Reference**

**TODO** — This is currently inchoate.

| Name | Type | Default | Description |
| :---- | :---- | :---- | :---- |
| `q` | string | `*:*` | Lucene/Solr‑style search string. |
| `page` | integer | 1 |  |
| `per_page` | integer (1‑100) | 10 | Page size. |
| `sort` | string | — | \` \<asc desc\>`; multiple separated by` ,\`. |
| `fields` | string (CSV) | — | Response field projection. |
| `facets` | string (CSV) | — | Fields to facet and count distinct values. |
| `filters` | object | — | Active facet filters |
| `pretty` | boolean | false | Human‑readable JSON. SHOULD NOT be used in production. |
| `include_ui` | boolean | true | Include Meta UI section |
| `include_geom` | boolean | true | Include Meta GEOM section |
| `callback` | string | — | JSONP callback name |
| `format` | string | JSON | Format options (JSON, CSV) |

---

## **10\. Model Context Protocol (MCP)**

TODO — Explore FastAPI’s MCP add-on for conformity

The OpenGeoMetadata API supports the [Model Context Protocol (MCP)](https://modelcontextprotocol.io/specification/2025-06-18), a formal specification for declaring the processing and behavioral context of an API response. MCP enables generic clients, validators, and AI agents to understand how to interpret metadata records and response payloads in a consistent, machine-readable way.

### **10.1 Usage**

API responses MAY declare one or more MCP \`profile\` URIs to advertise behavior:

| {"jsonapi": {  "version": "1.1",  "profile": \[    "https://opengeometadata.org/profile/aardvark",    "https://opengeometadata.org/profile/ui-hints",    "https://opengeometadata.org/profile/mcp/search"  \]} |
| :---- |

### **10.2 Profile URIs**

Each URI in the profile array MUST resolve to a valid MCP document, which includes:

* @context: MUST include the MCP context (https://modelcontextprotocol.io/context/v1.jsonld)  
* @type: SHOULD be ModelContextProfile  
* title, description, appliesTo: for human/machine interpretation  
* features: optional keys describing supported behaviors, fields, or UI expectations

### **10.3 Example MCP Profile (abridged)**

| {  "@context": "https://modelcontextprotocol.io/context/v1.jsonld",  "@type": "ModelContextProfile",  "id": "https://opengeometadata.org/profile/mcp/search",  "title": "OGM Search Results Profile",  "description": "Describes the structure and interpretation of search results.",  "appliesTo": "https://opengeometadata.org/api/v1/search",  "features": {    "search": {      "supportsGeoFilters": true,      "maxResults": 1000,      "defaultSort": "relevance"    },    "ui": {      "viewer": true,      "facets": true,      "pagination": true    }  }} |
| :---- |

### **10.4 Benefits**

* Allows automated agents to reason about what’s returned  
* Enables consistent UI rendering and schema interpretation  
* Provides potential future extensibility without API versioning


---

## **11\. Error Handling**

Errors **MUST** return a JSON object with `type`, `title`, `status`, and `detail` properties.

| {  "type": "https://opengeometadata.org/api/errors/RateLimitExceeded",  "title": "Rate limit exceeded",  "status": 429,  "detail": "Allowed 1000 requests per minute; received 1423."} |
| :---- |

| HTTP Status | Meaning |
| :---- | :---- |
| 400 | Bad request / parameter validation error |
| 401 | Missing or invalid API key |
| 404 | Record or endpoint not found |
| 429 | Rate limit exceeded |
| 500 | Internal server error |

---

## **12\. Security Considerations**

* All traffic **MUST** use HTTPS.

* API keys **MUST** be treated as secrets; rotate compromised keys immediately.

* Servers **SHOULD** implement audit logging and anomaly detection.

---

## **13\. Change Log**

| Version | Date | Notes |
| :---- | :---- | :---- |
| 0.1.0 | 2025‑07‑22 | Initial draft. |

---

## **14\. Implementation Notes**

* A reference implementation in FastAPI is available at [https://github.com/geobtaa/ogm-api](https://github.com/geobtaa/ogm-api).

* Example code snippets are provided in the repository README.

* JSON‑LD clients may apply the [OGM Aardvark context](https://opengeometadata/context/aardvark-v1.jsonld) ([https://opengeometadata/context/aardvark-v1.jsonld](https://opengeometadata/context/aardvark-v1.jsonld)) to treat field names as compact IRIs.

---

## **15\. Acknowledgements**

This specification borrows heavily from the structure and editorial approach of the IIIF community ([iiif.io](https://iiif.io/api/image/3.0/?utm_source=chatgpt.com)) and benefits from prior work by the GeoBlacklight and OpenGeoMetadata communities.

