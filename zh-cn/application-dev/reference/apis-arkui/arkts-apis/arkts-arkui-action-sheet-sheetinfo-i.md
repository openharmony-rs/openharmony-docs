# SheetInfo

弹窗中的选项内容，每一项支持设置文本、图标以及选中的回调。

**起始版本：** 8

<!--Device-unnamed-interface SheetInfo--><!--Device-unnamed-interface SheetInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: VoidCallback
```

选项选中的回调。

**类型：** VoidCallback

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SheetInfo-action: VoidCallback--><!--Device-SheetInfo-action: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string | Resource
```

选项的图标，默认无图标显示。

string格式可用于加载网络图片和本地图片，常用于加载网络图片。当使用相对路径引用本地图片时，例如Image("common/test.jpg")。

**类型：** string | Resource

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SheetInfo-icon?: string | Resource--><!--Device-SheetInfo-icon?: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: string | Resource
```

选项的文本内容。

文本超长时会触发滚动条。

**类型：** string | Resource

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SheetInfo-title: string | Resource--><!--Device-SheetInfo-title: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

