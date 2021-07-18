# AddonScript

This repository contains the AddonScript specification.

## What is AddonScript?

AddonScript is a format to distribute Minecraft addons. An addon could be anything, which is installed 
into the Minecraft game, like a mod, modpack, modloader, texturepack or even a world.
AddonScript can be used for example to define how addons are installed, or to specify dependencies 
for addons. This way, addon creators just have to publish the AddonScript file for their addon and let
AddonScript compatible tools (for example launchers) install them.

## The values of AddonScript

### Open

AddonScript can be used by everyone. There is no company or economic interest behind AddonScript.
It is intended to be an open standard, which can be implemented by anyone who likes to. Anyone can
contribute ideas to the AddonScript specification.

### Independent

AddonScript depends on nothing, except Minecraft itself (and Java). This means that the specification
does not depend on existing APIs and formats like Curseforge. It also does not reference any specific
modloader like Forge or Fabric, instead they are themselves addons, which can be defined using AddonScript.
This means, that AddonScript is not bound to a specific set of modloaders, instead you can use any 
modloader.

### Universal

AddonScript is not bound to any specific use case like just for modpacks or just for mods. Instead it
is considered to be a universal format, which can handle anything, that is installed into
the Minecraft game. AddonScript can handle modloaders, mods, modpacks, texturepacks and even worlds
and maybe other things as well.
