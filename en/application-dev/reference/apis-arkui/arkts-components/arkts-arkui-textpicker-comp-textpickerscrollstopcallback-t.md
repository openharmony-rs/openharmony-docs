# TextPickerScrollStopCallback

```TypeScript
declare type TextPickerScrollStopCallback = (value: string[], index: number[]) => void
```

Defines the **onScrollStop** event callback signature.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-unnamed-declare type TextPickerScrollStopCallback = (value: string | string[], index: number | number[]) => void--><!--Device-unnamed-declare type TextPickerScrollStopCallback = (value: string | string[], index: number | number[]) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string[] | Yes | Text of the currently selected item. For a multi-column data picker, the value is of the array type.<br>**Note:** <br>When the picker content is text or a mix of text and image, the value is the text value of the selected item. When the picker content is an image, the value is empty. |
| index | number[] | Yes | Index of the selected item. The index is zero-based. Use the array type for multi-column pickers. |
