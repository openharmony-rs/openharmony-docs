# getDragPreview

## getDragPreview

```TypeScript
function getDragPreview(): DragPreview
```

返回一个代表拖拽背板的对象。 > **说明：** > > 从API version 11开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_中的 > [getDragController]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_方法获取当前UI > 上下文关联的[DragController]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_对象。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 18

**替代接口：** ohos.arkui.UIContext.DragController#getDragPreview

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-dragController-function getDragPreview(): DragPreview--><!--Device-dragController-function getDragPreview(): DragPreview-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 一个代表拖拽背板的对象，提供背板样式设置的接口，在OnDrop和OnDragEnd回调中使用不生效。 |

