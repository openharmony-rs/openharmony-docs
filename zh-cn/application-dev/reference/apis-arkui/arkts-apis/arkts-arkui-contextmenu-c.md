# ContextMenu

在页面范围内关闭通过 [bindContextMenu]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 属性绑定的菜单。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

<!--Device-unnamed-declare class ContextMenu--><!--Device-unnamed-declare class ContextMenu-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## close

```TypeScript
static close()
```

在页面范围内关闭通过 [bindContextMenu]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 绑定的菜单。常用于页面跳转、拖拽开始等需要主动关闭已显示菜单的交互场景。 > **说明：** > > 从API version 18开始废弃，建议使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_中的 > [getContextMenuController]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_获取 > [ContextMenuController]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_实例，再通过此实例调用替代方法 > [close]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_。 > > 从API version 12开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_中的 > [getContextMenuController]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_来明确UI的执行上下文。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 18

**替代接口：** ohos.arkui.UIContext.ContextMenuController#close

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenu-static close()--><!--Device-ContextMenu-static close()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

