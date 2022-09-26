# Instance addons

Instance addons represent instances of Minecraft itself, while non-instance addons 
have to be installed into an existing instance of Minecraft. An instance addon MUST have
a launch configuration for each side for which it is available. This means, that an instance
addon MUST have exactly one [file](../schema/file.md) or [relation](../schema/relation.md)
for each side, which has the `launch` [flag](flags.md) flag. A file MUST NOT have this flag 
on both sides, since the file type is different for each side, while a relation MAY have
it on both sides, as long as the related addon is itself an instance addon for both sides.

## Instance addons as relations

If an instance addon is a relation of another instance addon, each side of that
relation MUST have at least one of the [flags](flags.md) `included`, `launch`, `env`
or `incompatible`. Non-instance addons MAY have instance addons as relations without
this restrictions.