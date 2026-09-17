# OnContentScrollCallback

```TypeScript
declare type OnContentScrollCallback = (totalOffsetX: number, totalOffsetY: number) => void
```

Called when the text content is scrolled.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| totalOffsetX | number | Yes | Offset of the horizontal coordinate of the upper left corner of the text relative to the horizontal coordinate of the upper left corner of the entire content input area. |
| totalOffsetY | number | Yes | Offset of the vertical coordinate of the upper left corner of the text relative to the vertical coordinate of the upper left corner of the entire content input area. |
