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
    "contributors": ["Alice", "Bob"]
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

The full, human-readable name of the addon. This is what a program such as a launcher should
display to the user.

### icon

A path to the icon of the addon. This path should point to an image file of small resolution
which is ideally square. It can be dispayed to users in programs.

### description

A path to a description file for the addon. The file should be in CommonMark markdown.

### summary

A short description of the addon, to be shown in lists and menus where the addon is shown aside others.

### website

A URL to a website about the addon

### source

A URL to the source code of the addon.

### issues

A URL to an issue tracker for the addon.

### contributors

An array of people who have contributed to the addon.

# Version Meta Object

## Optional properties

### changelog

A path to a changelog file for the addon.

### timestamp

A unix timestamp of the time and date of the version's release.
