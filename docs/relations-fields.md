# Relations Fields

Fields in the "relations" group are used to describe how records relate to each other. All these fields are designed to store the [ID(s)](https://opengeometadata.org/ogm-aardvark/#id) of related records. More than one record can be listed within each relationship type.

Starting in GeoBlacklight version 4.0, these fields are used to populate relationship widgets in the application sidebar, allowing users to easily explore related records and understand how they are connected. The relationship widgets are customizable in the `geoblacklight.en.yml` and `settings.yml` files.


| Field | Field Name | Obligation |
|:------|:-----------|:-----------|
| [Relation](../ogm-aardvark/#relation) | `dct_relation_sm` | Optional |
| [Member Of](../ogm-aardvark/#member-of)| `pcdm_memberOf_sm` | Optional |
| [Is Part Of](../ogm-aardvark/#is-part-of) | `dct_isPartOf_sm` | Optional |
| [Source](../ogm-aardvark/#source) | `dct_source_sm` | Optional |
| [Is Version Of](../ogm-aardvark/#is-version-of) | `dct_isVersionOf_sm` | Optional |
| [Replaces](../ogm-aardvark/#replaces) | `dct_replaces_sm` | Optional |
| [Is Replaced By](../ogm-aardvark/#is-replaced-by) | `dct_isReplacedBy_sm` | Optional |

## Relation
Use this field to link to records that are related in a general or non-specific way. IDs entered in this field will populate a "Related Records" widget on the item's show page, as well as on the related record's show page. Nothing needs to be entered in the related record's metadata.

```
"dct_relation_sm": ["nyu_2451_34636"]
```

**Item's show page**

![related records widget - source](images/rel-related-record-source.png)

**Related record's show page**

![related records widget - link](images/rel-related-record-link.png)

## Member Of

!!! tip

	To link items in a book or atlas, use "Is Part Of" instead.

This field links an item to its collection(s). The first step is to create a separate collection record and assign it a unique ID. Then, enter the collection record's ID in the *member item's* metadata.

IDs entered in this field in the *member item's* metadata will populate a "Belongs to collection..." widget on the member item's show page and a "Collection records..." widget on the collection's show page. Nothing needs to be entered in the collection record's metadata.

```
"pcdm_memberOf_sm": ["umass-macconnell-1951"]
```

**Member item's show page**

![belongs to collection widget](images/rel-belongs-collection.png)

**Collection's show page**

![collection records widget](images/rel-collection-records.png)

## Is Part Of

!!! tip

	To link items in a collection, use "Member Of" instead.

This field is similar to "Member Of" but is intended to link to items that are a subset of another item, like a book or atlas. The first step is to create a separate parent record and assign it a unique ID. Then, enter the parent record's ID in the *member item's* metadata.

IDs entered in this field in the *member item's* metadata will populate a "Is part of..." widget on the member item's show page and a "Has part..." widget on the parent's show page. Nothing needs to be entered in the parent record's metadata.

```
"dct_isPartOf_sm": ["88cc9b19-3294-4da9-9edd-775c81fb1c59"]
```

**Member item's show page**

![is part of widget](images/rel-is-part-of.png)

**Parent's show page**

![has part widget](images/rel-has-part.png)
