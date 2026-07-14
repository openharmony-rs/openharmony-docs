# DragController

提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。

> **说明：**
>
> 以下API需先使用UIContext中的[getDragController()](arkts-arkui-uicontext-c.md#getdragcontroller-1)方法获取DragController实例，再通过此实例调用对应方法。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## interruptFollowHandMorphDropAnimation

```TypeScript
interruptFollowHandMorphDropAnimation(): boolean
```

中断待执行的跟手变形落位动效，并立即触发其收尾流程。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回中断结果。<br>返回true表示中断成功，返回false表示当前不存在待中断的跟手变形落位动效。 |

