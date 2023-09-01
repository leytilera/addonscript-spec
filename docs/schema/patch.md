# Launch Patch Object

```json
{
    "side": "client",
    "main_class": "com.example.SomeClass",
    "arguments": [],
    "jvm_arguments": ["-Djvmargument"],
    "replace_jvm_arguments": false,
    "java_version": 8
}
```

## Required properties

### side

This specifies, for which side this patch should be applied. Valid values are `client`, `server` and `both`.

## Optional properties

### main_class

This is the main class for this instance, which will be used to launch
the game. It will override any main class from other patches for this side. 
Setting this to an empty string will indicate, that the main class
specified in of manifest of the [main jar file](../concepts/instance.md#main-file) 
should be used.

### arguments

This is an array of [game argument objects](#game-argument-object), which will be 
used to launch the instance in addition to arguments from other patches.

### jvm_arguments

This is an array of JVM arguments, which will be used to launch the instance
in addition to inherited JVM arguments. They will be appended after JVM arguments
from other patches.

### replace_jvm_arguments

This is a boolean which indicates, if the [JVM arguments](#jvmarguments) from
this patch should replace all other JVM arguments from other patches instead of
appending them. Defaults to `false`.

### java_version

This is the recommended major Java version for this instance. It MAY work on other
Java versions, but there is no guarantee for that. This overrides `java_version`
settings from other patches.

# Game Argument Object

```json
{
    "mode": "replace", //replace, append, expand, override
    "key": "tweakerClass",
    "value": "net.anvilcraft.SomeTweaker",
    "raw": "--some ArguemtnString"
}
```

## Required properties

### mode

This is the mode, which defines how the argument is added to the other arguments.
Possible values are:

- `replace` Removes all arguments with the same `key` as this one and adds this argument
  instead. Prevents other arguments with the same `key` to be added laster, except they
  are also using the `replace` mode. Requires `key` to be set.
- `append` Appends the argument to the previous ones.
- `expand` Appends the argument to the previous ones, if none with the same key was already
  added. Requires `key` to be set.
- `override` Overrides all previous arguments with those specified in `raw`
  Requires `raw` to be set.

## Optional properties

### key

This is the key of the argument, which MUST be a string. If used together with 
`value` the resulting game argument will be in the form `--<key> <value>`. 
If `raw` is not set, this property is required.

### value

This is the value of the argument, which MUST be a string. It is used together 
with `key` to generate the resulting game argument. Defaults to an empty string.

### raw

This is a string, which can override the resulting game argument. If this is set,
the resulting game argument will be equal to this string instead of the generated
argument. `key` MAY still be used in conjunction with this and MUST be considered 
by the `mode`.