# CanvasGradient

You can create a gradient object on the canvas by calling CanvasRenderingContext2D.createLinearGradient().

@interface CanvasGradient

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## addColorStop

```TypeScript
addColorStop(offset: number, color: string): void
```

Adds a color stop for the CanvasGradient object based on the specified offset and gradient color.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Proportion of the distance between the color stop and the start point to the total length. The value ranges from 0 to 1. |
| color | string | Yes | Sets the gradient color. |
