# Repository Object

```json
{
  "id": "asrepo",
  "type": "api",
  "link": "https://addonscript.net/repo"
}
```

## Required properties

### id

This is the ID of the repository. It has to be unique to the AddonScript file.

### type

This is the type of the repository. Possible values are `api` or `maven`.

### link

This is the base URL of the repository. While other URLs in AddonScript can have different schemes, 
the base URL has to be a http(s) URL.
