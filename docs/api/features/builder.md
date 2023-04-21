# Environment builder 

## Endpoints

### Build launch environment

`POST {base URL}/v2/builder`

This endpoint can be used to build the launch environment for an [instance addon](../../concepts/instance.md).

If an [instance addon](../../concepts/instance.md), which has to provide a launch configuration, has
[`use_builder`](../../schema/manifest.md#use_builder) set to `true`, AddonScript will send a request to this
endpoint of an API instance, on which the [repository](../../schema/repository.md) of the
[namespace](../../schema/manifest.md#namespace) of this addon can be found.
This request contains information about the AddonScript [schema version](../../schema/api_builder_request.md#addonscript),
which will be used in the request and about which [addon](../../schema/api_builder_request.md#addon) this request is for.
Moreover it contains for both sides a list of addons, including their version, which will be part of the 
[addon](../../schema/api_builder_request.md#addon) in this environment on that side. The [manifest](../../schema/manifest.md) 
of this [addon](../../schema/api_builder_request.md#addon) uses the `expected` [relation flag](../../concepts/flags.md#relational-flags)
to tell AddonScript, which [related addons](../../schema/relation.md) MAY and which MUST be requested on this endpoint
and which [versions](../../schema/relation.md#version) of them are valid. Which exact version of them and which optional
addons will be requested is either decided by the user, if the instance addon is installed manually, or by another
[instance addon](../../concepts/instance.md), which inherits the launch configuration from this addon. In later case,
that [instance addon](../../concepts/instance.md) uses the `env` [relation flag](../../concepts/flags.md#relational-flags)
to specify an exact version for each addon, that will be requested. Each required `expected` addon MUST be covered this way
while only those optional `expected` addons will be requested, which are covered this way. Lastly the request also contains
for each side a list of all [related addons](../../schema/relation.md) of this one, which are or will be installed
into this instance, including their version. This does not include [relations](../../schema/relation.md) with the 
`expected` [relation flag](../../concepts/flags.md#relational-flags). 

Since the API instance MAY download files or build/compile things to build the launch environment, this request MAY 
take some time so the client implementation SHOULD set the request timeout for this endpoint rather high. It is
RECOMMENDED to have a timeout of at least 5 minutes, better about 10 minutes.

After the launch environment was build by the API instance, this endpoint will respond with a list of
[file objects](../../schema/api_builder_response.md#files), the AddonScript 
[schema version](../../schema/api_builder_response.md#addonscript) for the response and the 
[launch configuration](../../concepts/instance.md#launch-configurations) for this addon. 
These files MUST be considered to be part of the [files](../../schema/manifest.md#files) of the addon, 
from which the request was send and can then be installed. The launch configuration will override the entirely.

#### Request Body:

The request body MUST be an [Environment Builder Request Object](../../schema/api_builder_request.md).

#### Responses:

- `200 OK`: The launch environment was successfully build.
The response body MUST be an [Environment Builder Response Object](../../schema/api_builder_response.md).
- `400 Bad Request`: The server was not able to build the launch environment because of
invalid information send by the client. The client SHOULD NOT try this request on
another API instance, since the request is invalid.
- `404 Not Found`: The launch environment can't be build for this addon, because no information
about it was found on this API instance. The client SHOULD try to use another API instance
to build the environment.
- `500 Internal Server Error`: The server was not able to build the launch environment
because of an internal error. The client MAY try to request the environment on another
API instance.