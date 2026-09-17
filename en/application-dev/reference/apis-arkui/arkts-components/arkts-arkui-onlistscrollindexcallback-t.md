# OnListScrollIndexCallback

```TypeScript
declare type OnListScrollIndexCallback = (start: number, end: number, center: number) => void
```

Represents a callback for item changes in the visible area of the **List** component.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Index of the first child component in the list display area. |
| end | number | Yes | Index of the last child component in the list display area. |
| center | number | Yes | Index of the center child component in the list display area. |
