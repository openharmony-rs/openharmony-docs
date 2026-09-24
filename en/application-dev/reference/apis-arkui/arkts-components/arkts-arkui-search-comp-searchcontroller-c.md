# SearchController

```TypeScript
declare class SearchController extends TextContentControllerBase
```

The controller for the **Search** component inherits from [TextContentControllerBase](arkts-arkui-common-comp-textcontentcontrollerbase-c.md). The APIs involved are as follows:<!--Del--> system API [getText](arkts-arkui-common-comp-textcontentcontrollerbase-c-sys.md#gettext) and other APIs like<!--DelEnd--> [getTextContentRect](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#gettextcontentrect), [getTextContentLineCount](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#gettextcontentlinecount), [getCaretOffset](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#getcaretoffset), [addText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#addtext), [deleteText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#deletetext), [getSelection](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#getselection), [clearPreviewText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#clearpreviewtext), [setStyledPlaceholder](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#setstyledplaceholder), and [deleteBackward](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#deletebackward).

## Objects to Import

```ts
controller: SearchController = new SearchController();
```

**Inheritance/Implementation:** SearchController extends [TextContentControllerBase](arkts-arkui-common-comp-textcontentcontrollerbase-c.md)

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## caretPosition

```TypeScript
caretPosition(value: number): void
```

Sets the position of the caret.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Length from the start of the character string to the position where the caret is located.<br>Values less than 0 are treated as **0**. Values greater than the string length are treated as the string length. |

## constructor

```TypeScript
constructor()
```

A constructor used to create a **SearchController** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

Sets the text selection range and highlights the selected text when the component is focused. This API works only when the value of **selectionStart** is less than that of **selectionEnd**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the text selection range. The start position of text in the text box is 0.<br>A value less than 0 is handled as **0**. A value greater than the maximum text length is handled as the maximum text length.<br> |
| selectionEnd | number | Yes | End position of the text selection range.<br>A value less than 0 is handled as **0**. A value greater than the maximum text length is handled as the maximum text length.<br> |
| options | [SelectionOptions](arkts-arkui-common-comp-selectionoptions-i.md) | No | Configuration options for text selection.<br>Default value: **MenuPolicy.DEFAULT** |

## stopEditing

```TypeScript
stopEditing(): void
```

Exits the editing state.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
