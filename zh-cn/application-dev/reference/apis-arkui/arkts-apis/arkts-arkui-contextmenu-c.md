# ContextMenu

在页面范围内关闭通过[bindContextMenu](../arkts-components/arkts-arkui-commonmethod-c.md#bindcontextmenu)属性绑定的菜单。

**起始版本：** 8

<!--Device-unnamed-declare class ContextMenu--><!--Device-unnamed-declare class ContextMenu-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## close

```TypeScript
static close()
```

可以通过该方法在页面范围内关闭通过[bindContextMenu](../arkts-components/arkts-arkui-commonmethod-c.md#bindcontextmenu)为组件绑定的菜单。
> **说明：**  
>  
> 从API version 18开始废弃，建议使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getContextMenuController](arkts-arkui-arkui-uicontext-uicontext-c.md#getcontextmenucontroller)获取  
> [ContextMenuController](arkts-arkui-uicontext.md)实例，再通过此实例调用替代方法  
> [close](arkts-arkui-arkui-uicontext-contextmenucontroller-c.md#close)。  
>  
> 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getContextMenuController](arkts-arkui-arkui-uicontext-uicontext-c.md#getcontextmenucontroller)来明确UI的执行上下文。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** close

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ContextMenu-static close()--><!--Device-ContextMenu-static close()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

