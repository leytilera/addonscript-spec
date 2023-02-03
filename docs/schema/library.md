# Library Object

```json
{
    "file": "somequalifier",
    "side": "both"
}
```

## Required properties

### file

This is the [qualifier](./file.md#qualifier) of the file of this library.
That file MUST be specified in the [manifest](./manifest.md), which
uses this library.

### Optional properties

### side

This specifies, for which side this library should be used. Valid values
are `client`, `server` and `both`. If this property is not present, 
it defaults to `both`.