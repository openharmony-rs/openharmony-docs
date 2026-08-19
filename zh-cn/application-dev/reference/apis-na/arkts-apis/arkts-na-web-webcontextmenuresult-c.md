# WebContextMenuResult

Defines the context menu result, related to [WebContextMenuResult](#webcontextmenuresult) method.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class WebContextMenuResult--><!--Device-unnamed-export declare class WebContextMenuResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## closeContextMenu

```TypeScript
closeContextMenu(): void
```

When close context menu without other call in WebContextMenuResult, User should call this function to close menu

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-closeContextMenu(): void--><!--Device-WebContextMenuResult-closeContextMenu(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-constructor()--><!--Device-WebContextMenuResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## copy

```TypeScript
copy(): void
```

Executes the copy operation related to this context menu.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-copy(): void--><!--Device-WebContextMenuResult-copy(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## copyImage

```TypeScript
copyImage(): void
```

If WebContextMenuParam has image content, this function will copy image related to this context menu. If WebContextMenuParam has no image content, this function will do nothing.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-copyImage(): void--><!--Device-WebContextMenuResult-copyImage(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## cut

```TypeScript
cut(): void
```

Executes the cut operation related to this context menu.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-cut(): void--><!--Device-WebContextMenuResult-cut(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## paste

```TypeScript
paste(): void
```

Executes the paste operation related to this context menu. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:<br> Permissions need to be configured: ohos.permission.READ_PASTEBOARD. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-paste(): void--><!--Device-WebContextMenuResult-paste(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## pasteAndMatchStyle

```TypeScript
pasteAndMatchStyle(): void
```

Executes the paste and match style operation related to this context menu. &lt;p&gt;&lt;strong&gt;API Note&lt;/strong&gt;:<br> Permissions need to be configured: ohos.permission.READ_PASTEBOARD. &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-pasteAndMatchStyle(): void--><!--Device-WebContextMenuResult-pasteAndMatchStyle(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## redo

```TypeScript
redo(): void
```

Executes the redo operation related to this context menu.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-redo(): void--><!--Device-WebContextMenuResult-redo(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## requestPasswordAutoFill

```TypeScript
requestPasswordAutoFill(): void
```

Request to fill the password vault contents into the input field.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-requestPasswordAutoFill(): void--><!--Device-WebContextMenuResult-requestPasswordAutoFill(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## saveImage

```TypeScript
saveImage(): void
```

Performing the "Save As Image" operation associated with this context menu will trigger the download process.

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WebContextMenuResult-saveImage(): void--><!--Device-WebContextMenuResult-saveImage(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## selectAll

```TypeScript
selectAll(): void
```

Executes the selectAll operation related to this context menu.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-selectAll(): void--><!--Device-WebContextMenuResult-selectAll(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## undo

```TypeScript
undo(): void
```

Executes the undo operation related to this context menu.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebContextMenuResult-undo(): void--><!--Device-WebContextMenuResult-undo(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

