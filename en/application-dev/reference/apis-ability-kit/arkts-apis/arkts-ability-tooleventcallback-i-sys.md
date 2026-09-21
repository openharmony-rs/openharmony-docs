# ToolEventCallback (System API)

```TypeScript
export interface ToolEventCallback
```

ToolEventCallback is used to receive session events generated during the running of the CLI tool process.

@interface ToolEventCallback

**Since:** 26.0.0

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

## onEvent

```TypeScript
onEvent: OnEventFn
```

Callback invoked when a CLI tool event is triggered.

The [CliToolEvent](arkts-ability-clitoolevent-i-sys.md) parameter contains the event type ([ToolEventType](arkts-ability-clitoolevent-tooleventtype-e-sys.md)) and the associated data. The caller can inspect the event type to determine how to handle the data — for example, displaying stdout output to the user, logging stderr for diagnostics, or checking the exit code when an exit event is received.

@typedef { OnEventFn }

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.
