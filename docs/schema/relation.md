# Relation Object

```json
{
  "id": "namespace:othermod",
  "version": "[1.0,)",
  "flags": []
}
```

## Required properties

### id

This is the ID or namespaced ID of the addon this relation refers to. 

### version

This is a [maven version range](https://maven.apache.org/enforcer/enforcer-rules/versionRanges.html) of supported versions of this relation.

## Optional properties

### flags

This is an array of [flags](../flags.md) for this relation. If this property is not present in a relation object, the relation
will have the flags which are set as default for relations or, if no default was set, it will inherit the flags
which are applicable for relations from the associated version.
