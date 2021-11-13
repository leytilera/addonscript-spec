# File Object

```json
{
  "id": "modfile",
  "url": "https://example.com/mymod.jar",
  "flags": [],
  "install": [],
  "sha1": "somesha1checksum",
  "conditions": {}
}
```

## Required properties

### id

This is the ID of the file.
It should be written in the `kebab-case` format, meaning lowercase only and using `-` instead of spaces.

<!--TODO: error if there are multiple relations with the same id and allow multiple urls-->

If multiple file objects in the same array have the same ID, they are treated as the same file,
which means that the first one of them in the array will be used unless it can't be retrieved from the URL,
in which case the next one will be used as a fallback.

### url

This is a [URL](../url.md), which points to the actual file.

### install

This is an array of [install objects](install.md). They describe how the file should be installed to the game.
The order in the array corresponds to the order in which the installation steps should be applied.

## Optional properties

### flags

This is an array of [flags](../flags.md) for this file. If this property is not present in a file object, the file will use the default flags.

### sha1

This is the sha1 checksum of the file. Although the checksum is optional, it is recommended.

### conditions

This is a [conditions object](conditions.md). It can only be used, if the [optional flag](../flags.md) was set.
