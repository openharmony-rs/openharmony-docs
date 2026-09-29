# ToolEventCallback

```TypeScript
export interface ToolEventCallback
```

ToolEventCallback is used to receive session events generated during the running of the CLI tool process.

@interface ToolEventCallback

**Since:** 26.0.1

<!--Device-unnamed-export interface ToolEventCallback--><!--Device-unnamed-export interface ToolEventCallback-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

## onEvent

```TypeScript
onEvent: OnEventFn
```

Callback invoked when a CLI tool event is triggered.

The [CliToolEvent](arkts-ability-clitoolevent-i.md) parameter contains the event type ([ToolEventType](arkts-ability-clitoolevent-tooleventtype-e.md)) and the associated data. The caller can inspect the event type to determine how to handle the data — for example, displaying stdout output to the user, logging stderr for diagnostics, or checking the exit code when an exit event is received.

@typedef { OnEventFn }

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ToolEventCallback-onEvent: OnEventFn--><!--Device-ToolEventCallback-onEvent: OnEventFn-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core
