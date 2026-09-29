# TextBaseController

```TypeScript
declare interface TextBaseController
```

Defines a text selection controller.

**Since:** 12

<!--Device-unnamed-declare interface TextBaseController--><!--Device-unnamed-declare interface TextBaseController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeSelectionMenu

```TypeScript
closeSelectionMenu(): void
```

Closes the custom or default text selection menu.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextBaseController-closeSelectionMenu(): void--><!--Device-TextBaseController-closeSelectionMenu(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getLayoutManager

```TypeScript
getLayoutManager(): LayoutManager
```

Obtains a **LayoutManager** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextBaseController-getLayoutManager(): LayoutManager--><!--Device-TextBaseController-getLayoutManager(): LayoutManager-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LayoutManager](arkts-arkui-layoutmanager-i.md) | Layout manager object used to obtain text layout information, such as the number of lines, line metrics, and glyph positions. |

## setSelection

```TypeScript
setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

Sets the range of content selection. The selected content is highlighted.

If both **selectionStart** and **selectionEnd** are set to **-1**, the entire content is selected.

The component must be focused for the API call to have effect.

Since API version 12, on PC/2-in-1 devices, calling the setSelection API does not pop up a menu regardless of the value of **options**. In addition, if a menu already exists in the component, calling the setSelection API closes the menu.

On non-2-in-1 devices, when **options** is set to **MenuPolicy.DEFAULT**, the following rules apply after the API is called:

1. If the component has a menu with a selection handle, the menu remains open and is relocated according to the
selection.

2. If the component has a menu without a selection handle, the menu remains open and its position remains
unchanged.

3. If there is no menu open, no menu will appear after the selection.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextBaseController-setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void--><!--Device-TextBaseController-setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the selection.<br>If the value is less than 0, it is processed as 0. If the value is greater than the text length, it is processed as the current text length. <br>Special value effect: when both selectionStart and selectionEnd are -1, all text is selected. |
| selectionEnd | number | Yes | End position of the selection.<br>If the value is less than 0, it is processed as 0. If the value is greater than the text length, it is processed as the current text length. <br>Special value effect: when both selectionStart and selectionEnd are -1, all text is selected. |
| options | [SelectionOptions](../arkts-components/arkts-arkui-common-comp-selectionoptions-i.md) | No | Configuration of options. The default value is inherited from [SelectionOptions](../arkts-components/arkts-arkui-common-comp-selectionoptions-i.md). |
