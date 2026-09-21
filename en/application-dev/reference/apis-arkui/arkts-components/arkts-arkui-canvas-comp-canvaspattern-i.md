# CanvasPattern

```TypeScript
declare interface CanvasPattern
```

**CanvasPattern** represents an object, created by the [createPattern](../arkts-apis/arkts-arkui-viewmodel-canvasrenderingcontext2d-i.md#createpattern) API, describing an image filling pattern based on the image and repetition mode. It is suitable for scenarios where pattern filling or background textures are needed on a canvas, simplifying pattern filling implementation and improving drawing efficiency.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

Applies a matrix transformation to the current **CanvasPattern** using a **Matrix2D** object as the parameter. This is suitable for scenarios where geometric transformations such as translation, scaling, and rotation need to be applied to the pattern fill. If no parameter is passed, no matrix transformation is applied to the **CanvasPattern**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transform | Matrix2D | No | Transformation matrix used to perform geometric transformations such as translation, scaling, and rotation on the **CanvasPattern**.<br>Note: No matrix transformation is performed when the parameter is **undefined** or **null**.<br>Default value: **null** |
