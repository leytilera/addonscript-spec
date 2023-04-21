# Launch Config Object

```json
{
    "main_file": "somefilequalifier",
    "main_class": "com.example.SomeClass",
    "arguments": ["--someArgument"],
    "jvm_arguments": ["-Djvmargument"],
    "java_version": 8
}
```

## Optional properties

### main_file

This is the [qualifier](./file.md#qualifier) of the main jar file for
this side. It will override any inherited main file for this side.
That file MUST be specified in the [manifest](./manifest.md) of this
addon. Setting this to an empty string will indicate, that
there is no main file for this instance, in which case the 
[main_class](#main_class) MUST be explicitly configured. 

### main_class

This is the main class for this instance, which will be used to launch
the game. It will override any inherited main class for this side. 
Setting this to an empty string will indicate, that the main class
specified in of manifest of the [main jar file](#main_file) should be used.

### arguments

This is an array of game arguments, which will be used to launch the instance
in addition to inherited arguments. They will be appended after inherited 
arguments.

### jvm_arguments

This is an array of JVM arguments, which will be used to launch the instance
in addition to inherited JVM arguments. They will be appended after inherited 
JVM arguments.

### java_version

This is the recommended major Java version for this instance. It MAY work on other
Java versions, but there is no guarantee for that. This overrides inherited `java_version`
settings.