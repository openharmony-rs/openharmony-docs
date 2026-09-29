# OnEventFn

```TypeScript
type OnEventFn = (event: CliToolEvent) => void
```

Defines the callback function type for receiving CLI tool events.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-type OnEventFn = (event: CliToolEvent) => void--><!--Device-unnamed-type OnEventFn = (event: CliToolEvent) => void-End-->

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [CliToolEvent](arkts-ability-clitoolevent-i.md) | Yes | The event sent by cli tool. |
