# UIGestureEvent

Defines a UIGestureEvent which is used to set different gestures to target component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface UIGestureEvent--><!--Device-unnamed-export declare interface UIGestureEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addGesture

```TypeScript
addGesture(gesture: GestureHandler, priority?: GesturePriority, mask?: GestureMask): void
```

Add a gesture bound to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIGestureEvent-addGesture(gesture: GestureHandler, priority?: GesturePriority, mask?: GestureMask): void--><!--Device-UIGestureEvent-addGesture(gesture: GestureHandler, priority?: GesturePriority, mask?: GestureMask): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | gesture indicates the gesture bound to a component. |
| priority | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | priority indicates the gesture's priority. |
| mask | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | mask indicates the gesture's GestureMask value. |

## addParallelGesture

```TypeScript
addParallelGesture(gesture: GestureHandler, mask?: GestureMask): void
```

Add a parallel gesture bound to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIGestureEvent-addParallelGesture(gesture: GestureHandler, mask?: GestureMask): void--><!--Device-UIGestureEvent-addParallelGesture(gesture: GestureHandler, mask?: GestureMask): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | gesture indicates the gesture bound to a component. |
| mask | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | mask indicates the gesture's GestureMask value. |

## clearGestures

```TypeScript
clearGestures(): void
```

Clear gestures bound to the component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIGestureEvent-clearGestures(): void--><!--Device-UIGestureEvent-clearGestures(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## removeGestureByTag

```TypeScript
removeGestureByTag(tag: string): void
```

Remove a gesture from a component that has been bound with a specific tag through a modifier.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIGestureEvent-removeGestureByTag(tag: string): void--><!--Device-UIGestureEvent-removeGestureByTag(tag: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tag | string | 是 | tag indicates the gesture's tag. |

