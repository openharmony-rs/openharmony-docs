# RichEditorBaseController

Represents the base class of the **RichEditor** component controller.

**Inheritance/Implementation:** RichEditorBaseController implements [TextEditControllerEx](../arkts-apis/arkts-arkui-texteditcontrollerex-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeSelectionMenu

```TypeScript
closeSelectionMenu(): void
```

Closes the custom selection menu or the system default selection menu.

When the controller is not bound to a component or the component bound to the controller is released, this API call does not take effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## deleteBackward

```TypeScript
deleteBackward(): void
```

Deletes the character before the caret or the selected content. If no content is selected, one character before the current caret position is deleted. If content is selected, the selected content is deleted.

This API is not supported in preview display scenarios.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getCaretOffset

```TypeScript
getCaretOffset(): number
```

Obtains the current caret position.

If the caret position cannot be obtained (for example, when the controller is not bound to the component), the return value is **-1**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Position of the caret. |

## getCaretRect

```TypeScript
getCaretRect(): RectResult | undefined
```

Returns the position of the current caret relative to the RichEditor component. If the caret does not blink or the controller is not bound to a component, undefined is returned.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [RectResult](arkts-arkui-rectresult-i.md) &#124; undefined | Relative position of the caret in the **RichEditor** component. |

## getLayoutManager

```TypeScript
getLayoutManager(): LayoutManager
```

Obtains the **LayoutManager** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LayoutManager](../arkts-apis/arkts-arkui-layoutmanager-i.md) | Layout manager object, which can be used to obtain information such as the layout position of the component content.<br>Returns undefined when the controller is not bound to a component or the component bound to the controller is released. |

## getPreviewText

```TypeScript
getPreviewText(): PreviewText
```

Obtains the preview text.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PreviewText](../arkts-apis/arkts-arkui-previewtext-i.md) | Preview text information, including the candidate text content pre-displayed by the input method and its start position.<br>Returns undefined when the controller is not bound to a component or the component bound to the controller is released. |

## getTypingStyle

```TypeScript
getTypingStyle(): RichEditorTextStyle
```

Obtains the preset text style of a user.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md) | A user-preset text input style object that contains style attributes such as font color, size, and weight. It can be used to query the input text style configuration of the current component.<br>When the controller is not bound to a component, or the component bound to the controller is released, undefined is returned. |

## isEditing

```TypeScript
isEditing(): boolean
```

Obtains the current editing state of the rich text. If the controller is not bound to a component or the component bound to the controller is released, false is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true indicates the editing state, and false indicates the non-editing state. |

## scrollToVisible

```TypeScript
scrollToVisible(range?: TextRange): void
```

Scrolls the content in the specified range into the visible area.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| range | [TextRange](../arkts-apis/arkts-arkui-textrange-i.md) | No | Content range to scroll into the visible area, including the start position and end position of the content.<br>The start position must be less than or equal to the end position; otherwise, the API call does not take effect. A start position less than 0 is treated as 0, and an end position greater than the total text length is treated as the total text length. <br>If no range is specified, all content is used by default. If no start position is specified, the start position defaults to 0; if no end position is specified, the end position defaults to the total text length. |

## setCaretOffset

```TypeScript
setCaretOffset(offset: number): boolean
```

Sets the caret position.

When the controller is not bound to a component or the component bound to the controller is released, this API returns false and the setting fails.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset of the caret. If it exceeds the range of all content, the setting will fail. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the caret offset is set successfully.<br>**true** if the caret offset is set successfully; **false** otherwise. |

## setSelection

```TypeScript
setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

Selects the content in the component, and the backplate of the selected part is highlighted.

If both **selectionStart** and **selectionEnd** are set to **-1**, all content is selected. If both **selectionStart** and **selectionEnd** are set to **0**, the current selection is cleared.

If this API is called when the text box is not focused, the selected effect is not displayed.

Since API version 12, on PC/2-in-1 devices (which can be determined by obtaining the device type through deviceInfo.deviceType), calling setSelection does not pop up a menu regardless of the value of options. If a menu already exists in the component, calling setSelection closes the menu. On non-PC/2-in-1 devices, when options is set to MenuPolicy.DEFAULT, the following rules apply:

1. If the component has a selection handle menu, calling the API will not close the menu,
and the menu position will be adjusted.
2. If the component has a menu without a selection handle, calling the API will not
close the menu, and the menu position will remain unchanged.
3. If there is no menu within the component, calling the API will not display the menu.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the selection. |
| selectionEnd | number | Yes | End position of the selection. |
| options | [SelectionOptions](arkts-arkui-selectionoptions-i.md) | No | Selection option configuration, used to control the menu popup policy during selection operations.<br>Pass this parameter when you need to customize the menu popup behavior (such as forcing the menu to show or hide); <br>when omitted, MenuPolicy.DEFAULT is used by default, following the system default menu popup policy. <br>For the applicable scenarios of each MenuPolicy value, see the SelectionOptions object description.<br>**Since:** 12 |

## setStyledPlaceholder

```TypeScript
setStyledPlaceholder(styledString: StyledString): void
```

Sets the placeholder text of the styled string when there is no input.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| styledString | [StyledString](../arkts-apis/arkts-arkui-styledstring-c.md) | Yes | Sets the placeholder text of the styled string. It takes higher priority than the placeholder text set by the [placeholder](arkts-arkui-richeditor-comp-attribute.md#placeholder) attribute. <br>The placeholder text does not support gesture events bound to the [GestureStyle](../arkts-apis/arkts-arkui-gesturestyle-c.md) of the styled string, or hyperlink navigation provided by [UrlStyle](../arkts-apis/arkts-arkui-urlstyle-c.md). |

## setTypingParagraphStyle

```TypeScript
setTypingParagraphStyle(style: RichEditorParagraphStyle): void
```

Sets the user-preset paragraph style. It takes effect only when the component content is empty or text is entered after a line break at the end of the component. When the controller is not bound to a component or the component bound to the controller is released, this API call does not take effect.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| style | [RichEditorParagraphStyle](arkts-arkui-richeditorparagraphstyle-i.md) | Yes | Preset paragraph style. |

## setTypingStyle

```TypeScript
setTypingStyle(value: RichEditorTextStyle): void
```

Sets the preset typing style.

When the controller is not bound to a component or the component bound to the controller is released, this API call does not take effect.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md) | Yes | Preset text input style, including font color, size, weight, and other attributes, used to set the default style for subsequently input text. |

## stopEditing

```TypeScript
stopEditing(): void
```

Exits the editing state.

If the controller is not bound to a component or the component bound to the controller is released, this API call does not take effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
