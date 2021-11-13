# Flags

## Side flags

These are flags, which specify, for which side a [version](schema/version.md), a [file](schema/file.md) or
a [relation](schema/relation.md) was made.

- `client` This flag specifies, that the version, relation or file can be installed on the client side
- `server` This flag specifies, that the version, relation or file can be installed on the server side

## Version flags

These are flags, which can be set for [versions](schema/version.md).

- `instance` This flag specifies, that this is a version of an instance addon. Instance addons represent instances of
  Minecraft itself, while non-instance addons have to be installed into an existing instance of Minecraft.

## Relational flags

These are flags, which describe the relation between the addon and [related addons](schema/relation.md)
or [files](schema/file.md).

- `required` This flag specifies, that the related addon or file is required for the addon. If the addon gets installed,
  than any relation or file, which has this flag set, also has to be installed.
- `optional` This flag specifies, that the related addon or file is optional for this addon. If the addon gets installed,
  the user should be able to choose, whether he wants to install the relation or file with this flag, or not. This flag
  can be used in combination with the [conditions](schema/conditions.md) property.

### Relation specific

These are relational flags, which can only be used for [relations](schema/relation.md).

- `included` This flag specifies, that the related addon is included in this one. This also means, that if some
  addon requires the related addon, it can also be installed with this addon instead.
- `incompatible` This flag specifies, that the related addon is incompatible to this one. This means, that they can't
  be installed together in the same instance.
- `launch` This flag specifies, that the related addon should take care of the Minecraft launch process. It can only
  be used, if both this and the related addon are instance addons.
