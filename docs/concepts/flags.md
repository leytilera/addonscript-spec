# Flags

Flags are side-specific information about a [manifest](../schema/manifest.md), [file](../schema/file.md) or
[relation](../schema/relation.md). There are two types of flags: [manifest flags](#manifest-flags) and
[relational flags](#relational-flags). [Manifest flags](#manifest-flags) provide information about an
addon manifest, including for which side it is available and for which side it is an [instance addon](instance.md).
[Relational flags](#relational-flags) provide information about how a file or relation is related to the addon.

## Manifest flags

- `required` This flag specifies, that the addon of the manifest is required on the side which has this flag set,
  meaning, that if the other side has this addon installed, this side also required this addon to be compatible.
  If the other side has the `incompatible` flag set, this flags behaves exactly like the `optional` flag, but 
  `required` is the prefered flag in this case.
- `optional` This flag specifies, that the addon of the manifest is optional on the side which has the flag set,
  meaning, that this addon is not required on this side to be compatible, even if the other side has this addon installed.
- `incompatible` This flag specifies, that the manifest is not compatible with the side which has this flag set.
  If a side has this flag, this side will completly be ignored for the manifest.
- `instance` This flag specifies, that this is a manifest of an [instance addon](instance.md).

## Relational flags

- `required` This flag specifies, that the related addon or file is required for the addon. If the addon gets installed,
  than any relation or file, which has this flag set, also has to be installed.
- `optional` This flag specifies, that the related addon or file is optional for this addon. If the addon gets installed,
  the user should be able to choose, whether he wants to install the relation or file with this flag, or not.
- `included` This flag is only valid for relations. It specifies, that the related addon is included in this one. 
  This also means, that if some addon requires the related addon, it can also be installed with this addon instead. 
  Relations with this flag must have an exact version specified, a version range, which includes multiple versions 
  is not allowed. If this flag is used together with `required` or `optional`, the files of the related addon will 
  be installed like if the relation wouldn't have this flag, relations of the related addon will however be ignored 
  since AddonScript assumes, that they are already covered by this addon.
- `incompatible` This flag specifies for a relation, that the related addon is incompatible to this one, which means, 
  that they can't be installed together in the same instance. For a file this flag specifies, that the file can't be 
  installed on the side which has this flag set.
- `launch` This flag is only valid for instance addons. For a relation this flag specifies, that the launch configuration
  should be delegated to the related addon. The related addon must also be an instance addon on that side. For a file this 
  flag specifies, that the file should be the launch file of this addon. On the client side the launch file must be a 
  [client JSON file](https://minecraft.fandom.com/wiki/Client.json) which contains the client launch configuration.
  On the server side the launch file must be an executable jar file, which should be executed to start the server.
  This jar file will implicitly be installed by being moved to the root of the server directory. This flag always
  also implies any effect of `required`.