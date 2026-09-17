# GestureActionPhase

Enumerates triggering phases of gesture callbacks, corresponding to the action callbacks defined in **gesture.d.ts**. However, different gesture types support different phases (for example, **SwipeGesture** only includes the **WILL_START** enumerated value).

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## WILL_START

```TypeScript
WILL_START = 0
```

The gesture has been successfully recognized by the system, and the action-start/action callback will be executed immediately.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## WILL_END

```TypeScript
WILL_END = 1
```

This indicates the gesture has been determined to be an end, which usually happens when the user lifts their fingers, ending the entire interaction, and the action-end callback will be executed immediately.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
