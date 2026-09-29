# TextContentControllerBase

```TypeScript
declare abstract class TextContentControllerBase
```

Represents the base controller for **TextInput**, **TextArea**, and **Search** components.

**Since:** 10

<!--Device-unnamed-declare abstract class TextContentControllerBase--><!--Device-unnamed-declare abstract class TextContentControllerBase-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addText

```TypeScript
addText(text: string, textOperationOptions?: TextContentControllerOptions): number
```

Inserts text at a specified position in the editable content. If no position is specified, the text is appended to the end of the existing content.

This API does not work when the text is being dragged.

`addText` only affects the UI performance within the application and does not affect the internal logic of the input method application. The preview text state is managed by the input method. Calling `addText`/`deleteText` at the application layer disrupts the state management of the input method. Therefore, avoid calling `addText` in the preview text state.

> **NOTE:** 
> 
> When the controller is not bound to a component or the component bound to the controller is released, this API
> does not take effect.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextContentControllerBase-addText(text: string, textOperationOptions?: TextContentControllerOptions): number--><!--Device-TextContentControllerBase-addText(text: string, textOperationOptions?: TextContentControllerOptions): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text to insert. |
| textOperationOptions | [TextContentControllerOptions](arkts-arkui-common-comp-textcontentcontrolleroptions-i.md) | No | Configuration options for inserting text, used to set parameters such as the insertion position. Pass this parameter when text needs to be inserted at a specified position. If not set, text is inserted at the end by default. |

**Return value:**

| Type | Description |
| --- | --- |
| number | New cursor position after insertion. |

## clearPreviewText

```TypeScript
clearPreviewText(): void
```

Notifies the input method to clear the current preview text.

> **NOTE:** 
> 
> When the controller is not bound to a component or the component bound to the controller is released, this API is
> not effective.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

