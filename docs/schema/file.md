# File Object

``` json
{
  "id": "modfile",
  "url": "https://example.com/mymod.jar",
  "flags": [],
  "install": [
    "move mods"
  ],
  "sha1": "somesha1checksum"
}
```

## Required properties

### id

This is the ID of the file. It should only contain **lowercase letters, numbers and dashes**.

If multiple file objects in the same array have the same ID, they are treated as the same file,
which means that the first one of them in the array will be used unless it can't be retrieved from the URL,
in which case the next one will be used as a fallback.

### url

This is an [URL](../url.md), which points to the actual file. 

### install

This is an array of [install steps](../install.md). They describe how the file should be installed to the game.
The order in the array corresponds to the order in which the install steps should be applied.

## Optional properties

### flags

This is an array of [flags](../flags.md) for this file. If this property is not present in a file object, the file
will have the flags which are set as default for files, or if no default was set, it will inherit the flags from the
associated version, which are applicable for files.

### sha1

This is the sha1 checksum of the file. Although the checksum is optional, it is recommended to use it.
