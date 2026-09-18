# CanvasPattern

**CanvasPattern** represents an object, created by the createPattern API, describing an image filling pattern based on the image and repetition mode.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

Uses a **Matrix2D** object as a parameter to perform matrix transformation on the current **CanvasPattern** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transform | [Matrix2D](../arkts-apis/arkts-arkui-matrix2d-c.md) | No | Transformation matrix.<br>The **undefined** and **null** values are treated as invalid.<br>Default value: **null**. |
