# Addon Manifest Object

```json
{
  "addonscript": {},
  "id": "myaddon",
  "namespace": "com.example",
  "version": "1.0.0",
  "files": [],
  "relations": [],
  "flags": {},
  "repositories": [],
  "meta": {}
}
```

## Required properties

### addonscript

This is an [AddonScript object](addonscript.md) containing information about the version of AddonScript used in this file.

### id

This is the ID of the addon.

It MUST only contains lowercase alphanumeric characters and hyphens and SHOULD be written in the `kebab-case` format.

### version

This is the [AddonScript version number](../concepts/versioning.md#addonscript-version-numbers) of this version.

### namespace

This is the [canonical namespace](../concepts/namespaces.md#canonical-namespaces) of the addon.

### flags

This is an [flags object](flags.md) which contains [manifest flags](../concepts/flags.md#manifest-flags) for both sides for this manifest.

## Optional properties

### files

This is an array of [file objects](file.md) including the files belonging to this addon.

### relations

This is an array of [relation objects](relation.md) which represent addons in relation to this one.

### repositories

This is an array of [repository objects](repository.md). Each repository object defines one repository from which files or
addons can be retrieved. Each AddonScript manifest SHOULD have a repository for the [canonical namespace](#namespace) of 
that manifest, from which AddonScript implementations MAY check for updates for this addon. If this addon has the `env`
[manifest flag](../concepts/flags.md#manifest-flags), it MUST have such a repository to provide API instances, which can
be used to request the [launch environment](../api/features/env.md#build-launch-environment).

### meta

This is a [meta object](meta.md) containing metadata about the addon.
