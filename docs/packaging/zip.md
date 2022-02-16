# Zip Packaging

With zip packaging, the AddonScript file and the associated files are contained in
a zip file. The AddonScript file has to be called `addon.json` and can either be placed
at the root of the zip file or, if there is just one directory in the root of the zip file,
in this directory. All files and directories inside the zip file can be accessed from AddonScript
using the [file links](../concepts/link.md#file). The path from the file URL is relative to the location of
the AddonScript file.
