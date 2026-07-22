# MenuOptions

菜单项的信息，继承自[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)。

**继承/实现关系：** MenuOptions extends [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)

**起始版本：** 10

<!--Device-unnamed-declare interface MenuOptions extends ContextMenuOptions--><!--Device-unnamed-declare interface MenuOptions extends ContextMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

是否在子窗口显示菜单。

true：在子窗口显示菜单；false：不在子窗显示菜单。

默认值：2in1设备上为true，其他设备为false。

**说明：**

仅对2in1设备生效。

**类型：** boolean

**默认值：** true for 2-in-1 devices [since 12]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuOptions-showInSubWindow?: boolean--><!--Device-MenuOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

菜单标题。

**说明：**

仅在content设置为Array&lt;[MenuElement](arkts-arkui-menuelement-i.md)&gt; 时生效。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuOptions-title?: ResourceStr--><!--Device-MenuOptions-title?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

