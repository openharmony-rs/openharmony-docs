# InputEventInterceptAction

```TypeScript
declare enum InputEventInterceptAction
```

Enumerates the input event interception actions, used to control whether input events continue to be delivered to the UI framework, applicable to scenarios where input events need to be allowed or blocked based on business rules.

**Since:** 26.0.0

<!--Device-unnamed-declare enum InputEventInterceptAction--><!--Device-unnamed-declare enum InputEventInterceptAction-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTINUE

```TypeScript
CONTINUE = 0
```

The event is permitted to propagate to the UI framework.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-InputEventInterceptAction-CONTINUE = 0--><!--Device-InputEventInterceptAction-CONTINUE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BLOCK

```TypeScript
BLOCK = 1
```

The event is blocked from propagating to the UI framework.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-InputEventInterceptAction-BLOCK = 1--><!--Device-InputEventInterceptAction-BLOCK = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
