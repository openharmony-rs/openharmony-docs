# OnContentScrollCallback

```TypeScript
declare type OnContentScrollCallback = (totalOffsetX: number, totalOffsetY: number) => void
```

Callback for text content scrolling.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnContentScrollCallback = (totalOffsetX: number, totalOffsetY: number) => void--><!--Device-unnamed-declare type OnContentScrollCallback = (totalOffsetX: number, totalOffsetY: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| totalOffsetX | number | Yes | Horizontal offset of the text in the content area, in px. |
| totalOffsetY | number | Yes | Vertical offset of the text in the content area, in px. |
