# DistortionParam (System API)

Defines the spatial distortion parameters.

> **NOTE:** 
> 
> - The coordinates of the four corners of the component can be set as follows: top-left corner: { x:0, y:0 }, top-right corner: { x:1, y:0 }, bottom-left corner: { x:0, y:1 }, bottom-right corner: { x:1, y:1 }.
> 
> - For example, if the **bottomLeft** attribute is set to **{ x:0.5, y:0.5 }**, the bottom-left corner is deformed to the position of the component center, and the corresponding distortion effect is generated.
> 
> - When setting the coordinates of the four corners, ensure they follow spatial logic. For example, if **topLeft**is **{ x:0, y:0.7 }** and **bottomLeft** is **{ x:0, y:0.2 }**, the top-left corner is lower than the bottom-left corner, which violates the spatial logic and may cause rendering exceptions.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## barrelDistortion

```TypeScript
barrelDistortion: Vector4
```

Barrel distortion degree of the four edges.

The four values in **Vector4** are as follows: **x** indicates the left edge, **y** indicates the right edge, **z** indicates the top edge, and **w** indicates the bottom edge.

A positive value indicates outward distortion, and a negative value indicates inward distortion. When the absolute value of the distortion parameter reaches 1, the distortion degree is extreme.

Recommended value range for x, y, z, and w: **[-1, 1]**

**Type:** [Vector4](arkts-arkui-vector4-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bottomLeft

```TypeScript
bottomLeft: Vector2
```

Coordinates of the bottom-left corner.

**Type:** [Vector2](arkts-arkui-vector2-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bottomRight

```TypeScript
bottomRight: Vector2
```

Coordinates of the bottom-right corner.

**Type:** [Vector2](arkts-arkui-vector2-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## topLeft

```TypeScript
topLeft: Vector2
```

Coordinates of the top-left corner.

**Type:** [Vector2](arkts-arkui-vector2-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## topRight

```TypeScript
topRight: Vector2
```

Coordinates of the top-right corner.

**Type:** [Vector2](arkts-arkui-vector2-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
