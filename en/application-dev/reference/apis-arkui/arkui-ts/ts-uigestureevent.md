# Bound Gesture Configuration
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=828befee530895124aaf1637c9402999a598c883 translatedAt=2026-09-01T11:58:05.497Z -->

Used to set the gestures bound to a component. You can use the UIGestureEvent object to dynamically add, remove, or clear gestures on a component, configure gesture priority and event response settings, and set parallel gestures that can be triggered simultaneously with child component gestures. This is suitable for scenarios where component gesture interactions are managed at runtime.

>**NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - In the **fingerList** of [GestureEvent](ts-gesture-common.md#gestureevent), the finger index corresponds to the position, that is, the id of fingerList[index] is index. For a finger that is pressed first but does not participate in triggering the current gesture, the corresponding position in **fingerList** is empty. It is recommended that you use **fingerInfos** preferentially.

## UIGestureEvent

Used to set the gestures bound to a component. It supports dynamically adding normal gestures or parallel gestures to a component, and removing or clearing bound gestures by gesture tag. This is suitable for scenarios where component gesture interactions are adjusted at runtime.

### addGesture

addGesture\<T>(gesture: GestureHandler\<T>, priority?: GesturePriority, mask?: GestureMask): void

Adds a gesture. Compared with addParallelGesture, addGesture is used to add a normal gesture to a component. When you need to bind a gesture that can be triggered simultaneously with child component gestures, you are advised to use addParallelGesture.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| gesture  |  [GestureHandler\<T>](./ts-gesturehandler.md#gesturehandlert) | Yes   | Gesture handler object to be added to the current component, used to define the normal gesture behavior bound to the current component. |
| priority  |  [GesturePriority](./ts-gesturehandler.md#gesturepriority) | No   | Priority of the bound gesture. GesturePriority.NORMAL indicates normal priority, which applies to scenarios where gestures are recognized in the default order. GesturePriority.PRIORITY indicates high priority, which applies to scenarios where the current component gesture needs to be recognized first. If not passed, the default value is GesturePriority.NORMAL. |
| mask  |  [GestureMask](./ts-gesture-common.md#gesturemask) | No   | Event response setting. GestureMask.Normal indicates that the default event response policy is used, which applies to scenarios where the current component gesture responds according to the default rules. GestureMask.IgnoreInternal indicates that the internal or child component gesture response is ignored, which applies to scenarios where child component gestures need to be prevented from participating in the response. If not passed, the default value is GestureMask.Normal. |

### addParallelGesture

addParallelGesture\<T>(gesture: GestureHandler\<T>, mask?: GestureMask): void

Adds a gesture that can be recognized at once by the component and its child component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| gesture | [GestureHandler\<T>](./ts-gesturehandler.md#gesturehandlert) | Yes | Gesture handler object to bind to the current component, used to define the gesture behavior that can be triggered simultaneously with child component gestures. |
| mask | [GestureMask](./ts-gesture-common.md#gesturemask) | No | Whether to block child component gestures. GestureMask.Normal indicates that child component gestures are not blocked and are recognized in the default gesture recognition order. GestureMask.IgnoreInternal indicates that child component gestures are blocked, including the system built-in gestures on child components. This is applicable to scenarios where child component gestures need to be excluded from recognition when binding parallel gestures. If this parameter is not passed, the default value is GestureMask.Normal. |

### removeGestureByTag

removeGestureByTag(tag: string): void

Removes the gesture with the specified tag that is bound to this component through modifier. This is suitable for scenarios where a tagged gesture is canceled when the component interaction mode is switched or the service state changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| tag  |  string | Yes   | Tag of the gesture handler to remove, used to match and remove the gesture that is bound through the modifier and has this tag set on the current component. |

### clearGestures

clearGestures(): void

Clears all gestures bound to this component through modifier. This is suitable for scenarios where the component interaction mode is switched or all dynamic gestures need to be disabled.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Example

See the example in [Gesture Modifier](./ts-universal-attributes-gesture-modifier.md).