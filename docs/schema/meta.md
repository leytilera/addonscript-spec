# Meta Object

```json
{
  "addon": {
    "name": "My cool addon name",
    "icon": "./icon.png",
    "description": "./README.md",
    "summary": "My Addon",
    "website": "https://example.com",
    "source": "https://gitea.com/user/myaddon",
    "issues": "https://gitea.com/user/myaddon/issues",
    "type": "mod",
    "contributors": [{"name": "Alice", "email": "alice@example.com"}, {"name": "Bob", "email": "bob@example.com"}]
  },
  "version": {
    "changelog": "./CHANGELOG.md",
    "timestamp": 1594753200
  },
  "additional": {}
}
```

## Optional properties

### addon

An [addon mata](#addon-meta-object) object.

### version

A [version mata](#version-meta-object) object.

### additional

This object can contain any arbitrary data,

# Addon Meta Object

## Optional Properties

### name

The full, human-readable name of the addon. This is what a program such as a launcher SHOULD
display to the user.

### icon

A [link](../concepts/links.md) to the icon of the addon. This path SHOULD point to an image file of small resolution
which is ideally square. It MAY be dispayed to users in programs.

### description

A [link](../concepts/links.md) to a description file for the addon. The file SHOULD be in CommonMark markdown.

### summary

A short description of the addon, to be shown in lists and menus where the addon is shown aside others.

### website

A URL to a website about the addon

### source

A URL to the source code of the addon.

### issues

A URL to an issue tracker for the addon.

### type

The type of the addon, for example `mod`, `modpack` or `resourcepack`.

### contributors

An array of people who have contributed to the addon. Each contributor is represented by an object, which
MUST have a `name` and a `email` property.

# Version Meta Object

## Optional properties

### changelog

A [link](../concepts/links.md) to a changelog file for the addon.

### timestamp

A unix timestamp of the time and date of the version's release.
