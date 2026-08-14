# MenuOptions

配置弹出菜单的参数，继承自[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md#ContextMenuOptions)。

**继承/实现关系：** MenuOptions extends [ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md#ContextMenuOptions)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare interface MenuOptions--><!--Device-unnamed-declare interface MenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

是否在子窗口显示菜单。 true：在子窗口显示菜单；false：不在子窗显示菜单。 默认值：2in1设备上为true，其他设备为false。 **说明：** 仅对2in1设备生效。

**类型：** boolean

**默认值：** true for 2-in-1 devices [since 12]

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuOptions-showInSubWindow?: boolean--><!--Device-MenuOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

菜单标题。 **说明：** 仅在content设置为Array&lt;[MenuElement](arkts-arkui-menuelement-i.md#MenuElement)&gt; 时生效。

**类型：** ResourceStr

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuOptions-title?: ResourceStr--><!--Device-MenuOptions-title?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

