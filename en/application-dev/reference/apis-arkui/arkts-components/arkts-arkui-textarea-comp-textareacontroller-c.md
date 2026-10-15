# TextAreaController

```TypeScript
declare class TextAreaController extends TextContentControllerBase
```

The controller of the TextArea component inherits from [TextContentControllerBase](arkts-arkui-common-comp-textcontentcontrollerbase-c.md). The involved APIs include [getTextContentRect](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#gettextcontentrect), [getTextContentLineCount](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#gettextcontentlinecount), [getCaretOffset](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#getcaretoffset), [addText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#addtext), [deleteText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#deletetext), [getSelection](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#getselection), [clearPreviewText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#clearpreviewtext), [setStyledPlaceholder](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#setstyledplaceholder), [deleteBackward](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#deletebackward), [scrollToVisible](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#scrolltovisible)<!--Del-->, and the system API [getText](arkts-arkui-common-comp-textcontentcontrollerbase-c-sys.md#gettext)<!--DelEnd-->.

**Inheritance/Implementation:** TextAreaController extends [TextContentControllerBase](arkts-arkui-common-comp-textcontentcontrollerbase-c.md)

**Since:** 8

<!--Device-unnamed-declare class TextAreaController extends TextContentControllerBase--><!--Device-unnamed-declare class TextAreaController extends TextContentControllerBase-End-->

**System capability:** 
- API version 10 and later: SystemCapability.ArkUI.ArkUI.Full

## Import Object

```ts
controller: TextAreaController = new TextAreaController();
```

## caretPosition

```TypeScript
caretPosition(value: number): void
```

Sets the position of the input cursor.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaController-caretPosition(value: number): void--><!--Device-TextAreaController-caretPosition(value: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Length of the characters from the start of the string to the cursor position.<br>If value is less than 0, it is processed as 0. If value is greater than the string length, it is processed as the string length. |

## constructor

```TypeScript
constructor()
```

Constructor of TextAreaController.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaController-constructor()--><!--Device-TextAreaController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

Sets the text selection area and highlights it when the component is focused. The text is selected and highlighted only when selectionStart is less than selectionEnd.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void--><!--Device-TextAreaController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the text selection area. The start position of the text in the text box is 0.<br>If selectionStart is less than 0, it is processed as 0. If selectionStart is greater than the maximum text length, it is processed as the maximum text length. <br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| selectionEnd | number | Yes | End position of the text selection area.<br>If selectionEnd is less than 0, it is processed as 0. If selectionEnd is greater than the maximum text length, it is processed as the maximum text length. <br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| options | [SelectionOptions](arkts-arkui-common-comp-selectionoptions-i.md) | No | Configuration for the selected text.<br>Default value: MenuPolicy.DEFAULT <br>**Atomic service API:** Since API version 12, this API is supported in atomic services.<br>**Since:** 12 |

## stopEditing

```TypeScript
stopEditing(): void
```

Exits the editing state.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextAreaController-stopEditing(): void--><!--Device-TextAreaController-stopEditing(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
