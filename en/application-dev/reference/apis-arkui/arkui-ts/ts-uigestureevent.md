# Bound Gesture Configuration
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

You can set the gestures that are bound to a component. Specifically, you can add or remove gestures by calling the APIs of the **UIGestureEvent** object.

>**NOTE**
>
>The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>  In **fingerList** of [GestureEvent](ts-gesture-common.md#gestureevent), the index of a finger corresponds to its position, that is, the ID of a finger in **fingerList[index]** refers to its index. If a finger is pressed first and does not participate in triggering of the current gesture, its position in **fingerList** is left empty. You are advised to use **fingerInfos** when possible.

## UIGestureEvent

Provides APIs for configuring gestures bound to a component.

### addGesture

addGesture\<T>(gesture: GestureHandler\<T>, priority?: GesturePriority, mask?: GestureMask): void

Adds a gesture.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| gesture  |  [GestureHandler\<T>](./ts-gesturehandler.md#gesturehandlert) | Yes  | Gesture handler object.|
| priority  |  [GesturePriority](./ts-gesturehandler.md#gesturepriority) | No  | Priority of the bound gesture.<br>Default value: **GesturePriority.NORMAL**.|
| mask  |  [GestureMask](./ts-gesture-common.md#gesturemask) | No  | Mask for gesture events.<br>Default value: **GestureMask.Normal**.|

### addParallelGesture

addParallelGesture\<T>(gesture: GestureHandler\<T>, mask?: GestureMask): void

Adds a gesture that can be recognized at once by the component and its child component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| gesture  |  [GestureHandler\<T>](./ts-gesturehandler.md#gesturehandlert) | Yes  | Gesture handler object.|
| mask  |  [GestureMask](./ts-gesture-common.md#gesturemask) | No  | Mask for gesture events.<br>Default value: **GestureMask.Normal**.|

### removeGestureByTag

removeGestureByTag(tag: string): void

Remove a gesture from a component that has been bound with a specific tag through a modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| tag  |  string | Yes  | Gesture handler flag.|

### clearGestures

clearGestures(): void

Clears all gestures that have been bound to the component through a modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Example

See the example in [Gesture Modifier](./ts-universal-attributes-gesture-modifier.md).
