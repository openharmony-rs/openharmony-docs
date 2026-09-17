# UIGestureEvent

Provides APIs for configuring gestures bound to a component.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addGesture

```TypeScript
addGesture<T>(gesture: GestureHandler<T>, priority?: GesturePriority, mask?: GestureMask): void
```

Adds a gesture.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesture | [GestureHandler](arkts-arkui-gesturehandler-c.md)&lt;T&gt; | Yes | Gesture handler object. |
| priority | [GesturePriority](arkts-arkui-gesturepriority-e.md) | No | Priority of the bound gesture.<br>Default value: **GesturePriority.NORMAL**. |
| mask | [GestureMask](arkts-arkui-gesturemask-e.md) | No | Mask for gesture events.<br>Default value: **GestureMask.Normal**. |

## addParallelGesture

```TypeScript
addParallelGesture<T>(gesture: GestureHandler<T>, mask?: GestureMask): void
```

Adds a gesture that can be recognized at once by the component and its child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesture | [GestureHandler](arkts-arkui-gesturehandler-c.md)&lt;T&gt; | Yes | Gesture handler object. |
| mask | [GestureMask](arkts-arkui-gesturemask-e.md) | No | Mask for gesture events.<br>Default value: **GestureMask.Normal**. |

## clearGestures

```TypeScript
clearGestures(): void
```

Clears all gestures that have been bound to the component through a modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## removeGestureByTag

```TypeScript
removeGestureByTag(tag: string): void
```

Remove a gesture from a component that has been bound with a specific tag through a modifier.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tag | string | Yes | Gesture handler flag. |
