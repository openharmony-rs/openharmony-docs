# Text Box Component Common APIs
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=976793f1477a1ea1d1147f29cf593c7a491f596e translatedAt=2026-09-02T12:10:24.160Z -->

Provides capabilities for the [TextInput](ts-basic-components-textinput.md) and [TextArea](ts-basic-components-textarea.md) components to obtain text and cursor information, insert and delete text, set the counter, and configure text decoration lines. This is applicable to scenarios where the text content and cursor position of an input box need to be controlled programmatically.

Provides capabilities for the [Search](ts-basic-components-search.md) component to obtain text and cursor information, insert and delete text, and configure text decoration lines.

> **NOTE**
>
> - This feature is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## TextContentControllerBase

Represents the base controller for **TextInput**, **TextArea**, and **Search** components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### getTextContentRect

getTextContentRect(): RectResult

Obtains the position of the edited text area relative to the component and its size. The unit of the return value is pixel.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type      | Description      |
| -------------------  | -------- |
| [RectResult](ts-universal-attributes-on-child-touch-test.md#rectresult) | Position of the edited text area relative to the component and its size.<br>If no component is bound to the controller or the component bound to the controller is released, **undefined** is returned.|

> **NOTE**
>
> - If no text is entered, the return value contains the position information, but the size is 0.
> - The position information is the offset of the first character relative to the editable area.
> - For the **Search** component, the returned position information is the offset of the first character relative to the search icon in the component.
> - If there is input, the width in the return value is the fixed width of the editable area.

### getTextContentLineCount

getTextContentLineCount(): number

Obtains the number of lines of the edited text.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type | Description      |
| ----- | -------- |
| number| Number of lines of the edited text.<br>If no component is bound to the controller or the component bound to the controller is released, **undefined** is returned.|

### getCaretOffset<sup>11+</sup>

getCaretOffset(): CaretOffset

Obtains the position information of the caret.

> **NOTE**
>
> - If this API is called while the caret position is being updated in the current frame, this API does not take effect.
> - In the Search component, the returned position information is the offset relative to the search icon in the Search component.
> - In the Search component, when no text is entered, the return value contains the position information relative to the Search component.
> - The position information in the return value is the position of the caret relative to the editable component.
> - When the caret position cannot be obtained (for example, when [TextInputController](ts-basic-components-textinput.md#textinputcontroller8) is not bound to the [TextInput](ts-basic-components-textinput.md) component), this API returns undefined.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                     | Description              |
| ----------------------- | ---------------- |
| [CaretOffset](#caretoffset11) | Position of the caret relative to the text box.<br>If no component is bound to the controller or the component bound to the controller is released, **undefined** is returned.|

### addText<sup>15+</sup>

addText(text: string, textOperationOptions?: TextContentControllerOptions): number

Inserts text at a specified position in the editable content. If no position is specified, the text is appended to the end of the existing content.

This API does not work when the text is being dragged.

`addText` only affects the UI performance within the application and does not affect the internal logic of the input method application. The preview text state is managed by the input method. Calling `addText`/`deleteText` at the application layer disrupts the state management of the input method. Therefore, avoid calling `addText` in the preview text state.

> **NOTE**
>
> When the controller is not bound to a component or the component bound to the controller is released, this API does not take effect.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| text | string | Yes   | Text to insert.|
| textOperationOptions   | [TextContentControllerOptions](#textcontentcontrolleroptions15) | No    | Configuration options for inserting text, used to set parameters such as the insertion position. Pass this parameter when text needs to be inserted at a specified position. If not set, text is inserted at the end by default. |

**Return value**

| Type | Description      |
| ----- | -------- |
| number| New cursor position after insertion.|

### setStyledPlaceholder<sup>22+</sup>

setStyledPlaceholder(styledString: StyledString): void

Sets the placeholder text with the styled string, triggering binding or update.

> **NOTE**
>
> When the controller is not bound to a component or the component bound to the controller is released, this API does not take effect.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| styledString | [StyledString](ts-universal-styled-string.md#styledstring) | Required | Sets the placeholder of the styled string. Its priority is higher than that of the plain text placeholder attribute.<br>The placeholder does not support styled string events, gestures, or hyperlink jumps.|

### deleteText<sup>15+</sup>

deleteText(range?: TextRange): void

Deletes text within a specified range in the editable content.

This API does not work when the text is being dragged.

`deleteText` only affects the UI performance within the application and does not affect the internal logic of the input method application. The preview text state is managed by the input method. Calling `addText`/`deleteText` at the application layer disrupts the state management of the input method. Therefore, avoid calling `deleteText` in the preview text state.

> **NOTE**
>
> When the controller is not bound to a component or the component bound to the controller is released, this API does not take effect.

**Differences from [deleteBackward](#deletebackward23)**
- deleteText supports range deletion and can delete text in any specified area; deleteBackward simulates the user deletion operation and deletes the character before the caret or the selected text.
- Avoid calling deleteText in the preview text state. deleteBackward is not supported in the preview text scenario.
- Select the API based on the deletion requirement: use deleteText to delete text in a specified range, and use deleteBackward to delete the character before the caret.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| range | [TextRange](ts-text-common.md#textrange12) | No    | Range of the text to delete, including the start position and end position of the text to delete.<br>The start position must be less than or equal to the end position; otherwise, the API call is invalid. A start position less than 0 is treated as 0, and an end position greater than the text length is treated as the text length.<br>If the deletion range is not specified, all text is deleted by default. If the start position of the text to delete is not specified, deletion starts from subscript 0 by default; if the end position of the text to delete is not specified, the end of the text is used as the deletion end point by default. |

### getSelection<sup>15+</sup>

getSelection(): TextRange

Obtains the current text selection range.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                     | Description              |
| ----------------------- | ---------------- |
| [TextRange](ts-text-common.md#textrange12) | Current text selection range, or cursor position if no text is selected.<br>If no component is bound to the controller or the component bound to the controller is released, **undefined** is returned.|

### clearPreviewText<sup>17+</sup>

clearPreviewText(): void

Notifies the input method to clear the current preview text.

> **NOTE**
>
> When the controller is not bound to a component or the component bound to the controller is released, this API is not effective.

**Atomic service API**: This API can be used in atomic services since API version 17.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### deleteBackward<sup>23+</sup>

deleteBackward(): void

Deletes the character before the caret in the text input box bound to the base controller `controller`. If some text has been selected with the mouse or keyboard before this API is called, the selected text is deleted.

This API is not effective in the state of dragged text.

`deleteBackward` only affects the internal UI behavior of the application and does not affect the internal logic of the input method application. It is not supported in the preview text scenario.

> **NOTE**
>
> When the controller is not bound to a component or the component bound to the controller is released, this API is not effective.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### scrollToVisible<sup>23+</sup>

scrollToVisible(range?: TextRange): void

Passes the start and end indexes to the bound text box components (**TextInput**, **TextArea**, and **Search**), and scrolls the text within the range to the visible area.

> **NOTE**
>
> When the controller is not bound to a component or the component bound to the controller is released, this API is not effective.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| range | [TextRange](ts-text-common.md#textrange12) | No   | Text range to be scrolled to the visible area, including the start and end positions of the text.<br>The start position must be less than or equal to the end position. Otherwise, the API call is invalid. If the start position is less than 0, it is treated as the value **0**. If the end position is greater than the length of the entire text, it is treated as the length of the entire text.<br>If no range is specified, the entire text is used by default. If the start position is not specified, the default start position is 0. If the end position is not specified, the default end position is the length of the entire text. |

## InputCounterOptions<sup>11+</sup>

Provides configuration options for the character counter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type   |     Read-Only   |     Optional   |     Description   |
| -------- | ------- | ----------- | ----------- | ----------- |
| thresholdPercentage | number | No | Yes | Percentage of the maximum number of characters that can be entered. The character counter displays the current number of entered characters/the maximum number of characters. When the number of entered characters is greater than the maximum number of characters multiplied by the percentage value, the character counter is displayed. The valid value range is [1,100]. When the value is a decimal, it is rounded down. If the set number is outside the valid value range, the character counter is not displayed. When set to undefined, the character counter is displayed, but this parameter is not effective.<br>**Atomic Service API:** Since API version 12, this API is supported in atomic services.|
| highlightBorder | boolean | No | Yes | If InputCounterOptions is not set when the user sets the counter, the border and the counter subscript turn red when the current number of entered characters reaches the maximum number of characters. If the user sets the character counter to be displayed and the thresholdPercentage parameter value is within the valid value range, the border and the counter subscript turn red when the number of entered characters exceeds the maximum number of characters. If this parameter is true, a red border is displayed; if it is false, no red border is displayed.<br>Default value: true<br>**Atomic Service API:** Since API version 12, this API is supported in atomic services.|
| counterTextColor<sup>22+</sup> | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | No | Yes | Sets the text color of the character counter in the component. When the number of characters entered by the user is greater than the maximum number of characters multiplied by the percentage value, the counter displays the current number of entered characters, and the text color of the counter is the color specified by counterTextColor. If counterTextColor is not set, the text color of the counter is the default color, which is gray.<br>**Atomic Service API:** Since API version 22, this API is supported in atomic services.|
| counterTextOverflowColor<sup>22+</sup> | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | No | Yes | Sets the text color of the character counter in the component when it overflows. When the number of characters entered by the user exceeds the maximum number of characters, the text color of the counter and the color of the border switch to the color specified by counterTextOverflowColor to remind the user that the input has exceeded the limit. If counterTextOverflowColor is not set, the text color of the counter and the border when overflowing is the default color, which is red.<br>**NOTE**<br>When the highlightBorder attribute of [InputCounterOptions](#inputcounteroptions11) is set, the border color is changed synchronously.<br>**Atomic Service API:** Since API version 22, this API is supported in atomic services.|

## CaretOffset<sup>11+</sup>

Describes the position of the caret relative to the text box.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type   |     Read-Only   |     Optional   |     Description   |
| -------- | ------- | ----------- | ----------- | ----------- |
| index | number | No | No | Index of the position where the caret is located. The value starts from 0 and ranges from 0 to the text length. |
| x     | number | No| No| X coordinate of the cursor relative to the text box, in px.|
| y     | number | No| No| Y coordinate of the cursor relative to the text box, in px.|

## TextDecorationOptions<sup>12+</sup>

Provides the text decoration options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type   |     Read-Only   |     Optional   |     Description   |
| -------- | ------- | ----------- | ----------- | ----------- |
| type  | [TextDecorationType](ts-appendix-enums.md#textdecorationtype) | No   | No | Sets the text decoration line type.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| color  | &nbsp;[ResourceColor](ts-types.md#resourcecolor) | No   | Yes | Sets the color of the text decoration line.<br>Default value: Color.Black. <br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| style | [TextDecorationStyle](ts-appendix-enums.md#textdecorationstyle12) | No   | Yes | Sets the style of the text decoration line.<br>Default value: TextDecorationStyle.SOLID.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| thicknessScale | number | No   | Yes | Sets the thickness scaling ratio of the text decoration line.<br>Default value: 1.0 <br>Value range: [0, +∞) <br>**Note:** Negative values are processed as the default value.<br>**Since:** 26.0.0<br>**Atomic service API:** This API can be used in atomic services since API version 26.0.0.<br>**Model restriction:** This API can be used only in the stage model. |

## SelectionOptions<sup>12+</sup>

Provides the configuration options for text selection.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type   |     Read-Only   |     Optional   |     Description   |
| -------- | ------- | ----------- | ----------- | ----------- |
| menuPolicy | [MenuPolicy](#menupolicy12) | No   | Yes | Policy for menu popup. Default value: MenuPolicy.DEFAULT.|

## MenuPolicy<sup>12+</sup>

Enumerates menu display policies.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Value  | Description                              |
| ------- | ---- | ---------------------------------- |
| DEFAULT | 0    | Whether the menu is displayed depends on the underlying default logic.|
| HIDE    | 1    | The menu is always hidden.                  |
| SHOW    | 2    | The menu is always displayed.                    |

## SymbolGlyphModifier<sup>12+</sup>

type SymbolGlyphModifier = import('../api/arkui/SymbolGlyphModifier').SymbolGlyphModifier

Defines custom icon symbol configurations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type | Description      |
| ----- | -------- |
| import('../api/arkui/SymbolGlyphModifier').[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | SymbolGlyphModifier object, used to set a custom icon symbol. |

## TextContentControllerOptions<sup>15+</sup>

Provides configuration options for text insertion operations in text input components.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type  | Read-Only| Optional| Description      |
| --------- | ------ | ---- | ---- | ---------- |
| offset | number | No | Yes | Position to insert text. Value range: [0, text length]. If the value is out of range, it is automatically corrected to a valid boundary position.<br>**Note:**<br>Pass this parameter when text needs to be inserted at a specified position (rather than at the end). If not passed, text is inserted at the end by default. |