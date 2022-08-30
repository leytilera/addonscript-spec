# File Repository

## Endpoints

### `GET {base URL}/v1/files/:namespace/:addon/:version/:qualifier`

This endpoint can be used to retrieve information about a specific file.
If the instance don't know this file, it must respond with status code 404.

#### Path variables:

- `namespace`: The [canonical namespace](../../concepts/namespaces.md#canonical-namespaces)
of the addon to which the file belongs to
- `addon`: The addon ID of the addon to which the file belongs to
- `version`: The addon version to which the file belongs to
- `qualifier`: The qualifier of the file

#### Example response:

```json
{
    "links": ["https://example.com/file.jar"],
    "filename?": "file.jar",
    "hashes": {
        "sha1": "somesha1checksum"
    },
    "meta": {
        "additional": {}
    }
}
```

### `GET {base URL}/v1/files/:algorithm/:hash`

This endpoint can be used to retrieve information about a file from the hash value of the file.
If the instance can't find the file by the hash or does not know the specified hash algorithm,
it must respond with status code 404. 

#### Path variables:

- `algorithm`: The hash algorithm of the hash
- `hash`: The hash value of the file

#### Example response:

```json
{
    "links": ["https://example.com/file.jar"],
    "filename?": "file.jar",
    "hashes": {
        "sha1": "somesha1checksum"
    },
    "meta": {
        "additional": {}
    }
}
```