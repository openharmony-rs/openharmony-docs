# TextPickerScrollStopCallback

```TypeScript
declare type TextPickerScrollStopCallback = (value: string | string[], index: number | number[]) => void
```

Defines the **onScrollStop** event callback signature.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; string[] | Yes | Text of the selected item. Use the array type for multi-column pickers.<br> **NOTE:** <br>The return value is a text value for text or mixed content, and an empty string for image-only content. |
| index | number &#124; number[] | Yes | Index of the selected item. The index is zero-based. Use the array type for multi-column pickers. |
