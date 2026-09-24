# GestureModifier

```TypeScript
declare interface GestureModifier
```

You need a custom class to implement the **GestureModifier** API.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## applyGesture

```TypeScript
applyGesture(event: UIGestureEvent): void
```

Applies a gesture.

You can customize this API as required. Dynamic configuration using the **if/else** syntax is supported. If gesture switching is triggered during an active gesture operation, the change takes effect in the next gesture operation after the current one completes (when all fingers are lifted).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [UIGestureEvent](arkts-arkui-common-comp-uigestureevent-i.md) | Yes | **UIGestureEvent** object, which is used to set the gesture to be bound to the component. |
