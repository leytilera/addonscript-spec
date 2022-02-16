# Relation Object

```json
{
  "id": "namespace:othermod",
  "version": "[1.0]",
  "repositories": ["repo1"],
  "flags": [],
  "conditions": {}
}
```

## Required properties

### id

This is the ID or namespaced ID of the addon this relation refers to.

## Optional properties

### version

This is a [maven version range](../concepts/versioning.md#dependancy-version-requirement-specification) that specifies, which versions
of the related addon are targeted by this relation. You can either set this property or `semver`, but exactly one of them has to be set.

### semver

This is a [semver version range](https://github.com/semver/semver/pull/584) of supported versions of this relation.
It will only allow versions of the related addon, which have a valid semver version number, which is in this range.

### repositories

This is an array of [repository](repository.md) IDs. These are the repositories, from which AddonScript should try to get this relation from,
in the order as they are specified in the array. If this property is not set or the array is empty, AddonScript will try to resolve the relation by
the namespace from all defined repositories.

### flags

This is an array of [flags](../concepts/flags.md) for this relation. If this property is not present in a relation object, the relation will use the default flags.

### conditions

This is a [conditions object](conditions.md). It can only be used, if the [optional flag](../concepts/flags.md) was set.
