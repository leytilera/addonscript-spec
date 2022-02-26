# Links

AddonScript uses links to point to specific files. AddonScript specifies three link types, which can be used
to point to files.

## http(s)

`https://example.com/file.jar`

This link type is mostly self-explaining. It is just a simple http or https URL, which points to
a file on a http server.

## file

`./relative/path/to/file.jar`

This is a relative path to a file. It can only be used with [packaging](../packaging/README.md)
or in some third-party environments, which are not covered by this specification.
