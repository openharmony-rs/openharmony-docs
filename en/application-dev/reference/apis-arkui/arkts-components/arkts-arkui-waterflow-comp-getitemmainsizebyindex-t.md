# GetItemMainSizeByIndex

```TypeScript
declare type GetItemMainSizeByIndex = (index: number) => number
```

Obtains the main axis size of a specified water flow item based on its index.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the target water flow item.<br>Value range: [0, total number of child nodes - 1]. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Main axis size, in vp, of the water flow item at the specified index, which is the height for a vertical **WaterFlow** component and the width for a horizontal **WaterFlow** component. |
