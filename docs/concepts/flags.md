# Flags

## Side flags

These are flags, which specify, for which side a [version](../schema/addon.md), a [file](../schema/file.md) or
a [relation](../schema/relation.md) was made. If a file has no side flags set, it will inherit them from the
[version object](../schema/addon.md), while a version is required to have side flags set.

- `client` This flag specifies, that the version, relation or file can be installed on the client side
- `server` This flag specifies, that the version, relation or file can be installed on the server side

## Version flags

These are flags, which can be set for [versions](../schema/addon.md).

- `instance` This flag specifies, that this is a version of an instance addon. Instance addons represent instances of
  Minecraft itself, while non-instance addons have to be installed into an existing instance of Minecraft.

## Relational flags

These are flags, which describe the relation between the addon and [related addons](../schema/relation.md)
or [files](../schema/file.md).

- `required` This flag specifies, that the related addon or file is required for the addon. If the addon gets installed,
  than any relation or file, which has this flag set, also has to be installed.
- `optional` This flag specifies, that the related addon or file is optional for this addon. If the addon gets installed,
  the user should be able to choose, whether he wants to install the relation or file with this flag, or not.

### Relation specific

These are relational flags, which can only be used for [relations](../schema/relation.md).

- `included` This flag specifies, that the related addon is included in this one. This also means, that if some
  addon requires the related addon, it can also be installed with this addon instead. Relations with this flag must
  have an exact version specified, a version range, which includes multiple versions is not allowed. If this flag
  is used together with `required` or `optional`, the files of the related addon will be installed like if the
  relation wouldn't have this flag, relations of the related addon will however be ignored since AddonScript assumes,
  that they are already covered by this addon.
- `incompatible` This flag specifies, that the related addon is incompatible to this one. This means, that they can't
  be installed together in the same instance.
- `launch` This flag specifies, that the related addon should take care of the Minecraft launch process. It can only
  be used, if both this and the related addon are instance addons.
