# SearchController

```TypeScript
declare class SearchController extends TextContentControllerBase
```

The controller of the Search component inherits from [TextContentControllerBase](arkts-arkui-common-comp-textcontentcontrollerbase-c.md), and the involved APIs include [getTextContentRect](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#gettextcontentrect), [getTextContentLineCount](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#gettextcontentlinecount), [getCaretOffset](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#getcaretoffset), [addText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#addtext), [deleteText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#deletetext), [getSelection](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#getselection), [clearPreviewText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#clearpreviewtext), [setStyledPlaceholder](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#setstyledplaceholder), [deleteBackward](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#deletebackward), [scrollToVisible](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#scrolltovisible)<!--Del-->and the system API [getText](arkts-arkui-common-comp-textcontentcontrollerbase-c-sys.md#gettext)<!--DelEnd-->.

## Import Object

```ts
controller: SearchController = new SearchController();
```

**Inheritance/Implementation:** SearchController extends [TextContentControllerBase](arkts-arkui-common-comp-textcontentcontrollerbase-c.md)

**Since:** 8

<!--Device-unnamed-declare class SearchController extends TextContentControllerBase--><!--Device-unnamed-declare class SearchController extends TextContentControllerBase-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: number): void
```

Sets the position of the input cursor.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchController-caretPosition(value: number): void--><!--Device-SearchController-caretPosition(value: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Length from the start of the string to the cursor position.&lt;/br&gt;When value is less than 0, it is processed as 0. When value is greater than the string length, it is processed as the string length. |

## constructor

```TypeScript
constructor()
```

Constructor of SearchController.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchController-constructor()--><!--Device-SearchController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

When the component is in focus, this API is called to set the text selection area and highlight it. The text is selected and highlighted only when selectionStart is less than selectionEnd.

> **NOTE:** 
> 
> - If selectionStart or selectionEnd is set to undefined, it is treated as 0.
> 
> - If selectionMenuHidden is set to true or the device is a 2-in-1 device, no menu is displayed when setTextSelection is called, even if options is set to MenuPolicy.SHOW.
> 
> - If the selected text contains emojis, an emoji is selected when its start position falls within the set text selection area.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SearchController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void--><!--Device-SearchController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the text selection area. The start position of the text in the text box is 0.<br>If selectionStart is less than 0, it is treated as 0. If selectionStart is greater than the maximum text length, it is treated as the maximum text length. <br> |
| selectionEnd | number | Yes | End position of the text selection area.<br>If selectionEnd is less than 0, it is treated as 0. If selectionEnd is greater than the maximum text length, it is treated as the maximum text length. <br> |
| options | [SelectionOptions](arkts-arkui-common-comp-selectionoptions-i.md) | No | Configuration for the selected text.<br>Default value: MenuPolicy.DEFAULT. |

## stopEditing

```TypeScript
stopEditing(): void
```

Exits the editing state.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SearchController-stopEditing(): void--><!--Device-SearchController-stopEditing(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
