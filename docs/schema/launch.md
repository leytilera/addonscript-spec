# Launch Config Object

```json
{
    "libraries": [],
    "java_version": 8,
    "client": {},
    "server": {}
}
```

## Optional properties


### libraries

This is an array of [libraries](library.md), which are added to the instance in
addition to those of inherited launch configurations.

### java_version

This is the recommended major Java version for this instance. It MAY work on other
Java versions, but there is no guarantee for that. This overrides inherited `java_version`
settings.

### client

This is a [side config object](#side-config-object) containing the launch configuration
for the client.

### server

This is a [side config object](#side-config-object) containing the launch configuration
for the server.

# Side Config Object

```json
{
    "main_file": "somefilequalifier",
    "main_class": "com.example.SomeClass",
    "arguments": ["--someArgument"],
    "jvm_arguments": ["-Djvmargument"]
}
```

## Optional properties

### main_file

This is the [qualifier](./file.md#qualifier) of the main jar file for
this side. It will override any inherited main file for this side.
That file MUST be specified in the [manifest](./manifest.md), which
uses this library. Setting this to an empty string will indicate, that
there is no main file for this instance, in which case the 
[main_file](#mainfile) MUST be explicitly configured. 

### main_class

This is the main class for this instance, which will be used to launch
the game. It will override any inherited main class for this side. 
Setting this to an empty string will indicate, that the main class
specified in of manifest of the [main jar file](#mainfile) should be used.

### arguments

This is an array of arguments, which will be used to launch the instance
in addition to inherited arguments. They will be appended after inherited 
arguments.

### jvm_arguments

This is an array of JVM arguments, which will be used to launch the instance
in addition to inherited JVM arguments. They will be appended after inherited 
JVM arguments.