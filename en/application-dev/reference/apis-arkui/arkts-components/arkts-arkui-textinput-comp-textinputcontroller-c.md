# TextInputController

```TypeScript
declare class TextInputController extends TextContentControllerBase
```

The controller of the TextInput component inherits from [TextContentControllerBase](arkts-arkui-common-comp-textcontentcontrollerbase-c.md). The involved APIs include [getTextContentRect](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#gettextcontentrect), [getTextContentLineCount](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#gettextcontentlinecount), [getCaretOffset](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#getcaretoffset), [addText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#addtext), [deleteText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#deletetext), [getSelection](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#getselection), [clearPreviewText](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#clearpreviewtext), [setStyledPlaceholder](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#setstyledplaceholder), [deleteBackward](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#deletebackward), [scrollToVisible](arkts-arkui-common-comp-textcontentcontrollerbase-c.md#scrolltovisible)<!--Del-->, and the system API [getText](arkts-arkui-common-comp-textcontentcontrollerbase-c-sys.md#gettext)<!--DelEnd-->.

**Inheritance/Implementation:** TextInputController extends [TextContentControllerBase](arkts-arkui-common-comp-textcontentcontrollerbase-c.md)

**Since:** 8

<!--Device-unnamed-declare class TextInputController extends TextContentControllerBase--><!--Device-unnamed-declare class TextInputController extends TextContentControllerBase-End-->

**System capability:** 
- API version 10 and later: SystemCapability.ArkUI.ArkUI.Full

## Imported Object

```ts
controller: TextInputController = new TextInputController();
```

## caretPosition

```TypeScript
caretPosition(value: number): void
```

Sets the position of the input cursor. If the value is less than 0, it is set to 0. If the value is greater than the text length, the cursor is displayed at the end of the text.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputController-caretPosition(value: number): void--><!--Device-TextInputController-caretPosition(value: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Character length from the start of the string to the cursor position. |

## constructor

```TypeScript
constructor()
```

Constructor of TextInputController.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputController-constructor()--><!--Device-TextInputController-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

Sets the text selection region and highlights it.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void--><!--Device-TextInputController-setTextSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the text selection region. The start position of the text in the text box is 0. If selectionStart is less than 0, it is processed as 0. If selectionStart is greater than the text length, it is processed as the text length. |
| selectionEnd | number | Yes | End position of the text selection region. If selectionEnd is less than 0, it is processed as 0. If selectionEnd is greater than the text length, it is processed as the text length. |
| options | [SelectionOptions](arkts-arkui-common-comp-selectionoptions-i.md) | No | Configuration for the selected text, used to control the display policy of the text selection menu.<br>The configuration item includes menuPolicy, which specifies the menu display mode: MenuPolicy.DEFAULT indicates that the menu is displayed according to the system default behavior; MenuPolicy.SHOW indicates that the menu is forcibly displayed; MenuPolicy.HIDE indicates that the menu is forcibly hidden. <br>Default value: MenuPolicy.DEFAULT <br>Since API version 12, the options parameter in this API is supported in atomic services.<br>**Since:** 12 |

## stopEditing

```TypeScript
stopEditing(): void
```

Exits the editing state.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextInputController-stopEditing(): void--><!--Device-TextInputController-stopEditing(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
