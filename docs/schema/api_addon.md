# API Addon Object

```json
{
    "id": "myaddon",
    "namespace": "com.example",
    "meta": {
        "addon": {},
        "additional": {}
    },
    "versions": [
        "1.0"
    ]
}
```

## Required properties

### id

This is the ID of the addon.

It should be written in the `kebab-case` format, meaning lowercase only and using `-` instead of spaces.

### namespace

This is the [canonical namespace](../concepts/namespaces.md#canonical-namespaces) of the addon.

### versions

This is an array of all [version numbers](../concepts/versioning.md) of this addon, which are
available on this API instance.

## Optional properties

### meta 

This is a [meta object](meta.md) containing metadata about the addon. It does not
contain any version specific metadata.