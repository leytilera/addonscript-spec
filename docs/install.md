# File installing

## Install steps

### move
`move [location]`

`move` is simplest install step of all. It just moves the selected file to 
the given location.

### extract
`extract [location]`

`extract` can be used with zip files, to extract the contents of the zip file
to the given location.

### rename
`rename [new name]`

`rename` renames the selected file to the new given filename.

### execute
`execute [location] [arguments]`

`execute` can be used with an executable jar file. The jar file will be executed with the given arguments and 
the given location as working directory. A client should inform the user before just executing the file and
ask them for permission to do so and/or it should execute the jar in a closed environment like a container
to prevent malicous code from running.

### launch
`launch`

`launch` can be used to mark the selected file as the launch file for a specific side. Files having this
install step can only have the `client` or the `server` flag, not both. If the file is client-sided, it
has to be a [client JSON file](https://minecraft.fandom.com/wiki/Client.json) as specified by Minecraft
itself. If it is server-sided. it has to be a jar file, which is the file, that should be launched to start
the server. The jar file has to be moved to the root of the instance directory, before using `launch` on it.
Moreover, this install step may only be used with instance addons and there may be only one file for each
side, which has this install step, except all of them are marked as `optional`, in which case they are also 
implicitly marked as incompatible.

### select
`select [filename]`

`select` is used to select the file with the given file name for other installation steps.
The file name can also be a relative path, if the file is not directly in the Minecraft directory.
If no file name is given, the selection resets to the original file itself, also if it was already moved to another location.

## Locations

Locations are specified as a relative path from the Minecraft directory to which the file should be installed.
For example `./mods` would point to the mods directory of the Minecraft instance. 

## Directories

If the selected file is a directory, then it is treated like a zip file, which means, that you can move and
rename it like a normal file, but also use the `extract` install step to move all contents of the directory
to the specified location.
