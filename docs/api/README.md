# The AddonScript API

## The Index Endpoint

`GET {base URL}`

The index endpoint can be used to get basic information about an API
instance, including the API versions and features supported by that
instance and the [default namespace](../concepts/namespaces.md#default-namespaces) of the instance. 
The response object of this endpoint contains a `versions` property, which is an object with API
version numbers as keys and the configuration objects for the specific API version as values.
For API version `v2` (AddonScript major release 2) the configuration object contains a `default_namespace`
property, which is the [default namespace](../concepts/namespaces.md#default-namespaces) of the API
instance, and a `features` property, which is an array containing all [API features](#features)
available on this API instance.

### Example response body:

``` json
{
    "versions": {
        "v2": {
            "default_namespace": "com.example",
            "features": ["listing", "filters", "com.example.customfeature"]
        }
    }
}
```

## Features

API features can be either part of the specification itself or 
are specified by third parties. Third-party API features should
be in a namespace-like format (reversed domain name).

These API features are part of the AddonScript specification itself:

- `addons`: [Addon repository](./features/addons.md)
- `files`: [File repository](./features/files.md)