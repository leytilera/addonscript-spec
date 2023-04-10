# Environment Builder Request Object

```json
{
    "addonscript": {},
    "addon": {},
    "client": {},
    "server": {}
}
```

## Required properties

### addonscript

This is an [AddonScript object](addonscript.md) containing information about the version of AddonScript used in this request.
It SHOULD be equal to the [addonscript Property](manifest.md#addonscript) of the [manifest](manifest.md) from which the request
was send.

### addon

This is an [addon descriptor object](api_addon_descriptor.md), which contains the [addon ID](manifest.md#id), 
[canonical namespace](manifest.md#namespace) and [version](manifest.md#version) of the addon, for which the
launch environment will be build.

## Optional properties

### client

This is an [environment object](#environment-object) containing information about the client environment.

### server

This is an [environment object](#environment-object) containing information about the server environment.

# Environment Object

```json
{
    "requested": [],
    "provided": []
}
```

## Optional properties

### requested 

This is an array of [addon descriptor objects](api_addon_descriptor.md) which contains all addons, that will
be part of the launch environment, including their version.

### provided

This is an array of [addon descriptor objects](api_addon_descriptor.md) which contains all addons from the 
[relations](manifest.md#relations) of the [addon](#addon), from which the request was send, that will be installed
in the instance, including their version