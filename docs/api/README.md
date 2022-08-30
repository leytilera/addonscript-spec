# The AddonScript API

## The Index Endpoint

### `GET {base URL}`

The index endpoint can be used to get basic information about an API
instance, including the API versions and features supported by that
instance and the default [namespace](../concepts/namespaces.md) of the instance. 

#### Example response body:

``` json
{
    "default_namespace": "com.example",
    "versions": ["v1"],
    "features": ["listing", "filters", "com.example.customfeature"]
}
```

## Basic Endpoints

### `GET {base URL}/v1/addons/:namespace/:addon`

This endpoint can be used to retrieve information about a specific addon,
including metadata, all available versions and the [canonical namespace](../concepts/namespaces.md#canonical-namespaces) 
of the addon. 

#### Path variales:

- `namespace`: A [namespace](../concepts/namespaces.md) which contains the addon
- `addon`: The ID of the addon

#### Example response body:

``` json
{
    "id": "addon-id",
    "namespace": "com.example.canonical",
    "meta": {
        "addon": {},
        "additional": {}
    },
    "versions": [
        "1.0"
    ]
}
```

The [meta object](../schema/meta.md) is the same as in the AddonScript files,
except, that it only includes `addon` and `additional` metadata and not `version`
specific metadata.

### `GET {base URL}/v1/addons/:namespace/:addon/:version`

This endpoint can be used to retrieve a specific version of an addon.
The response body of this endpoint contains the [addon schema](../schema/addon.md),
which is also used in AddonScript JSON files.

#### Path variables:

- `namespace`: The namespace which contains the addon
- `addon`: The ID of the addon
- `version`: The [version number](../concepts/versioning.md) of the requested version

## Features

API features can be either part of the specification itself or 
are specified by third parties. Third-party API features should
be in a namespace-like format (reversed domain name).

These API features are part of the AddonScript specification itself:

- `files`: [File repository](./features/files.md)
- To be added