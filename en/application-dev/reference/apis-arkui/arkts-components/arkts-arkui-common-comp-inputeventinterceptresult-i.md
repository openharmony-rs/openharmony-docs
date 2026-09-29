# InputEventInterceptResult

```TypeScript
declare interface InputEventInterceptResult
```

Input event interception result interface, used by the listener callback [InputEventListener](arkts-arkui-common-comp-inputeventlistener-t.md) to return the interception decision.

**Since:** 26.0.0

<!--Device-unnamed-declare interface InputEventInterceptResult--><!--Device-unnamed-declare interface InputEventInterceptResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: InputEventInterceptAction
```

Input event interception action.

**CONTINUE**: The event is allowed to continue being passed to the UI framework.

**BLOCK**: The event is blocked from being passed to the UI framework.

**Type:** [InputEventInterceptAction](../arkts-apis/arkts-arkui-inputeventinterceptaction-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-InputEventInterceptResult-action: InputEventInterceptAction--><!--Device-InputEventInterceptResult-action: InputEventInterceptAction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
