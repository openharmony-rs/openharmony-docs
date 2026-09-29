# OnTextPickerChangeCallback

```TypeScript
declare type OnTextPickerChangeCallback = (selectItem: string[], index: number[]) => void
```

Defines the **onChange** event callback signature.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnTextPickerChangeCallback = (selectItem: string | string[], index: number | number[]) => void--><!--Device-unnamed-declare type OnTextPickerChangeCallback = (selectItem: string | string[], index: number | number[]) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectItem | string[] | Yes | Text of the currently selected item. For a multi-column data picker, selectItem is of the array type.<br>**Note:** <br>When the picker content is text or a mix of text and images, the value of selectItem is the text value of the selected item. When the picker content is an image, the value of selectItem is empty. |
| index | number[] | Yes | Index of the selected item. The index is zero-based. Use the array type for multi-column pickers. |
