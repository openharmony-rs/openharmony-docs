# OnSelectCallback

```TypeScript
declare type OnSelectCallback = (index: number, selectStr: string) => void
```

Callback of selecting an item from the select event.

@typedef {function} OnSelectCallback

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnSelectCallback = (index: number, selectStr: string) => void--><!--Device-unnamed-declare type OnSelectCallback = (index: number, selectStr: string) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | The index of the selected item. |
| selectStr | string | Yes | The value of the selected item. |
