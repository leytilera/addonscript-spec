# Addon repository

## Endpoints 

### Get addon

`GET {base URL}/v2/addons/:namespace/:addon`

This endpoint can be used to retrieve information about a specific addon,
including metadata, all available versions and the [canonical namespace](../../concepts/namespaces.md#canonical-namespaces) 
of the addon. 

#### Path variales:

- `namespace`: The [namespace](../../concepts/namespaces.md#repository-namespaces) of a repository which contains the addon
- `addon`: The ID of the addon

#### Responses:

- `200 OK`: The addon is available in this addon repository. 
The response body MUST be an [API Addon Object](../../schema/api_addon.md).
- `404 Not Found`: The addon is not available in this addon repository.

### Get addon manifest

`GET {base URL}/v2/addons/:namespace/:addon/:version`

This endpoint can be used to retrieve the manifest of a specific version of an addon.

#### Path variables:

- `namespace`: The [namespace](../../concepts/namespaces.md#repository-namespaces) of a repository which contains the addon
- `addon`: The ID of the addon
- `version`: The [version number](../../concepts/versioning.md) of the requested version

#### Responses:

- `200 OK`: This version of the addon is available in this addon repository.
The response body MUST be an [Addon Manifest](../../schema/manifest.md).
- `404 Not Found`: This version of the addon is not available in this addon repository.

### Get namespaces

`GET {base URL}/v2/namespaces` 

This endpoint can be used to get a list of [repository namespaces](../../concepts/namespaces.md#repository-namespaces),
which can be found on this API instance. It MAY be incomplete or empty at all. 

#### Responses:

- `200 OK`: The response body MUST be a JSON array of namespace strings.