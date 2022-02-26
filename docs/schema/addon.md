# Addon Object

```json
{
  "addonscript": {},
  "id": "myaddon",
  "namespace": "com.example",
  "version": "1.0",
  "semver": "1.0.0",
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

This is the ID of the addon.

It should be written in the `kebab-case` format, meaning lowercase only and using `-` instead of spaces.

### version

This is the [version number](../concepts/versioning.md) of this version. Versions are compared by 
[Maven version order rules](../concepts/versioning.md#version-order-specification).
If this version number is valid semver, the `semver` property is implicitly equal to `version` if `semver` was not explicitly set.

## Optional properties

### semver

This is the version number of this version in semver format. It must follow the [semver versioning specifications](https://semver.org/spec/v2.0.0.html).

### namespace

This is the [namespace](../concepts/namespaces.md) of the addon, which should be in a reversed domain name format. 
Used to identify addons across repositories.

### files

This is an array of [file objects](file.md) including the files belonging to this addon.

### relations

This is an array of [relation objects](relation.md) which represent addons in relation to this one.

### flags

This is an array of [flags](../concepts/flags.md) for this version.

### repositories

This is an array of [repository objects](repository.md). Each repository object defines one repository from which files or
addons can be retrieved.

### meta

This is a [meta object](meta.md) containing metadata about the addon.
