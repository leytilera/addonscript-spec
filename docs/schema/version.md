# Version Object

```json
{
  "version": "1.0",
  "files": [],
  "relations": [],
  "flags": ["server", "client"],
  "meta": {}
}
```

## Required properties

### version

This is the version number of this version. It should follow [Maven version naming conventions](https://docs.oracle.com/middleware/1212/core/MAVEN/maven_version.htm), 
as they are used to comparing versions.

## Optional properties

### files

This is an array of [file objects](file.md), including the files, belonging to this version.

### relations

This is an array of [relation objects](relation.md), which represents related addons.

### flags

This is an array of [flags](../flags.md) for this version. If this property is not present in a version object, the version
will have the flags, which are set as default for versions.

### meta

This is a [meta object](meta.md).
