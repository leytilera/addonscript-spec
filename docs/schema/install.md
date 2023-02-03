# Install Object

```json
{
  "action": "move",
  "args": ["./mods"],
  "side": "both"
}
```

## Required properties

### action

This is the [install action](../concepts/install.md), which will be used at this installation step.

## Optional properties

### args

This is an array of arguments for the [install action](../concepts/install.md). Each of them takes other arguments.

### side

This specifies, for which side this install action should be performed. Valid values are `client`, `server` and `both`.
If this property is not present, it defaults to `both`.
