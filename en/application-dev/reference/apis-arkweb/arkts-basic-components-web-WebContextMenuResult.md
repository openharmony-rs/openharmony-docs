# Class (WebContextMenuResult)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @zhufenghao-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=eb5077b0e0ddac08df4dbb76ee1a57a53454c9c0 translatedAt=2026-08-07T04:42:10.549Z pushedAt=2026-08-07T08:12:40.391Z -->

WebContextMenuResult is a class in the ArkWeb component used to handle context menu events (triggered by long-pressing a page element or right-clicking). It provides developers with a set of menu operation execution capabilities, including text editing operations (copy, paste, cut, select all, undo, redo, paste and match style), image operations (copy image, save image), menu control (close menu), and password auto-fill.

Developers typically use WebContextMenuResult when they need to customize the context menu behavior of the Web component. Obtain a WebContextMenuResult instance through the **onContextMenuShow** event callback, and use the menu context information provided by **WebContextMenuParam** to determine the user operation scenario and call the corresponding response method, thereby implementing custom menu interaction logic. If the developer does not perform any menu response operation, the **closeContextMenu** method must be called to close the menu.

For details about the sample code, see [onContextMenuShow<sup>9+</sup>](./arkts-basic-components-web-events.md#oncontextmenushow9).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 9.
>
> - The sample effect is subject to the actual device.

## constructor<sup>9+</sup>

constructor()

Constructs a **WebContextMenuResult** object.

**System capability**: SystemCapability.Web.Webview.Core

## closeContextMenu<sup>9+</sup>

closeContextMenu(): void

Closes this context menu. This API must be called when no operations in **WebContextMenuResult** are performed.

**Calling notes**

- After calling other methods of WebContextMenuResult (such as copy, paste, and cut) to complete an operation, this method should be called to close the menu.

- If no other menu operations need to be performed, this method should also be called in a timely manner to close the menu.

- Failure to call this method may result in menu resources not being properly released.

**System capability**: SystemCapability.Web.Webview.Core

## copyImage<sup>9+</sup>

copyImage(): void

When **WebContextMenuParam** contains image content, this method is used to copy the image to the clipboard. Starting from API version 24, copying canvas images is supported. If you need to save the image to a local file, use the saveImage() method.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.

**System capability**: SystemCapability.Web.Webview.Core

## copy<sup>9+</sup>

copy(): void

Performs the copy text operation.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.

**System capability**: SystemCapability.Web.Webview.Core

## paste<sup>9+</sup>

paste(): void

Performs the paste operation, preserving the original format. If you need to paste plain text and match the target format, use the pasteAndMatchStyle() method.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.
>
> The permission [ohos.permission.READ_PASTEBOARD](../../security/AccessToken/restricted-permissions.md#ohospermissionread_pasteboard) must be declared.

**System capability**: SystemCapability.Web.Webview.Core

## cut<sup>9+</sup>

cut(): void

Performs the cut operation.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.

**System capability**: SystemCapability.Web.Webview.Core

## selectAll<sup>9+</sup>

selectAll(): void

Performs the select all operation.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.

**System capability**: SystemCapability.Web.Webview.Core

## undo<sup>20+</sup>

undo(): void

Performs the undo operation, which undoes the last editing operation.

**Coordination**

- Used together with the redo() method. After undo() is called, redo() can be used to re-execute the revoked operation.

- If the user has not performed an undo operation, the redo() method cannot be used.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.

**System capability**: SystemCapability.Web.Webview.Core

## redo<sup>20+</sup>

redo(): void

Performs the redo operation, which re-executes the revoked operation.

**Coordination**

- Used together with the undo() method. After undo() is called, redo() can be used to re-execute the revoked operation.

- If the user has not performed an undo operation, the redo() method cannot be used.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.

**System capability**: SystemCapability.Web.Webview.Core

## pasteAndMatchStyle<sup>20+</sup>

pasteAndMatchStyle(): void

Performs the paste operation related to this context menu. The pasted content matches the target format and is presented as plain text.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.
>
> The permission [ohos.permission.READ_PASTEBOARD](../../security/AccessToken/restricted-permissions.md#ohospermissionread_pasteboard) must be declared.

**System capability**: SystemCapability.Web.Webview.Core

## requestPasswordAutoFill<sup>23+</sup>

requestPasswordAutoFill(): void

Requests the username or password data in the password vault to be automatically filled in the current focused text box.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.

**System capability**: SystemCapability.Web.Webview.Core

## saveImage<sup>24+</sup>

saveImage(): void

Saves the image related to this context menu. Calling this method triggers the download process.

> **NOTE**
>
> After the operation is complete, [closeContextMenu](#closecontextmenu9) should be called to close the menu. Failure to do so may result in menu resources not being properly released.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Web.Webview.Core
<!--no_check-->