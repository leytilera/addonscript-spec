# File Object

```json
{
  "qualifier": "modfile",
  "link": ["https://example.com/mymod.jar", "./mymod.jar"],
  "flags": {},
  "install": [],
  "hashes": {
    "sha1": "somesha1checksum"
  }
}
```

## Required properties

### qualifier

This is the qualifier of this file.
It MUST only contains lowercase alphanumeric characters and hyphens and SHOULD be written in the `kebab-case` format.
The qualifier has to be unique to this addon version. The namespace, addon ID, version and qualifier
can together be used to uniquely identify a file.

### link

This is an array of [links](../concepts/links.md), which are pointing to the actual file. All of these links must
have the same file type. Since AddonScript treats directories and zip files equally, 
they can be mixed in the same link array. When downloading the file,
the first link in this array SHOULD be used with the other links as fallback, if the first doesn't work.
If none of the specified links works or the array is empty, the file link SHOULD be retrieved by it's identifier
from one of the [repositories](repository.md), but only, if a `sha1` hash is specified, so that it can be
verified, that the downloaded file is correct. 

## Optional properties

### install

This is an array of [install objects](install.md). They describe how the file will be installed to the game.
The order in the array corresponds to the order in which the installation steps will be applied.

### flags

This is an [flags object](flags.md) which contains [relational flags](../concepts/flags.md#relational-flags) for both sides for this file.
If a file has no flag for a side, the file will be ignored for that side.

### hashes

This is an object with checksums for this file. The object contains key-value-pairs where the key is the hash algorithm and the
value is the checksum. 

Supported hash algorithms:
- `sha1`

