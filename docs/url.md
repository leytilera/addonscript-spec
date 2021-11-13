# URLs

AddonScript uses URLs to point to specific files. AddonScript specifies three URL schemes, which can be used
to point to files.

## http(s)

`https://example.com/file.jar`

This URL scheme is mostly self-explaining. It is jsut a simple http or https URL, which points to
a file on a http server.

## mvn

`mvn://com.example/someartifact/1.0/core.jar`

This URL scheme is used, to point to a maven artifact. The URL consists of multiple parts.
In this example `com.example` it the namespace of the artifact, `someartifact` is the artifact ID,
`1.0` is the version, `core` is an optional specifier and `.jar` is the file ending.
`mvn://com.example/someartifact/1.0.jar` would also be a valid URL without an optional specifier.

## file

`./relative/path/to/file.jar`

This is a relative path to a file. It can only be used with [packaging](packaging/README.md)
or in some third-party environments, which are not covered by this specification.
