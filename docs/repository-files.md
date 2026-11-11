# Repository Files

Besides metadata records, an OpenGeoMetadata repository can contain a few files at its root that describe the repository itself. Harvesters skip these files when indexing records.

| File | Purpose |
|---|---|
| `withdrawn.json` | Lists records the repository has withdrawn, so harvesters can delete them. See below. |
| `layers.json` | Legacy. Maps record identifiers to their folders, for people browsing the repository. See [Share on OpenGeoMetadata](../share-on-ogm/#naming-by-metadata-standard). |

## withdrawn.json

A log of records that the repository has deliberately stopped publishing. Harvesters read it and delete the listed records from their indexes. For when and how to use it, see [Withdraw Records](../withdraw-records).

[:material-code-json: JSON schema](schema/ogm-withdrawals-1.0.json){ .md-button }

```json
{
  "$schema": "https://opengeometadata.org/schema/ogm-withdrawals-1.0.json",
  "ogm_version": "1.0",
  "withdrawn": [
    {
      "id": "stanford-bb058zh0946",
      "date": "2026-03-14",
      "reason": "superseded",
      "note": "Replaced by the 2026 parcel release.",
      "is_replaced_by": ["stanford-cc123dd4567"]
    },
    {
      "id": "stanford-qp039xv4451",
      "date": "2026-03-14",
      "reason": "upstream-removed"
    }
  ]
}
```

The file is a JSON object with these properties:

| Property | Obligation | Description |
|---|---|---|
| `$schema` | Optional | `https://opengeometadata.org/schema/ogm-withdrawals-1.0.json` |
| `ogm_version` | Required | `"1.0"` |
| `withdrawn` | Required | An array with one entry per withdrawn record. Each entry has the fields below. |

The rules harvesters follow:

* **A record that is still published is never deleted.** If an `id` is listed in `withdrawn.json` and also appears in a record in any harvested repository, the record stays and the harvester warns. A mistaken entry is therefore harmless.
* **Each `id` counts once.** If an `id` is listed more than once, the last entry's date, reason, note, and replacements apply. The order of entries never changes whether records are withdrawn.
* **Unknown properties are ignored**, both on the file and on entries.
* **Entries are permanent.** Harvesters read the whole log on every run, and one that hasn't run in a while learns about a withdrawal only if the entry is still there. Remove an entry only when you publish the record again.

### Fields

{{ read_csv('ogm-repository/withdrawn-json.csv') }}

### ID
{{ read_csv('ogm-repository/id.csv') }}

### Date
{{ read_csv('ogm-repository/date.csv') }}

### Reason
{{ read_csv('ogm-repository/reason.csv') }}

#### Reason values
{{ read_csv('ogm-repository/reason-values.csv') }}

### Note
{{ read_csv('ogm-repository/note.csv') }}

### Is Replaced By
{{ read_csv('ogm-repository/is-replaced-by.csv') }}
