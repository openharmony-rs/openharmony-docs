# ToolEventType (System API)

```TypeScript
export enum ToolEventType
```

Enumerates the event types that a CLI tool or command process can produce during execution.

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## STDOUT

```TypeScript
STDOUT = 'stdout'
```

Standard output event. The [data](arkts-ability-clitoolevent-i-sys.md#data) field contains the text written by the tool to its standard output (stdout) stream.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## STDERR

```TypeScript
STDERR = 'stderr'
```

Standard error event. The [data](arkts-ability-clitoolevent-i-sys.md#data) field contains the text written by the tool to its standard error (stderr) stream. Note that some tools write diagnostic or progress information to stderr even when execution is proceeding normally.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## EXIT

```TypeScript
EXIT = 'exit'
```

Exit event. The tool process has exited. The [data](arkts-ability-clitoolevent-i-sys.md#data) field contains the exit code as a string.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## ERROR

```TypeScript
ERROR = 'error'
```

Error event. The tool process encountered an error that prevented normal execution. The [data](arkts-ability-clitoolevent-i-sys.md#data) field contains a descriptive error message.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
