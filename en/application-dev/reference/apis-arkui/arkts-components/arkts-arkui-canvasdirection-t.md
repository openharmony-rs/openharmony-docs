# CanvasDirection

```TypeScript
declare type CanvasDirection = "inherit" | "ltr" | "rtl"
```

Defines the current text direction. The value type is a union of the types listed in the table below.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| "inherit" | Inherits the text direction set in the general attributes of the canvas component. If the **direction** attribute is not set on the canvas component, the system text direction is used. |
| "ltr" | The text direction is from left to right. |
| "rtl" | The text direction is from right to left. |
