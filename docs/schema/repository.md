# Repository Object

```json
{
  "id": "asrepo",
  "type": "api",
  "url": "https://api.addonscript.net"
}
```

## Required properties

### id

This is the ID of the repository. It has to be unique to the AddonScript file.

### type

This is the type of the repository. Possible values are `addonscript` or `maven`.
A repository of the type `addonscript` is an instance of the [AddonScript API](../api).
AddonScript will use the basic endpoints of that instance to retrieve available versions
of a specific addon, as well as the [addon JSON](./addon.md) for a specific version of an 
addon. 


### url

This is the base URL of an [AddonScript API](../api) instance, if the repository 
type is `addonscript`, or the base URL of a Maven Repository, if the repository 
type is `maven`.
