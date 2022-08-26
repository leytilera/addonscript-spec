# File installing

## Install commands

### move

args:

- `[location]`

`move` is simplest install step of all. It just moves the selected file to
the given location.

### extract

args:

- `[location]`

`extract` can be used with zip files, to extract the contents of the zip file
to the given location.

### rename

args:

- `[new name]`

`rename` renames the selected file to the new given filename.

### inject

`inject` can be used with zip or jar files, to inject the contents of that file
into the server launch jar on server side or into the client jar on client side.
In contrast to libraries, `inject` will not add that file to the classpath, but
will also overwrite classes, which are already contained in the game jar, if they
are also in injected file. 

### launch

`launch` can be used to mark the selected file as the launch file for a specific side. Files having this
install step can only have the `client` or the `server` flag, not both. If the file is client-sided, it
has to be a [client JSON file](https://minecraft.fandom.com/wiki/Client.json) as specified by Minecraft
itself. If it is server-sided, it has to be a jar file, which is the file, that should be launched to start
the server. The jar file has to be moved to the root of the instance directory, before using `launch` on it.
Moreover, this install step may only be used with launchable or instance addons and there may be only one file for each
side, which has this install step, except all of them are marked as `optional`, in which case they are also
implicitly marked as incompatible to each other.

## Locations

Locations are specified as a relative path from the Minecraft directory to which the file should be installed.
For example `./mods` would point to the mods directory of the Minecraft instance.

## Directories

If the selected file is a directory, then it is treated like a zip file, which means, that you can move and
rename it like a normal file, but also use the `extract` install step to move all contents of the directory
to the specified location.
