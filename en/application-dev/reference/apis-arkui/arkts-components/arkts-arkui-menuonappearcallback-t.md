# MenuOnAppearCallback

```TypeScript
declare type MenuOnAppearCallback = (start: number, end: number) => void
```

Represents the callback invoked when the custom context menu on selection appears.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Start position of the selected content. |
| end | number | Yes | End position of the selected content. |
