# Environment Builder Response Object

```json
{
    "addonscript": {},
    "files": [],
    "launch_client": {},
    "launch_server": {},
}
```

## Required properties

### addonscript

This is an [AddonScript object](addonscript.md) containing information about the version of AddonScript used in this response.
It MUST be equal to the [addonscript Property](api_builder_request.md#addonscript) of the [request](api_builder_request.md).

### files

This is an array of [File objects](file.md). These files will be concidered to be files of the addon, for which the launch
environment was build, and MUST be treated equal to the [files in the manifest](manifest.md#files).

## Optional properties

### launch_client

This is a [Launch Config object](./patch.md) for the client, which can be used, to modify the launch configuration of the instance.

### launch_server

This is a [Launch Config object](./patch.md) for the server, which can be used, to modify the launch configuration of the instance.