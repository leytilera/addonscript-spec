# Addon Object

``` json
{
  "addonscript": {},
  "id": "myaddon",
  "namespace": "com.example",
  "version": "1.0",
  "files": [],
  "relations": [],
  "flags": ["server", "client"],
  "repositories": [],
  "meta": {}
}
```

## Required properties

### addonscript

This is an [AddonScript object](addonscript.md) containing information about the version of AddonScript used in this file.

### id

This is the ID of the addon. It should only contain **lowercase letters, numbers and dashes**.

### version

This is the version number of this version. It must follow [semver version naming conventions](https://semver.org/spec/v2.0.0.html), 
as they are used to compare versions.

## Optional properties

### namespace

This is the namespace of the addon. 

### files

This is an array of [file objects](file.md) including the files belonging to this version.

### relations

This is an array of [relation objects](relation.md) which represents related addons.

### flags

This is an array of [flags](../flags.md) for this version.
 
### repositories

This is an array of [repository objects](repository.md). Each repository object defines one repository from which files or
addons can be retrieved.

### meta

This is a [meta object](meta.md).
