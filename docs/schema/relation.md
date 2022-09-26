# Relation Object

```json
{
  "id": "othermod",
  "namespace": "com.example",
  "version": "[1.0]",
  "repositories": ["repo1"],
  "flags": {}
}
```

## Required properties

### id

This is the ID of the addon this relation refers to.

### version

This is an [AddonScript version range](../concepts/versioning.md#addonscript-version-ranges) that specifies, which versions
of the related addon are targeted by this relation.

## Optional properties

### namespace

This is the [canonical namespace](../concepts/namespaces.md#canonical-namespaces) of the related addon. If this property is not set,
AddonScript will resolve the namespace via the [addon endpoint](../api/features/addons.md#get-addon) of a [repository](#repositories).

### repositories

This is an array of [repository namespaces](repository.md#namespace). These are the repositories, from which AddonScript will try to get this relation from,
in the order as they are specified in the array. If this property is not set or the array is empty, AddonScript will try to resolve the relation from
the repository described by the [manifest namespace](manifest.md#namespace). The repository described the the [canonical namespace](#namespace) of this
relation has always precedence before these repositories.

### flags

This is an [flags object](flags.md) which contains [relational flags](../concepts/flags.md#relational-flags) for both sides for this relation.
If a relation has no flag for a side, the relation will be ignored for that side. This behavior is different from the `incompatible` flag,
since the related addon can still be installed on that side without any conflict.
