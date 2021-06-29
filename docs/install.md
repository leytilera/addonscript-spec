# File installing

## Install steps

### move
```move [location]``` \
move is simplest install step of all. It just moves the selected file to 
the given location.

### extract
```extract [location]``` \
extract can be used with zip files, to extract the contents of the zip file
to the given location.

### rename
```rename [new name]``` \
rename renames the selected file to the new given filename.

### execute
```execute [location] [arguments]```
execute can be used with an executable jar file. The jar file will be executed with the given arguments and 
the given location as working directory. A client should inform the user before just executing the file and
ask him for permission to do so and/or it should execute the jar in a closed environment, like a container,
to prevent viruses from being installed.

### select
```select [filename]```
select is used to select the file with the given file name for other installation steps.
The file name can also be a relative path, if the file is not directly in the Minecraft directory.
If no file name is given, the selection resets to the original file itself, also if it was already moved to another location.

## Locations

Locations are specified as a relative path from the Minecraft directory. For example `./mods` 
would point to the mods directory of the Minecraft instance, to which the file should be installed.

## Directories

If the selected file is a directory, then it is treated like a zip file, which means, that you can move and
rename it like normal files, but also use the `extract` install step, to move all contents of the directory
to the specified location.
