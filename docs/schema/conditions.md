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

This is an array of addons, which are required for this relation or file and must be present.

### companion

This is an array of file IDs which go together with this relation/file.
This field is fairly complex.

The `companion` field is used to represent a relation between an optional file/relation, and an optional relation.
This means, if one of them isn't optional, an error occurs.

The behaviour can be summarized as such:

1. The relation/file that declares companions is only installed if all companions are also installed.
2. A relation that is a companion also will not be installed, unless **all** files/relations of that
   relation declare it as a companion are also installed.

This can be described as the relation and the relation/file that is a companion of the relation requiring **eachother**.
The reason this isn't done by declaring a `require` condition both on the addon/file and the file, is that files
cannot be referenced, as only addon-ids are used.

<!--this table has to be in HTML and without indentation to allow markdown code blocks-->
<table>
<thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Installed if</th>
<th>Flags</th>
<th>Conditions</th>
</tr>
</thead>
<tbody>
<tr>
<td>companion-relation</td>
<td>relation</td>
<td><em>example-file</em> is installed</td>
<td>

```json
["optional"]
```

</td>
<td>

```json
{}
```

</td>
</tr>
<tr>
<td>example-file</td>
<td>file</td>
<td><em>companion-relation</em> is installed</td>
<td>

```json
["optional"]
```

</td>
<td>

<!-- prettier-ignore -->
```json
{
  "companion": [
    "companion-relation"
  ]
}
```

</td>
</tr>
</tbody>
</table>

An example of this would be to present alternative files for different modloaders in the case of a mod.
Let's consider this example addon:

```json
{
  "addonscript": { "version": 2 },
  "id": "example-addon",
  "version": "0.1.0",
  "relations": [
    {
      "id": "forge",
      "version": "37.0",
      "flags": ["optional"]
    },
    {
      "id": "fabric",
      "version": "9.0",
      "flags": ["optional"]
    },
    {
      "id": "fabric-api",
      "version": "0.42.1",
      "flags": ["optional"],
      "conditions": {
        "companion": ["fabric"]
      }
    }
  ],
  "files": [
    {
      "id": "example-addon-forge",
      "url": "./example_addon_forge.jar",
      "conditions": {
        "companion": ["forge"]
      },
      "flags": ["optional"]
    },
    {
      "id": "example-addon-fabric",
      "url": "./example_addon_fabric.jar",
      "conditions": {
        "companion": ["fabric"]
      },
      "flags": ["optional"]
    }
  ]
}
```

This example addon provides files for forge and fabric, the files both having their
respective modloaders as companions. This allows a mod to ship files for both modloaders
without using different addons.

Also note that the addon also adds the `fabric` relation to the `fabric-api` relation.
Thus it will also be installed if the fabric version of the mod is used.

### exclude

This is an array of addons, which can't be installed together with this relation or file.
