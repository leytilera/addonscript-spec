# File installing

## Install actions

### move

args:

- `[location]`

`move` moves the file to the given location.

### extract

args:

- `[location]`

`extract` can be used with zip files, to extract the contents of the zip file
to the given location.

### rename

args:

- `[new name]`

`rename` renames the file to the new given filename.

### inject

`inject` can be used with zip or jar files, to inject the contents of that file
into the server launch jar on server side or into the client jar on client side.
In contrast to libraries, `inject` will not add just that file to the classpath, but
will also overwrite classes, which are already contained in the game jar, if they
are also in injected file. 

## Locations

Locations are specified as a relative path from the Minecraft directory to which the file will be installed.
For example `./mods` would point to the mods directory of the Minecraft instance.

## Directories

If the file is a directory, then it is treated like a zip file, which means, that you can move and
rename it like a normal file, but also use the `extract` install action to move all contents of the directory
to the specified location.
