# File Repository

## Endpoints

### Get a file by identifier

`GET {base URL}/v2/files/:namespace/:addon/:version/:qualifier`

This endpoint can be used to retrieve information about a specific file.
If the instance don't know this file, it must respond with status code 404.

#### Path variables:

- `namespace`: The [canonical namespace](../../concepts/namespaces.md#canonical-namespaces)
of the addon to which the file belongs to
- `addon`: The addon ID of the addon to which the file belongs to
- `version`: The addon version to which the file belongs to
- `qualifier`: The qualifier of the file

#### Responses:

- `200 OK`: The file is available in this file repository.
The response body must be an [API File Object](../../schema/api_file.md).
- `404 Not Found`: The file is not available in this file repository.

### Get a file by hash

`GET {base URL}/v2/files/:algorithm/:hash`

This endpoint can be used to retrieve information about a file from the hash value of the file.
If the instance can't find the file by the hash or does not know the specified hash algorithm,
it must respond with status code 404. 

#### Path variables:

- `algorithm`: The hash algorithm of the hash
- `hash`: The hash value of the file

#### Responses:

- `200 OK`: The file is available in this file repository.
The response body must be an [API File Object](../../schema/api_file.md).
- `404 Not Found`: The file is either not available in this file repository
or the hash algorithm is unknown to the API instance.