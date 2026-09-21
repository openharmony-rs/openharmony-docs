# TextBaseController

```TypeScript
declare interface TextBaseController
```

Defines a text selection controller.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## closeSelectionMenu

```TypeScript
closeSelectionMenu(): void
```

Closes the custom or default text selection menu.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getLayoutManager

```TypeScript
getLayoutManager(): LayoutManager
```

Obtains a **LayoutManager** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [LayoutManager](arkts-arkui-layoutmanager-i.md) | Layout manager object. |

## setSelection

```TypeScript
setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

Sets the range of content selection. The selected content is highlighted.

If both **selectionStart** and **selectionEnd** are set to **-1**, the entire content is selected.

The component must be focused for the API call to have effect.

Since API version 12, on 2-in-1 devices, regardless of the value of **options**, calling the **setSelection** API will not display a menu; if a menu is already open, calling the API will close it.

On non-2-in-1 devices, when **options** is set to **MenuPolicy.DEFAULT**, the following rules apply after the API is called:

1. If the component has a menu with a selection handle,
the menu remains open and is relocated according to the selection.
2. If the component has a menu without a selection handle,
the menu remains open and its position remains unchanged.
3. If there is no menu open, no menu will appear after the selection.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectionStart | number | Yes | Start position of the selection.<br>Values less than 0 are treated as **0**. |
| selectionEnd | number | Yes | End position of the selection.<br>If the value exceeds the text length, the current text length is used instead. |
| options | [SelectionOptions](../arkts-components/arkts-arkui-common-comp-selectionoptions-i.md) | No | Configuration of options. The default value is inherited from [SelectionOptions](../arkts-components/arkts-arkui-common-comp-selectionoptions-i.md). |