<!--Device-TextContentControllerBase-clearPreviewText(): void--><!--Device-TextContentControllerBase-clearPreviewText(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## deleteBackward

```TypeScript
deleteBackward(): void
```

Deletes the character before the caret in the text input box bound to the base controller `controller`. If some text has been selected with the mouse or keyboard before this API is called, the selected text is deleted.

This API is not effective in the state of dragged text.

> **NOTE:** 
> 
> When the controller is not bound to a component or the component bound to the controller is released, this API is
> not effective.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextContentControllerBase-deleteBackward(): void--><!--Device-TextContentControllerBase-deleteBackward(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## deleteText

```TypeScript
deleteText(range?: TextRange): void
```

Deletes text within a specified range in the editable content.

This API does not work when the text is being dragged.

`deleteText` only affects the UI performance within the application and does not affect the internal logic of the input method application. The preview text state is managed by the input method. Calling `addText`/`deleteText` at the application layer disrupts the state management of the input method. Therefore, avoid calling `deleteText` in the preview text state.

> **NOTE:** 
> 
> When the controller is not bound to a component or the component bound to the controller is released, this API
> does not take effect.
> 
> **Differences from [deleteBackward](#deletebackward)**:
> 
> - deleteText supports range deletion and can delete text in any specified area; deleteBackward simulates the user deletion operation and deletes the character before the caret or the selected text.
> 
> - Avoid calling deleteText in the preview text state. deleteBackward is not supported in the preview text scenario.
> 
> - Select the API based on the deletion requirement: use deleteText to delete text in a specified range, and use deleteBackward to delete the character before the caret.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextContentControllerBase-deleteText(range?: TextRange): void--><!--Device-TextContentControllerBase-deleteText(range?: TextRange): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | No | Range of the text to delete, including the start position and end position of the text to delete.<br>The start position must be less than or equal to the end position; otherwise, the API call is invalid. A start position less than 0 is treated as 0, and an end position greater than the text length is treated as the text length. <br>If the deletion range is not specified, all text is deleted by default. If the start position of the text to delete is not specified, deletion starts from subscript 0 by default; if the end position of the text to delete is not specified, the end of the text is used as the deletion end point by default. |

## getCaretOffset

```TypeScript
getCaretOffset() : CaretOffset
```

Obtains the position information of the caret.

> **NOTE:** 
> 
> - If this API is called while the caret position is being updated in the current frame, this API does not take effect.
> 
> - In the Search component, the returned position information is the offset relative to the search icon in the Search component.
> 
> - In the Search component, when no text is entered, the return value contains the position information relative to the Search component.
> 
> - The position information in the return value is the position of the caret relative to the editable component.
> 
> - When the caret position cannot be obtained (for example, when [TextInputController](arkts-arkui-textinput-comp-textinputcontroller-c.md)is not bound to the [TextInput](arkts-arkui-textinput-comp.md) component), this API returns undefined.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextContentControllerBase-getCaretOffset() : CaretOffset--><!--Device-TextContentControllerBase-getCaretOffset() : CaretOffset-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [CaretOffset](arkts-arkui-common-comp-caretoffset-i.md) | Position of the caret relative to the text box.<br>If no component is bound to the controller or the component bound to the controller is released, **undefined** is returned. |

## getSelection

```TypeScript
getSelection(): TextRange
```

Obtains the current text selection range.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextContentControllerBase-getSelection(): TextRange--><!--Device-TextContentControllerBase-getSelection(): TextRange-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | Current text selection range, or cursor position if no text is selected.<br>If no component is bound to the controller or the component bound to the controller is released, **undefined** is returned. |

## getTextContentLineCount

```TypeScript
getTextContentLineCount() : number
```

Obtains the number of lines of the edited text.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextContentControllerBase-getTextContentLineCount() : number--><!--Device-TextContentControllerBase-getTextContentLineCount() : number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of lines of the edited text.<br>If no component is bound to the controller or the component bound to the controller is released, **undefined** is returned. |

## getTextContentRect

```TypeScript
getTextContentRect() : RectResult
```

Obtains the position of the edited text area relative to the component and its size. The unit of the return value is pixel.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-TextContentControllerBase-getTextContentRect() : RectResult--><!--Device-TextContentControllerBase-getTextContentRect() : RectResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [RectResult](arkts-arkui-common-comp-rectresult-i.md) | Position of the edited text area relative to the component and its size.<br>If no component is bound to the controller or the component bound to the controller is released, **undefined** is returned. |

## scrollToVisible

```TypeScript
scrollToVisible(range?: TextRange): void
```

Passes the start and end indexes to the bound text box components (**TextInput**, **TextArea**, and **Search**), and scrolls the text within the range to the visible area.

> **NOTE:** 
> 
> When the controller is not bound to a component or the component bound to the controller is released, this API is
> not effective.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextContentControllerBase-scrollToVisible(range?: TextRange): void--><!--Device-TextContentControllerBase-scrollToVisible(range?: TextRange): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | No | Text range to be scrolled to the visible area, including the start and end positions of the text.<br>The start position must be less than or equal to the end position. Otherwise, the API call is invalid. If the start position is less than 0, it is treated as the value **0**. If the end position is greater than the length of the entire text, it is treated as the length of the entire text. <br>If no range is specified, the entire text is used by default. If the start position is not specified, the default start position is 0. If the end position is not specified, the default end position is the length of the entire text. |

## setStyledPlaceholder

```TypeScript
setStyledPlaceholder(styledString: StyledString): void
```

Sets the placeholder text with the styled string, triggering binding or update.

> **NOTE:** 
> 
> When the controller is not bound to a component or the component bound to the controller is released, this API
> does not take effect.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-TextContentControllerBase-setStyledPlaceholder(styledString: StyledString): void--><!--Device-TextContentControllerBase-setStyledPlaceholder(styledString: StyledString): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| styledString | [StyledString](../arkts-apis/arkts-arkui-styledstring-c.md) | Yes | Sets the placeholder of the styled string. Its priority is higher than that of the plain text placeholder attribute.<br>The placeholder does not support styled string events, gestures, or hyperlink jumps. |
