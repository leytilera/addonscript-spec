# Environment Builder Response Object

```json
{
    "addonscript": {},
    "files": []
}
```

## Required properties

### addonscript

This is an [AddonScript object](addonscript.md) containing information about the version of AddonScript used in this response.
It MUST be equal to the [addonscript Property](api_env_request.md#addonscript) of the [request](api_env_request.md).

### files

This is an array of [File objects](file.md). These files will be concidered to be files of the addon, for which the launch
environment was build, and MUST be treated equal to the [files in the manifest](manifest.md#files).