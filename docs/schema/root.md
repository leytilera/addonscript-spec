# Addon Object

``` json
{
    "addonscript": {},
    "id": "myaddon",
    "versions": [],
    "repositories": [],
    "index": {},
    "flags": {},
    "meta": {}
}
```

## Required properties

### addonscript

This is an [AddonScript object](addonscript.md) containing information about the version of AddonScript used in this file.

### id

This is the ID of your addon. It should only contain lowercase letters, numbers and dashes.

## Optional properties

### versions

This is an array of [version objects](version.md). It is possible to define multiple versions of the addon in one AddonScript file,
but in the most cases, there should be just one version per file. Although this property is optional, as you can define versions
in the [index](index.md), it can be used to define a list of versions, which can be found in the index.
 
### repositories

This is an array of [repository objects](repository.md). Each repository object defines one repository, from which files or
addons can be retrieved.

### index

This is an [index object](index.md), which includes links to other versions of this addon or to other related addons.

### flags

Not yet specified

### meta

This is a [meta object](meta.md).
