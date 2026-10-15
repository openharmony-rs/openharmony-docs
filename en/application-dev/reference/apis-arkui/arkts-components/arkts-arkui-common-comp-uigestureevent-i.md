# UIGestureEvent

```TypeScript
declare interface UIGestureEvent
```

Used to set the gestures bound to a component. It supports dynamically adding normal gestures or parallel gestures to a component, and removing or clearing bound gestures by gesture tag. This is suitable for scenarios where component gesture interactions are adjusted at runtime.

**Since:** 12

<!--Device-unnamed-declare interface UIGestureEvent--><!--Device-unnamed-declare interface UIGestureEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addGesture

```TypeScript
addGesture<T>(gesture: GestureHandler<T>, priority?: GesturePriority, mask?: GestureMask): void
```

Adds a gesture. Compared with addParallelGesture, addGesture is used to add a normal gesture to a component. When you need to bind a gesture that can be triggered simultaneously with child component gestures, you are advised to use addParallelGesture.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIGestureEvent-addGesture<T>(gesture: GestureHandler<T>, priority?: GesturePriority, mask?: GestureMask): void--><!--Device-UIGestureEvent-addGesture<T>(gesture: GestureHandler<T>, priority?: GesturePriority, mask?: GestureMask): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesture | [GestureHandler](arkts-arkui-tapgesture-comp-gesturehandler-c.md)&lt;T&gt; | Yes | Gesture handler object to be added to the current component, used to define the normal gesture behavior bound to the current component. |
| priority | [GesturePriority](arkts-arkui-tapgesture-comp-gesturepriority-e.md) | No | Priority of the bound gesture. **GesturePriority.NORMAL** indicates normal priority, which applies to scenarios where gestures are recognized in the default order. **GesturePriority.PRIORITY** indicates high priority, which applies to scenarios where the current component gesture needs to be recognized first.<br>Default value: **GesturePriority.NORMAL**. |
| mask | [GestureMask](arkts-arkui-tapgesture-comp-gesturemask-e.md) | No | Event response setting. **GestureMask.Normal** indicates that the default event response policy is used, which applies to scenarios where the current component gesture responds according to the default rules. **GestureMask.IgnoreInternal** indicates that the internal or child component gesture response is ignored, which applies to scenarios where child component gestures need to be prevented from participating in the response.<br>Default value: **GestureMask.Normal**. |

## addParallelGesture

```TypeScript
addParallelGesture<T>(gesture: GestureHandler<T>, mask?: GestureMask): void
```

Adds a gesture that can be recognized at once by the component and its child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIGestureEvent-addParallelGesture<T>(gesture: GestureHandler<T>, mask?: GestureMask): void--><!--Device-UIGestureEvent-addParallelGesture<T>(gesture: GestureHandler<T>, mask?: GestureMask): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gesture | [GestureHandler](arkts-arkui-tapgesture-comp-gesturehandler-c.md)&lt;T&gt; | Yes | Gesture handler object to bind to the current component, used to define the gesture behavior that can be triggered simultaneously with child component gestures. |
| mask | [GestureMask](arkts-arkui-tapgesture-comp-gesturemask-e.md) | No | Whether to block child component gestures. **GestureMask.Normal** indicates that child component gestures are not blocked and are recognized in the default gesture recognition order. **GestureMask.IgnoreInternal** indicates that child component gestures are blocked, including the system built-in gestures on child components. This is applicable to scenarios where child component gestures need to be excluded from recognition when binding parallel gestures.<br>Default value: **GestureMask.Normal**. |

## clearGestures

```TypeScript
clearGestures(): void
```

Clears all gestures bound to this component through modifier. This is suitable for scenarios where the component interaction mode is switched or all dynamic gestures need to be disabled.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIGestureEvent-clearGestures(): void--><!--Device-UIGestureEvent-clearGestures(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## removeGestureByTag

```TypeScript
removeGestureByTag(tag: string): void
```

Removes the gesture with the specified tag that is bound to this component through modifier. This is suitable for scenarios where a tagged gesture is canceled when the component interaction mode is switched or the service state changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UIGestureEvent-removeGestureByTag(tag: string): void--><!--Device-UIGestureEvent-removeGestureByTag(tag: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tag | string | Yes | Tag of the gesture handler to remove, used to match and remove the gesture that is bound through the modifier and has this tag set on the current component. |
