# TapGestureEvent

Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin).

**Inheritance/Implementation:** TapGestureEvent extends [BaseGestureEvent](arkts-arkui-basegestureevent-i.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tapLocation

```TypeScript
tapLocation?: EventLocationInfo
```

Coordinate information of the current tap gesture. For non-tap gestures, the return value of **tapLocation** is **undefined**.

**Type:** [EventLocationInfo](arkts-arkui-eventlocationinfo-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
