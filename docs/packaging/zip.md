# Zip Packaging

With zip packaging, the AddonScript file and the associated files are contained in
a zip file. The AddonScript file MUST be named `addon.json` and MUST either be placed
at the root of the zip file or, if there is just one directory in the root of the zip file,
in this directory. All files and directories inside the zip file can be accessed from AddonScript
using the [file links](../concepts/links.md#file). The path from the file URL is relative to the location of
the AddonScript file.
