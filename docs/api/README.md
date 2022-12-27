# The AddonScript API

## The Index Endpoint

`GET {base URL}`

The index endpoint can be used to get basic information about which
API versions an API instance implements. The response object of this 
endpoint contains a `versions` property, which is an array containing
all API versions available on this instance.

### Example response body:

``` json
{
    "versions": ["v2"]
}
```

`GET {base URL}/{API version}`

Each API version also has an index endpoint with information specifically
about that version. The response of that index MAY differ across different
API versions. If an API version is not implemented on an instance, the 
corresponding index endpoint MUST return a `400 Bad Request` or 
`404 Not Found` status code.

## API Version v2:

This version of the AddonScript specification only specifies API version `v2`,
which is currently the only existing version. 

`GET {base URL}/v2`

The `v2` version index endpoint can be used to retrieve the API features
supported by this API instance on version `v2`. The response object of 
this endpint contains a `features` property, which is an array containing
all [API features](#features) supported on this instance. It also contains
a `manifest_version` property, which is the latest 
[manifest version](../schema/addonscript.md#version) available on this API
instance. This version MUST be part of AddonScript major version 2.
The manifest version of all manifests (and other objects using the manifest 
version), returned by enpoints of this API version on this instance, MUST be 
equal or less than this property, but MUST also be part of AddonScript major 
version 2 (manifest version must be greater or equal to 2). If a client does 
not support the manifest version returned by this endpoint, it SHOULD try to 
request addons from other API instances, as this instance MAY return manifests
which are unsupported by the client.

### Example response body:

``` json
{
    "features": ["addons", "env", "com.example.customfeature"],
    "manifest_version": 2
}
```

### Features

API features can be either part of the specification itself or 
are specified by third parties. Third-party API features SHOULD
be in a namespace-like format (reversed domain name).

These API features are part of the AddonScript specification itself:

- `addons`: [Addon repository](./features/addons.md)
- `files`: [File repository](./features/files.md)
- `env`: [Environment builder](./features/env.md)