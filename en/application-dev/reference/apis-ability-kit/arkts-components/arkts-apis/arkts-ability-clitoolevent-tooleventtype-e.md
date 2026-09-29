# ToolEventType

```TypeScript
export enum ToolEventType
```

Enumerates the event types that a CLI tool or command process can produce during execution.

**Since:** 26.0.1

<!--Device-unnamed-export enum ToolEventType--><!--Device-unnamed-export enum ToolEventType-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## STDOUT

```TypeScript
STDOUT = 'stdout'
```

Standard output event. The [data](arkts-ability-clitoolevent-i.md#data) field contains the text written by the tool to its standard output (stdout) stream.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ToolEventType-STDOUT = 'stdout'--><!--Device-ToolEventType-STDOUT = 'stdout'-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## STDERR

```TypeScript
STDERR = 'stderr'
```

Standard error event. The [data](arkts-ability-clitoolevent-i.md#data) field contains the text written by the tool to its standard error (stderr) stream. Note that some tools write diagnostic or progress information to stderr even when execution is proceeding normally.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ToolEventType-STDERR = 'stderr'--><!--Device-ToolEventType-STDERR = 'stderr'-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## EXIT

```TypeScript
EXIT = 'exit'
```

Exit event. The tool process has exited. The [data](arkts-ability-clitoolevent-i.md#data) field contains the exit code as a string.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ToolEventType-EXIT = 'exit'--><!--Device-ToolEventType-EXIT = 'exit'-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## ERROR

```TypeScript
ERROR = 'error'
```

Error event. The tool process encountered an error that prevented normal execution. The [data](arkts-ability-clitoolevent-i.md#data) field contains a descriptive error message.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ToolEventType-ERROR = 'error'--><!--Device-ToolEventType-ERROR = 'error'-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
