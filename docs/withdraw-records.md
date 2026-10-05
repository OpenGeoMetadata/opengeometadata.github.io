# Withdraw Records

To have harvesters remove a record, list it in a `withdrawn.json` file at the root of your repository. This page explains when to do that and how. For the field-by-field reference, see [Repository Files](../repository-files).

## Is withdrawal what you want?

OpenGeoMetadata has three similar ways to signal a record's status, but they mean different things:

| State | How you signal it | What a harvester does |
|---|---|---|
| Suppressed | [Suppressed](../ogm-aardvark/#suppressed) (`gbl_suppressed_b`) set to `true` on the record | Hides it from search results, but keeps its page working |
| Superseded | [Is Replaced By](../ogm-aardvark/#is-replaced-by) (`dct_isReplacedBy_sm`) on the record, with a [Display Note](../ogm-aardvark/#display-note) | Indexes it normally, but shows a link to the newer record |
| Withdrawn | Delete the record from GitHub and list it in `withdrawn.json` | Deletes it from the search index and removes its web page |

To choose:

1. **Are you keeping the record published?** If it has been replaced by a newer version but people may still cite it, it is *superseded*. Leave it in your repository and add Is Replaced By.
2. **Should it stay reachable but out of search results?** This sometimes suits pages of an atlas or parts of a series. The record is *suppressed*. Set `gbl_suppressed_b` to `true`.
3. **Should it disappear from other institutions' catalogs?** The record is *withdrawn*. Read on.

## Withdraw a record by hand

This works for any repository, including ones you edit in the GitHub web interface. No scripts are needed.

1. Delete the record's metadata file(s) from your repository.
2. In the root of the repository, open `withdrawn.json`. If it doesn't exist yet, create it with this content:

	```json
	{
	  "$schema": "https://opengeometadata.org/schema/ogm-withdrawals-1.0.json",
	  "ogm_version": "1.0",
	  "withdrawn": []
	}
	```

3. Add an entry for the record to the `withdrawn` list. Use the record's `id` exactly as it appeared in the record, and today's date:

	```json
	{
	  "$schema": "https://opengeometadata.org/schema/ogm-withdrawals-1.0.json",
	  "ogm_version": "1.0",
	  "withdrawn": [
	    { "id": "princeton-rv042w38t", "date": "2026-03-14", "reason": "quality" }
	  ]
	}
	```

4. Commit both changes together.

You can add a [reason](../repository-files/#reason), a [note](../repository-files/#note), and the [records that replace it](../repository-files/#is-replaced-by). Only `id` and `date` are required.

!!! tip

	Check that the file is valid JSON before you commit, for example by pasting it into a JSON validator. A missing comma makes harvesters skip the whole file. You can also validate it against the [JSON schema](schema/ogm-withdrawals-1.0.json).

## Withdraw records automatically

If a script generates your repository from another system, have it write `withdrawn.json` in the same run that removes the records:

1. Work out which records your source system no longer publishes.
2. Delete their files.
3. Append one entry per removed record to `withdrawn.json`, and keep the entries already there.
4. Commit everything together, so the withdrawals arrive as one reviewable change.

For example, in Ruby:

```ruby
require 'json'
require 'date'

log = JSON.parse(File.read('withdrawn.json', encoding: 'utf-8'))
removed_ids.each do |id|
  log['withdrawn'] << { 'id' => id, 'date' => Date.today.iso8601, 'reason' => 'upstream-removed' }
end
File.write('withdrawn.json', JSON.pretty_generate(log) + "\n")
```

!!! danger "Guard against a bad source"

	If the request that lists your source system's records fails and comes back empty or partial, a script like this will "withdraw" your entire repository. Harvesters can't catch this, because the records really are gone from your repository. Before deleting anything, stop if the number of records your source returned is zero or has dropped sharply since the last run.

## Things to know

### Deleting a file is not a withdrawal

Harvesters never treat a missing file as a withdrawal. Files disappear for many innocent reasons, like migrating to a new schema or reorganizing folders. Only an entry in `withdrawn.json` asks for a delete.

### A published record always wins

If a record is listed in `withdrawn.json` but still exists in your repository or any other harvested repository, harvesters keep it and warn. A typo can't delete someone else's record. It also means a record isn't withdrawn until you actually remove its file.

### Keep entries permanently

Harvesters read the whole file on every run, and one that hasn't run in months only learns about a withdrawal if the entry is still there. Remove an entry only if you go back to publishing that record again.

### Withdrawal is not erasure

Your repository's git history still contains the record, and so may the copies other institutions harvested. If a record must be erased for legal reasons, contact the repository owners directly. `withdrawn.json` is public, so don't put personal information, legal detail, or the identity of whoever requested the withdrawal in a note.

### What withdrawal doesn't cover

* **Records removed before you adopted `withdrawn.json`.** Harvesters only delete what the file lists. You can add entries for records you removed in the past.
* **Records changed to Restricted, or moved to a different schema version.** Many harvesters skip records like these from then on, but they don't delete the copy they indexed earlier.
* **Repositories that are archived or leave OpenGeoMetadata.** Harvesters stop updating their copies but don't delete them. Institutions that harvested those records need to remove them by hand.
