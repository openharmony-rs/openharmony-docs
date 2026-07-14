# getDragPreview

## getDragPreview

```TypeScript
function getDragPreview(): DragPreview
```

返回一个代表拖拽背板的对象。

> **说明：**
>
> 从API version 11开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的
> [getDragController](arkts-arkui-uicontext-c.md#getdragcontroller-1)方法获取当前UI
> 上下文关联的[DragController](arkts-arkui-dragcontroller-c.md)对象。

**起始版本：** 11

**废弃版本：** 18

**替代接口：** getDragPreview

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DragPreview | 一个代表拖拽背板的对象，提供背板样式设置的接口，在OnDrop和OnDragEnd回调中使用不生效。 |

