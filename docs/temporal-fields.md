# Temporal Fields

Aardvark has four fields in the "temporal" group. Having multiple temporal fields allows for flexibility in describing the date of a resource, allowing users to easily find records by way of text search, facet filtering, and time slider widgets (an optional customization in the GeoBlacklight software). In some cases, the same value might be used for more than one field.

| Field | Field Name | Obligation |
|:------|:-----------|:-----------|
| [Temporal Coverage](../ogm-aardvark/#temporal-coverage) | `dct_temporal_sm` | Suggested |
| [Date Issued](../ogm-aardvark/#date-issued)             | `dct_issued_s` | Optional |
| [Index Year](../ogm-aardvark/#index-year)               | `gbl_indexYear_im` | Suggested |
| [Date Range](../ogm-aardvark/#date-range)               | `gbl_dateRange_drsim` | Optional |


## Temporal Coverage
This is a descriptive, free-text field that is intended to describe the time period or time range of the resource. Its multi-valued setting allows for flexibility in describing the date of the resource: multiple strings can be used to indicate the time range the resource depicts, when the data was collected, and/or when the resource was created. It is the ideal field to use for indicating uncertainty.

```
["1985"]
```
```
["1985-1995", "Late 20th century"]
```

## Date Issued
This is an optional field for describing the date of an item's publication. Although optional, this field is often useful when a clear temporal coverage value is not present. For example, a dataset with uncertain lineage may at least have a date of last update. Generally it should be structured as a single year: `YYYY`, but more precise dates can take the ISO format without the time value: `YYYY-MM-DD` or `YYYY-MM`.

```
"1999"
```
```
"1999-08-21"
```

## Index Year
This is a suggested field for describing the date depicted in a resource. It is the only integer field in the temporal group and is formatted as an array of multiple values. The default GeoBlacklight application uses this field in the "Year" facet, allowing users to filter search results by year. It is also used to power customizable time-slider widgets that rely on integers for dates.

```
[1985]
```
```
[1985,1986,1987]
```

## Date Range
This optional field is not yet supported by GeoBlacklight software, but its intent is to power time widgets that use a date range (an optional customization to the software). The field is formatted as a start date and end date in the Solr date range field convention.

```
["1985 TO 1987"]
```
