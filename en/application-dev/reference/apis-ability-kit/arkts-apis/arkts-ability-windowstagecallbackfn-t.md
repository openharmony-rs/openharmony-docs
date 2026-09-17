# WindowStageCallbackFn

```TypeScript
type WindowStageCallbackFn = (ability: any, windowStage: window.WindowStage) => void
```

The callback was called when both ability and window stage are registered for listening.

@typedef { function }

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ability | any | Yes | Indicates the ability to register for listening. |
| windowStage | [window.WindowStage](../../apis-arkui/arkts-apis/arkts-arkui-window-windowstage-i.md) | Yes | Indicates the window stage to register for listening. |
