# UIGestureEvent

用于设置组件绑定的手势。

**起始版本：** 12

<!--Device-unnamed-declare interface UIGestureEvent--><!--Device-unnamed-declare interface UIGestureEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="addgesture"></a>
## addGesture

```TypeScript
addGesture<T>(gesture: GestureHandler<T>, priority?: GesturePriority, mask?: GestureMask): void
```

添加手势。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIGestureEvent-addGesture<T>(gesture: GestureHandler<T>, priority?: GesturePriority, mask?: GestureMask): void--><!--Device-UIGestureEvent-addGesture<T>(gesture: GestureHandler<T>, priority?: GesturePriority, mask?: GestureMask): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | [GestureHandler](../arkts-apis/arkts-arkui-gesturehandler-c.md)&lt;T&gt; | 是 | 手势处理器对象。 |
| priority | [GesturePriority](../arkts-apis/arkts-arkui-gesturepriority-e.md) | 否 | 绑定手势的优先级。<br>默认值：GesturePriority.NORMAL |
| mask | [GestureMask](../arkts-apis/arkts-arkui-gesturemask-e.md) | 否 | 事件响应设置。<br>默认值：GestureMask.Normal |

<a id="addparallelgesture"></a>
## addParallelGesture

```TypeScript
addParallelGesture<T>(gesture: GestureHandler<T>, mask?: GestureMask): void
```

绑定可与子组件手势同时触发的手势。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIGestureEvent-addParallelGesture<T>(gesture: GestureHandler<T>, mask?: GestureMask): void--><!--Device-UIGestureEvent-addParallelGesture<T>(gesture: GestureHandler<T>, mask?: GestureMask): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gesture | [GestureHandler](../arkts-apis/arkts-arkui-gesturehandler-c.md)&lt;T&gt; | 是 | 手势处理器对象。 |
| mask | [GestureMask](../arkts-apis/arkts-arkui-gesturemask-e.md) | 否 | 事件响应设置。<br>默认值：GestureMask.Normal |

<a id="cleargestures"></a>
## clearGestures

```TypeScript
clearGestures(): void
```

清除该组件上通过modifier绑定的所有手势。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIGestureEvent-clearGestures(): void--><!--Device-UIGestureEvent-clearGestures(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="removegesturebytag"></a>
## removeGestureByTag

```TypeScript
removeGestureByTag(tag: string): void
```

移除该组件上通过modifier绑定的设置为指定标志的手势。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UIGestureEvent-removeGestureByTag(tag: string): void--><!--Device-UIGestureEvent-removeGestureByTag(tag: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tag | string | 是 | 手势处理器标志。 |

