# API File Object

```json
{
    "link": ["https://example.com/file.jar"],
    "hashes": {
        "sha1": "somesha1checksum"
    },
    "meta": {
        "additional": {}
    }
}
```

## Required properties

### link

This is an array of [links](../concepts/links.md), which are pointing to the actual file. This must be a http(s) link.
All of these links must have the same file type.

## Optional properties

### hashes

This is an object with checksums for this file. The object contains key-value-pairs where the key is the hash algorithm and the
value is the checksum. 

Supported hash algorithms:
- `sha1`

### meta

This is a [meta object](meta.md) containing metadata about the file. it may only contain [additional metadata](meta.md#additional).