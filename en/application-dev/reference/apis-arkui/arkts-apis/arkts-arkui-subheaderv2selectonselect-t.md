# SubHeaderV2SelectOnSelect

```TypeScript
export type SubHeaderV2SelectOnSelect = (selectedIndex: number, selectedContent?: string) => void
```

Defines the callback invoked when an item in the drop-down list box is selected.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedIndex | number | Yes | Index of the selected drop-down menu option. |
| selectedContent | string | No | Content of the selected drop-down menu option. |
