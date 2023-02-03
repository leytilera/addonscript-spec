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
- `env` This flag is only valid for [instance addons](instance.md). It specifies, that the 
  [environment builder API](../api/features/env.md) will be used to get the launch files for this addon.
  An addon with this flag MUST have a [repository](../schema/repository.md) for it's 
  [canonical namespace](../schema/manifest.md#namespace).

## Relational flags

- `required` This flag specifies, that the related addon or file is required for the addon. If the addon gets installed,
  than any relation or file, which has this flag set, also has to be installed.
- `optional` This flag specifies, that the related addon or file is optional for this addon. If the addon gets installed,
  the user SHOULD be able to choose, whether he wants to install the relation or file with this flag, or not.
- `included` This flag is only valid for relations. It specifies, that the related addon is included in this one. 
  This also means, that if some addon requires the related addon, it can also be installed with this addon instead. 
  Relations with this flag MUST have an exact version specified, a version range, which includes multiple versions 
  is not allowed. If this flag is used together with `required` or `optional`, the files of the related addon will 
  be installed like if the relation wouldn't have this flag, relations of the related addon will however be ignored 
  since AddonScript assumes, that they are already covered by this addon.
- `incompatible` This flag specifies for a relation, that the related addon is incompatible to this one, which means, 
  that they can't be installed together in the same instance. For a file this flag specifies, that the file can't be 
  installed on the side which has this flag set.
- `launch` This flag is only valid for relations of [instance addons](instance.md). It specifies, that the 
  [launch configuration](../schema/launch.md) should be inherited from the related addon (which MUST als be an
  instance addon or [Minecraft](./minecraft.md) itself). The inherited launch configuration, MAY still be modified
  using the [launch object](../schema/launch.md) of this addon. This flag always also implies any effect of `required`.
- `env` This flag is only valid for relations of [instance addons](instance.md). It MUST only be used for instance
  addons, that either have the `env` [manifest flag](#manifest-flags) or are delegating the launch configuration
  to such an addon. This flag speficies, that the related addon will be [requested](../schema/api_env_request.md#requested)
  to be part of the [launch environment](../api/features/env.md#build-launch-environment). For the addon, for
  which the launch environment will be build, it is used together with the `required` or `optional` flag
  to specify, which addons are required for the launch environment, which are optional and which versions
  of them are valid. An addon, that is delegating the launch configuration to one, which has the `env` 
  [manifest flag](#manifest-flags), uses this flag to tell AddonScript, which version of the addons will be requested
  for the environment by setting an exact [version](../schema/relation.md#version) for the relation. It also tells
  AddonScript, which optional `env` addons will be part of the environment. If an addon with the `env`
  [manifest flag](#manifest-flags) gets manually installed, meaning not as a dependency, the user SHOULD be asked,
  which optional `env` addons and which version of each `env` addon will be requested.