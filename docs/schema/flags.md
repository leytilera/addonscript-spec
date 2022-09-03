# Flags object

```json
{
    "client": ["optional"],
    "server": ["required"],
    "both": ["included"]
}
```

## Optional properties

### client

This is an array of [flags](../concepts/flags.md) which only apply on the client side.

### server

This is an array of [flags](../concepts/flags.md) which only apply on the server side. 

### both

This is an array of [flags](../concepts/flags.md) which apply on both sides. AddonScript will
treat each flag in this array as if it was in the [client array](#client) and the [server array](#server).