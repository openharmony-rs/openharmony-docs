# SelectionMenuOptionsExt

自定义菜单扩展项。

**起始版本：** 13

**系统能力：** SystemCapability.Web.Webview.Core

## menuType

```TypeScript
menuType?: MenuType
```

自定义选择菜单类型。

默认值：`MenuType.SELECTION_MENU`。

从API version 20起，`MenuType.PREVIEW_MENU`支持超链接预览。

**类型：** MenuType

**起始版本：** 13

**系统能力：** SystemCapability.Web.Webview.Core

## onAppear

```TypeScript
onAppear?: Callback<void>
```

自定义选择菜单弹出时回调。

**类型：** Callback<void>

**起始版本：** 13

**系统能力：** SystemCapability.Web.Webview.Core

## onDisappear

```TypeScript
onDisappear?: Callback<void>
```

自定义选择菜单关闭时回调。

**类型：** Callback<void>

**起始版本：** 13

**系统能力：** SystemCapability.Web.Webview.Core

## onMenuHide

```TypeScript
onMenuHide?: Callback<void>
```

自定义选择菜单隐藏时回调。

**类型：** Callback<void>

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

## onMenuShow

```TypeScript
onMenuShow?: Callback<void>
```

自定义选择菜单显示时回调。

**类型：** Callback<void>

**起始版本：** 21

**系统能力：** SystemCapability.Web.Webview.Core

## preview

```TypeScript
preview?: CustomBuilder
```

自定义选择菜单的预览内容样式，未配置时无预览内容。

**类型：** CustomBuilder

**起始版本：** 13

**系统能力：** SystemCapability.Web.Webview.Core

## previewMenuOptions

```TypeScript
previewMenuOptions?: PreviewMenuOptions
```

自定义选择预览菜单选项。

**类型：** PreviewMenuOptions

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

