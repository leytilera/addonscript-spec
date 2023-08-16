# Instance addons

Instance addons represent instances of Minecraft itself, while non-instance addons 
have to be installed into an existing instance of Minecraft. An instance addon MAY have
launch patches for each side by applying launch patches of other instance addons using 
the `patch` [flag](flags.md) or by patching the [Minecraft](./minecraft.md)
launch configuration directly using a [launch patch object](../schema/patch.md).
Moreover they MAY override the main jar file using the `launch` [flag](flags.md)
or inherit the launch configuration, including main jar overrides and patches,
from another instance addon using the the `launch` [flag](flags.md).
The `launch` [flag](flags.md) is recursive which means, that an instance addon MAY 
inherit it's launch configuration from another addon, which 
itself inherits it. Instance addons MAY modify inherited launch configurations using a 
[launch patch object](../schema/patch.md) or override the main jar file. Inheriting a 
launch configuration with the `launch` [flag](flags.md) also includes any
modifications to it.

## Launch configurations

Instance launch configurations are always based on a 
[Minecraft launch config](./minecraft.md#launch-configuration) and MAY have patches
applied to it. Patches are done by [launch patch objects](../schema/patch.md), which
can override the main class and include additional arguments. Moreover instance addons MAY also
add libraries to the classpath using the `library` [install action](./install.md#library).
When launching a Minecraft instance, AddonScript implementations SHOULD take the Minecraft
launch configuration as specified [here](./minecraft.md#launch-configuration) of the version,
on which the instance is based on, and then apply all patches of instance addons in the instance
to it. Patches are applied in the order [specified below](#patch-apply-order). Patches, which 
are applied later, MAY override settings from earlier patches.

### Patch apply order

Patches are applied in the following order:

1. Patches inherited from the another instance addon using the `launch` [flag](flags.md). The
   patches of that instance addon are applied according to the same order rules
2. Patches inherited from the another instance addon using the `patch` [flag](flags.md) in the order,
   in which the addons are specified in the [relations array](../schema/manifest.md#relations)
3. Patches done directly by the instance addon using the 
   [client_patches](../schema/manifest.md#clientpatches) and [server_patches](../schema/manifest.md#serverpatches)
   properties.

## Main file

Instance addons MAY have a main jar file for each side. The main file MAY be specified for a side
using the `launch` [flag](flags.md) or MAY be inherited from another instance addon or from
[Minecraft](./minecraft.md) itself using the `launch` [flag](flags.md). If it is neither specified
nor inherited, the instance doesn't have a main jar file.