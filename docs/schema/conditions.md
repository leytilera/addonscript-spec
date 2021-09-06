# Conditions Object

```json
{
  "require": ["some-addon"],
  "companion": ["another-addon"],
  "exclude": ["incompatible-addon"]
}
```

## Optional properties

All addons in the arrays are specified as addon IDs or namespaced addon IDs. They all need to be specified
as optional relations in this version.

### require

This is an array of addons, which are required for this relation or file.

### companion

This is an array of addons, which have to be installed together with this
relation or file. In contrast to `require`, this is a two-way dependency, which means, that if this
file or relation is installed, the addons in the array also have to be installed and if one of the
addons in the array are installed, this relation or file also have to be installed.

### exclude

This is an array of addons, which can't be installed together with this relation or file.
