# ArcScrollIndexHandler

```TypeScript
declare type ArcScrollIndexHandler = (start: number, end: number, center: number) => void
```

Represents the callback triggered when a child component enters or leaves the visible area of the **ArcList** component.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Index of the first child component in the visible area of the **ArcList** component. |
| end | number | Yes | Index of the last child component in the visible area of the **ArcList** component. |
| center | number | Yes | Index of the center child component in the visible area of the **ArcList** component. |
