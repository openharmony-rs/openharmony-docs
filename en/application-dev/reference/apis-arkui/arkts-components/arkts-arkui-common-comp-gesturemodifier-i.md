# GestureModifier

```TypeScript
declare interface GestureModifier
```

**GestureModifier** is used to encapsulate the logic for dynamically setting component gestures. Developers need to customize a class to implement the **GestureModifier** interface and set or switch the gestures bound to a component in **applyGesture** as required.

**Since:** 12

<!--Device-unnamed-declare interface GestureModifier--><!--Device-unnamed-declare interface GestureModifier-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## applyGesture

```TypeScript
applyGesture(event: UIGestureEvent): void
```

Applies a gesture. It is applicable to scenarios where the gesture binding needs to be dynamically switched based on the component state or user operation. Developers can customize the implementation of this method as required. By calling the **addGesture()** method of **UIGestureEvent**, you can set the gestures to be bound to a component. The **if/else** syntax is supported for dynamic setting. If gesture switching is triggered on the component during an active gesture operation, the change takes effect in the next gesture operation after the current gesture ends (when all fingers are lifted).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureModifier-applyGesture(event: UIGestureEvent): void--><!--Device-GestureModifier-applyGesture(event: UIGestureEvent): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [UIGestureEvent](arkts-arkui-common-comp-uigestureevent-i.md) | Yes | **UIGestureEvent** object, which is used to set the gesture to be bound to the component. |
