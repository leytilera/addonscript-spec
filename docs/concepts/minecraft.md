# Minecraft

Minecraft itself can be used as a [relation](../schema/relation.md) in AddonScript
[manifests](../schema/manifest.md). This way addons MAY define, with which versions
of Minecraft they are compatible. [Instance addons](./instance.md) MUST either
directly or indirectly inherit their launch configuration from Minecraft. This 
way it is also defined, on which version of Minecraft an instance is base on.
There is no AddonScript manifest for Minecraft, AddonScript implementations
MUST know the [ID and namespace](#id-and-namespace) of Minecraft and how to
handle it as specified below.

## ID and Namespace

The [addon ID](../schema/manifest.md#id) of Minecraft, which will be used for
[relations](../schema/relation.md) is `minecraft` and the 
[namespace](namespaces.md#canonical-namespaces) is `net.minecraft`.

## Versions

The AddonScript [version number](./versioning.md) of a Minecraft version
is equal to the version ID from the piston-meta API of Mojang and the 
official version manifests used by the Minecraft launcher, except for the 
difference that characters, which are invalid in AddonScript versioning
(whitespace and non-ASCII characters), will be replaced with an underscore (`_`).

### Release

Release versions of Minecraft are SemVer compatible. Addons, which only use
release versions as [relations](../schema/relation.md) SHOULD use SemVer
version ranges instead of Maven version ranges. Release versions are correctly 
ordered according to both, SemVer and Maven.

### Alpha and Beta

Alpha and beta versions are all Minecraft versions before the initial release 
`1.0`. They are not SemVer compatible. Most alpha and beta versions are
correctly ordered according to Maven, except for some early alpha versions.
AddonScript implementations SHOULD be careful when ordering alpha versions and
SHOULD rather trust the information from piston-meta than the Maven order.

### Snapshot

Snapshot versions are mostly neither SemVer compatible nor do they fit into
Maven version ordering. AddonScript implementations SHOULD use piston-meta
to order snapshot versions. When installing an addon into an instace, which is
based on a snapshot version, AddonScript implementations SHOULD NOT trust the
version range for Minecraft of that addon, as it might be incorrect due to
version ordering. Instead the user SHOULD be asked, if the installation should
be proceeded, and warned about possible incompatibilities.

## Launch configuration

AddonScript implementations, which are meant to install or launch AddonScript
instances MUST know the launch configuration for Minecraft itself.
For the server side, the launch configuration only consists of the server jar,
which already includes the required libraries and a manifest with the main class.
For the client side the launch configuration SHOULD be retrieved from the 
piston-meta API in form of the version manifest. This manifest includes information 
about the main file, the main class, all required libraries and launch arguments.
In contrast to launch config modifications done by [instance addons](./instance.md),
arguments in the version manifest can include variables, which MUST be replaced with
the correct values when launching the game and both, libraries and arguments, can
be operating system or architecture specific, which MUST also be considered by
implementations. Moreover they also provide an asset index, which SHOULD be used by
implementations to retrieve game assets (if they are not already cached).