# LongPressGestureEvent

```TypeScript
interface LongPressGestureEvent extends BaseGestureEvent
```

Inherits from [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-common-comp-commonmethod-c.md#ongesturejudgebegin).

**Inheritance/Implementation:** LongPressGestureEvent extends [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat: boolean
```

Whether the event is a repeated trigger event. **true**: The event is repeated. **false**: The event is not repeated.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
