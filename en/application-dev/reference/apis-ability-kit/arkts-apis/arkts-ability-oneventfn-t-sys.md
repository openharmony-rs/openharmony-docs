# OnEventFn (System API)

```TypeScript
type OnEventFn = (event: CliToolEvent) => void
```

Defines cli event callback function.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AgentRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [CliToolEvent](arkts-ability-clitoolevent-i-sys.md) | Yes | The event sent by cli tool. |
