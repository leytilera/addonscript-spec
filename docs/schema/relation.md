# Relation Object

```json
{
  "id": "namespace:othermod",
  "version": "1.0",
  "repositories": ["repo1"],
  "flags": [],
  "conditions": {}
}
```

## Required properties

### id

This is the ID or namespaced ID of the addon this relation refers to.

### version

<!--TODO: update link one PR is merged-->

This is a [semver version range](https://github.com/semver/semver/pull/584) of supported versions of this relation.

## Optional properties

### repositories

This is an array of [repository](repository.md) IDs. These are the repositories, from which AddonScript should try to get this relation from,
in the order as they are specified in the array. If this property is not set or the array is empty, AddonScript will try to resolve the relation by
the namespace from all defined repositories.

### flags

This is an array of [flags](../flags.md) for this relation. If this property is not present in a relation object, the relation will use the default flags.

### conditions

This is a [conditions object](conditions.md). It can only be used, if the [optional flag](../flags.md) was set.
