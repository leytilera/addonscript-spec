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
all [API features](#features) supported on this instance.

### Example response body:

``` json
{
    "features": ["addons", "env", "com.example.customfeature"]
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