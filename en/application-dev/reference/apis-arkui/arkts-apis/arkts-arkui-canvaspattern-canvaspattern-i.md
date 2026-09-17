# CanvasPattern

Describes an opaque object of a template, which is created using the createPattern() method.

@interface CanvasPattern

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

Adds the matrix transformation effect to the current template.

**Since:** 11

**Model restriction:** This API can be used only in the FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transform | [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | No | transformation matrix |
