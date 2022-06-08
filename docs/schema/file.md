# File Object

```json
{
  "id": "modfile",
  "link": ["https://example.com/mymod.jar", "./mymod.jar"],
  "flags": [],
  "maven": {},
  "install": [],
  "sha1": "somesha1checksum",
  "conditions": {}
}
```

## Required properties

### id

This is the ID of the file.
It should be written in the `kebab-case` format, meaning lowercase only and using `-` instead of spaces.
The file ID has to be unique to this addon version.

### link

This is an array of [links](../concepts/links.md), which are pointing to the actual file. All of these links must
have the same file type. Since AddonScript treats directories and zip files equally, 
they can be mixed in the same link array. When downloading the file,
the first link in this array should be used with the other links as fallback, if the first doesn't work.
If none of the specified links works, the file should be downloaded by it's Maven
specifier from one of the specified repository, but only, if a `sha1` hash is specified, so that it can be
verified, that the downloaded file is correct.

## Optional properties

### install

This is an array of [install objects](install.md). They describe how the file should be installed to the game.
The order in the array corresponds to the order in which the installation steps should be applied.

### flags

This is an array of [flags](../concepts/flags.md) for this file. If this property is not present in a file object, the file will 
inherit the [side flags](../concepts/flags.md#side-flags) from the [version](addon.md) and have the `required` flag set by default.

### sha1

This is the sha1 checksum of the file. Although the checksum is optional, it is strongly recommended.

### conditions

This is a [conditions object](conditions.md). It can only be used, if the [optional flag](../concepts/flags.md) was set.

### maven

```json
{
  "group": "com.example",
  "artifact": "mymod",
  "version": "1.0",
  "qualifier": ""
}
```

Each file has a unique Maven specifier, consisting of a group ID, an artifact ID, a version, a file type and an optional qualifier.
By default, the group ID is equal to the addon namespace, the artifact ID to the addon ID, the version to the addon version and
the qualifier to file ID. Those values can be overwritten in this object. If the qualifier is set to an empty string, it will be
removed from the Maven specifier. The file type is always equal to the file type of the `link`. If the group ID, addon ID and version
all have their default values and the qualifier is an emptry string, the file type may not be `json`.
