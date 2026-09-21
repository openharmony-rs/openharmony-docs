# MenuOptions

```TypeScript
declare interface MenuOptions extends ContextMenuOptions
```

配置弹出菜单的参数，继承自[ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)。

**继承/实现关系：** MenuOptions extends [ContextMenuOptions](arkts-arkui-common-comp-contextmenuoptions-i.md)

**起始版本：** 10

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

**默认值：** 
- API版本12+：true for 2-in-1 devices

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

菜单标题。

**说明：** 

仅在content设置为Array&lt;[MenuElement](arkts-arkui-common-comp-menuelement-i.md)&gt; 时生效。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
