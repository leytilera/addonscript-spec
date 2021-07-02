# Index Object

```json
{
  "versions": {
    "1.0": "https://example.json/mymod-1.0.json"
  },
  "addons": {
    "othermod": "https://example.com/othermod.json"
  }
}
```

## Optional Properties

### versions

This is a map, with version numbers as keys and URLs to AddonScript files as values. The AddonScript file, to which the URL
points, must include the version number, which is the key in the map, and its addon ID must match the addon ID of the AddonScript
file, which includes the index object.

### addons

This is a map, with addon IDs as keys and URLs to AddonScript files as values. The addon ID of the AddonScript file, to
which the URL points, must match the key in the map.