# Repository Object

```json
{
  "namespace": "net.addonscript",
  "instances": ["https://api.addonscript.net"]
}
```

## Required properties

### namespace

This is the [namespace](../concepts/namespaces.md), which describes this repository.

### instances

This is an array of base URLs of [AddonScript API](../api) instances, on which this
repository can be found. To get an addon from this repository, AddonScript will
try to get it from the [addon endpoint](../api/features/addons.md#get-addon)
of these API instances in the order, in which they are specified in this array.
Instances in this array with the `env` [feature](../api/features/env.md) will
be used by AddonScript, to request the launch environment for an addon with a
[canonical namespace](../concepts/namespaces.md#canonical-namespaces) equal
to the [namespace](#namespace) of this repository. The first API instance with 
the `env` feature will be used in this case with the others as fallback.