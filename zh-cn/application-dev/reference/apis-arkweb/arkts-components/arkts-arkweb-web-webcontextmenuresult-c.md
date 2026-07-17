# WebContextMenuResult

Defines the context menu result, related to {@link WebContextMenuResult} method.

**起始版本：** 9

<!--Device-unnamed-declare class WebContextMenuResult--><!--Device-unnamed-declare class WebContextMenuResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## closeContextMenu

```TypeScript
closeContextMenu(): void
```

在WebContextMenuResult中无其他调用且需要关闭上下文菜单时，开发者需调用此函数关闭菜单。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-closeContextMenu(): void--><!--Device-WebContextMenuResult-closeContextMenu(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

WebContextMenuResult的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-constructor()--><!--Device-WebContextMenuResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## copy

```TypeScript
copy(): void
```

执行与此上下文菜单关联的复制操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-copy(): void--><!--Device-WebContextMenuResult-copy(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## copyImage

```TypeScript
copyImage(): void
```

若WebContextMenuParam包含图片内容，该函数将复制当前上下文菜单对应的图片。若WebContextMenuParam不包含图片内容，则该函数不执行任何操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-copyImage(): void--><!--Device-WebContextMenuResult-copyImage(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## cut

```TypeScript
cut(): void
```

执行与此上下文菜单关联的剪切操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-cut(): void--><!--Device-WebContextMenuResult-cut(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## paste

```TypeScript
paste(): void
```

执行与此上下文菜单关联的粘贴操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-paste(): void--><!--Device-WebContextMenuResult-paste(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## pasteAndMatchStyle

```TypeScript
pasteAndMatchStyle(): void
```

执行与此上下文菜单关联的粘贴并匹配样式操作。

**起始版本：** 20

<!--Device-WebContextMenuResult-pasteAndMatchStyle(): void--><!--Device-WebContextMenuResult-pasteAndMatchStyle(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## redo

```TypeScript
redo(): void
```

执行与此上下文菜单关联的重做操作。

**起始版本：** 20

<!--Device-WebContextMenuResult-redo(): void--><!--Device-WebContextMenuResult-redo(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## requestPasswordAutoFill

```TypeScript
requestPasswordAutoFill(): void
```

请求将密码保险箱内容填充到输入框中。

**起始版本：** 23

<!--Device-WebContextMenuResult-requestPasswordAutoFill(): void--><!--Device-WebContextMenuResult-requestPasswordAutoFill(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## saveImage

```TypeScript
saveImage(): void
```

执行与此上下文菜单关联的“另存为图像”操作将触发下载过程。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebContextMenuResult-saveImage(): void--><!--Device-WebContextMenuResult-saveImage(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## selectAll

```TypeScript
selectAll(): void
```

执行与此上下文菜单关联的全选操作。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebContextMenuResult-selectAll(): void--><!--Device-WebContextMenuResult-selectAll(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## undo

```TypeScript
undo(): void
```

执行与此上下文菜单关联的撤销操作。

**起始版本：** 20

<!--Device-WebContextMenuResult-undo(): void--><!--Device-WebContextMenuResult-undo(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

