# WebContextMenuResult

WebContextMenuResult is a class in the ArkWeb component used to handle context menu events (triggered by long- pressing a page element or right-clicking). It provides developers with a set of menu operation execution capabilities, including text editing operations (copy, paste, cut, select all, undo, redo, paste and match style), image operations (copy image, save image), menu control (close menu), and password auto-fill.

Developers typically use WebContextMenuResult when they need to customize the context menu behavior of the Web component. Obtain a WebContextMenuResult instance through the **onContextMenuShow** event callback, and use the menu context information provided by **WebContextMenuParam** to determine the user operation scenario and call the corresponding response method, thereby implementing custom menu interaction logic. If the developer does not perform any menu response operation, the **closeContextMenu** method must be called to close the menu.

For details about the sample code, see [onContextMenuShow&lt;sup&gt;9+&lt;/sup&gt;](arkts-arkweb-web-comp-attribute.md#oncontextmenushow).

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## closeContextMenu

```TypeScript
closeContextMenu(): void
```

Closes this context menu. This API must be called when no operations in **WebContextMenuResult** are performed.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **WebContextMenuResult** object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## copy

```TypeScript
copy(): void
```

Performs the copy text operation.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## copyImage

```TypeScript
copyImage(): void
```

When **WebContextMenuParam** contains image content, this method is used to copy the image to the clipboard. Starting from API version 24, copying canvas images is supported. If you need to save the image to a local file, use the saveImage() method.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## cut

```TypeScript
cut(): void
```

Performs the cut operation.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## paste

```TypeScript
paste(): void
```

Performs the paste operation, preserving the original format. If you need to paste plain text and match the target format, use the pasteAndMatchStyle() method.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.
> 
> The permission
> [ohos.permission.READ_PASTEBOARD](../../../security/AccessToken/restricted-permissions.md#ohospermissionread_pasteboard)
> must be declared.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## pasteAndMatchStyle

```TypeScript
pasteAndMatchStyle(): void
```

Performs the paste operation related to this context menu. The pasted content matches the target format and is presented as plain text.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.
> 
> The permission
> [ohos.permission.READ_PASTEBOARD](../../../security/AccessToken/restricted-permissions.md#ohospermissionread_pasteboard)
> must be declared.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## redo

```TypeScript
redo(): void
```

Performs the redo operation, which re-executes the revoked operation.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## requestPasswordAutoFill

```TypeScript
requestPasswordAutoFill(): void
```

Requests the username or password data in the password vault to be automatically filled in the current focused text box.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.

**Since:** 23

**System capability:** SystemCapability.Web.Webview.Core

## saveImage

```TypeScript
saveImage(): void
```

Saves the image related to this context menu. Calling this method triggers the download process.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

## selectAll

```TypeScript
selectAll(): void
```

Performs the select all operation.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## undo

```TypeScript
undo(): void
```

Performs the undo operation, which undoes the last editing operation.

> **NOTE:** 
> 
> After the operation is complete, [closeContextMenu](#closecontextmenu) should be called
> to close the menu. Failure to do so may result in menu resources not being properly released.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core
