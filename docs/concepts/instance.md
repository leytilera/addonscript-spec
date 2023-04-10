# Instance addons

Instance addons represent instances of Minecraft itself, while non-instance addons 
have to be installed into an existing instance of Minecraft. An instance addon MUST have
a launch configuration for each side by inheriting the launch configuration of another
instance addon or [Minecraft](./minecraft.md) itself using the `launch` [flag](flags.md). 
Inheriting a launch configuration MAY be recursive which 
means, that an instance addon MAY inherit it's launch configuration from another addon, which 
itself inherits it. Instance addons MAY modify inherited launch configurations using a 
[launch config object](../schema/launch.md) by overriding the main file or main class, or by
adding libraries or launch arguments. Inheriting a launch configuration also includes any
modifications to it.

## Instance addons as relations

If an instance addon is a relation of another instance addon, each side of that
relation MUST have at least one of the [flags](flags.md) `included`, `launch`, `env`,
`expect` or `incompatible`. Non-instance addons MAY have instance addons as relations 
without this restriction.

## Launch configurations

Instance launch configurations are always based on a 
[Minecraft launch config](./minecraft.md#launch-configuration) and MAY have modifications
applied to it. Modifications are done by [launch config objects](../schema/launch.md) and
can override the main class or main file and include additional libraries and arugments.
When launching a Minecraft instance, AddonScript implementations SHOULD take the Minecraft
launch configuration as specified [here](./minecraft.md#launch-configuration) and then apply
all modifications by instance addons in the instance stack to it. When overriding the main class
or file, an instance addon has always priority over the instance addon, from which it inherits
the launch config. When adding arguments, they are always appended at the end of those
arguments from the inherited launch config.