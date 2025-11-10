# Text Box Component Common APIs
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @kangshihui-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @HelloCrease-->

Provides capabilities for [TextInput](ts-basic-components-textinput.md) and [TextArea](ts-basic-components-textarea.md) components to obtain text and cursor information, insert and delete text, set character counters, and configure text decoration lines.
Provides capabilities for the [Search](ts-basic-components-search.md) component to obtain text and cursor information, insert and delete text, and configure text decoration lines.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.

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
| [RectResult](ts-universal-attributes-on-child-touch-test.md#rectresult) | Position of the edited text area relative to the component and its size.|

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
| number| Number of lines of the edited text.|

### getCaretOffset<sup>11+</sup>

getCaretOffset(): CaretOffset

Obtains the position information of the caret.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                     | Description              |
| ----------------------- | ---------------- |
| [CaretOffset](#caretoffset11) | Position of the caret relative to the text box.|

> **NOTE**
>
> - If this API is called when the caret position is updated in the current frame, it will not take effect.
> - For the **Search** component, the returned position information is the offset of the first character relative to the search icon in the component.
> - If no text is entered in the **Search** component, the return value contains the position information relative to the component.
> - The location information in the return value is the location of the caret relative to the editable component.

### addText<sup>15+</sup>

addText(text: string, textOperationOptions?: TextContentControllerOptions): number

Inserts text at a specified position in the editable content. If no position is specified, the text is appended to the end of the existing content.
This API does not work when the text is being dragged.

**addText** only affects the UI performance within the application and has no effect on the internal logic of the input method application. Therefore, avoid calling this API for preview text.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| text | string | Yes   | Text to insert.|
| textOperationOptions   | [TextContentControllerOptions](#textcontentcontrolleroptions15) | No   | Configuration option for inserting text. If this parameter is not provided, the text is appended to the end.|

**Return value**

| Type | Description      |
| ----- | -------- |
| number| New cursor position after insertion.|

### setStyledPlaceholder<sup>22+</sup>

setStyledPlaceholder(styledString: StyledString): void

Binds or updates the styled placeholder string.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| styledString | [StyledString](ts-universal-styled-string.md#styledstring) | Yes| Styled string for the placeholder. This takes precedence over the plain text **placeholder** attribute.<br>The placeholder does not support gesture events or hyperlink navigation within styled strings.|

### deleteText<sup>15+</sup>

deleteText(range?: TextRange): void

Deletes text within a specified range in the editable content.
This API does not work when the text is being dragged.

**deleteText** only affects the UI performance within the application and has no effect on the internal logic of the input method application. Therefore, avoid calling this API for preview text.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory  | Description |
| ------- | ------ | ---- | ----- |
| range | [TextRange](ts-text-common.md#textrange12) | No   | Range of the text to be deleted, including the start and end positions.<br>If the range is not specified, the entire text is deleted. If the start position is not specified, deletion starts from index 0. If the end position is not specified, deletion ends at the end of the text.|

### getSelection<sup>15+</sup>

getSelection(): TextRange

Obtains the current text selection range.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                     | Description              |
| ----------------------- | ---------------- |
| [TextRange](ts-text-common.md#textrange12) | Current text selection range, or cursor position if no text is selected.|

### clearPreviewText<sup>17+</sup>

clearPreviewText(): void

Notifies the input method to clear the current preview text.

**Atomic service API**: This API can be used in atomic services since API version 17.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## InputCounterOptions<sup>11+</sup>

Provides configuration options for the character counter.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type   |     Read-Only   |     Optional   |     Description   |
| -------- | ------- | ----------- | ----------- | ----------- |
| thresholdPercentage | number  | No| Yes| Threshold percentage for displaying the character counter. The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. When displayed, the character counter is in the following format: Number of characters that have been entered/Maximum number of characters allowed. It is visible when the number of characters entered is greater than the character limit multiplied by the threshold percentage value. Value range: [1, 100]. If the value is not an integer, it is rounded down to the nearest integer. If the value exceeds the valid value range, the character counter is not displayed. If the value is **undefined**, the character counter is displayed, but this parameter has no effect.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| highlightBorder     | boolean | No | Yes| Whether to highlight the text box border and character counter subscript in red. If **options** is not set, the text box border and character counter subscript turn red when the number of characters entered reaches the limit. If the character counter is displayed and **thresholdPercentage** is set to a valid value, the text box border and character counter subscript turn red when the number of entered characters exceeds the limit. The value **true** (default) means to highlight the text box border and character counter subscript in red.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| counterTextColor<sup>22+</sup> | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | No| Yes| Text color of the character counter in the component. When the number of characters entered is greater than the maximum number of characters multiplied by the percentage value, the counter displays the number of characters entered, and the color of the counter is the color specified by counterTextColor. If counterTextColor is not set, the default color (black) is used.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
| counterTextOverflowColor<sup>22+</sup> | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | No| Yes| Text color of the character counter when the counter overflows. When the number of characters entered by the user exceeds the maximum length of the counter, the text color and border color of the counter are switched to the color specified by counterTextOverflowColor to remind the user that the input has exceeded the limit. If counterTextOverflowColor is not set, the text color of the counter and border is the default color (red) when the overflow occurs.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|

## CaretOffset<sup>11+</sup>

Describes the position of the caret relative to the text box.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type   |     Read-Only   |     Optional   |     Description   |
| -------- | ------- | ----------- | ----------- | ----------- |
| index | number | No| No| Index of the caret position.   |
| x     | number | No| No| X-coordinate of the caret relative to the text box, in px.|
| y     | number | No| No| Y-coordinate of the caret relative to the text box, in px.|

## TextDecorationOptions<sup>12+</sup>

Provides the text decoration options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type   |     Read-Only   |     Optional   |     Description   |
| -------- | ------- | ----------- | ----------- | ----------- |
| type  | [TextDecorationType](ts-appendix-enums.md#textdecorationtype) | No  | No| Type of the text decoration.|
| color  |  [ResourceColor](ts-types.md#resourcecolor) | No  | Yes| Color of the text decoration.|
| style | [TextDecorationStyle](ts-appendix-enums.md#textdecorationstyle12) | No  | Yes| Style of the text decoration.|

## SelectionOptions<sup>12+</sup>

Provides the configuration options for text selection.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type   |     Read-Only   |     Optional   |     Description   |
| -------- | ------- | ----------- | ----------- | ----------- |
| menuPolicy | [MenuPolicy](#menupolicy12) | No  | Yes| Menu display policy.|

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

type SymbolGlyphModifier = SymbolGlyphModifier

Defines custom icon symbol configurations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type | Description      |
| ----- | -------- |
| [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | Returns the current **SymbolGlyphModifier** instance.|

## TextContentControllerOptions<sup>15+</sup>

Provides Configuration options for text insertion operations in a text box.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type  | Read-Only| Optional| Description      |
| --------- | ------ | ---- | ---- | ---------- |
| offset | number | No  | Yes  | Position where the text will be inserted.|
