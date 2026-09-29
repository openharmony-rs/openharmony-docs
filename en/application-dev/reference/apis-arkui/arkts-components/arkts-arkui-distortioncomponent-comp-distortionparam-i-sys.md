# DistortionParam (System API)

```TypeScript
declare interface DistortionParam
```

Defines the spatial distortion parameters.

> **NOTE:** 
> 
> - The coordinates of the four corner points can be set according to the following coordinate system. For a component, the top-left corner is at **{ x:0, y:0 }**, the top-right corner is at **{ x:1, y:0 }**, the bottom-left corner is at **{ x:0, y:1 }**, and the bottom-right corner is at **{ x:1, y:1 }**.
> 
> - If the bottomLeft attribute is set to **{ x:0.5, y:0.5 }**, it indicates that the bottom-left corner is distorted to the center of the component, producing an inward-shrinking distortion effect in the bottom-left area of the component.
> 
> - When setting the coordinates of the four corner points, comply with the spatial logic: the y coordinate of the top corner points should be smaller than that of the bottom corner points, and the x coordinate of the left corner points should be smaller than that of the right corner points, to ensure that the distorted quadrilateral maintains a reasonable spatial perspective relationship. (That is, the corner point coordinates should maintain a reasonable spatial perspective relationship to avoid vertical flipping or crossing.) For example, if **topLeft** =
> **{ x:0, y:0.7 }** and **bottomLeft** = **{ x:0, y:0.2 }**, the top-left corner is lower than the bottom-left
> corner, which violates the spatial logic and may cause rendering exceptions (such as crossing or flipping of mesh
> patches, resulting in disordered or unpredictable visual results).
> 
> - The coordinates of the four corner points can be used together with **barrelDistortion** to build richer spatial distortion effects.

**Since:** 26.0.0

<!--Device-unnamed-declare interface DistortionParam--><!--Device-unnamed-declare interface DistortionParam-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## barrelDistortion

```TypeScript
barrelDistortion: Vector4
```

Barrel distortion parameters for the four edges.

The four values in Vector4: **x** for the left edge, **y** for the right edge, **z** for the top edge, and **w** for the bottom edge.

A positive value indicates the edge is convex, while a negative value indicates it is concave. When the absolute value of the distortion parameter is 1, the distortion is at its extreme.

Value range for x, y, z, and w: [-1, 1]

**Note:** 

The four components of **barrelDistortion** jointly determine the barrel distortion intensity of the four edges and can be used in combination with the four corner coordinates to create more various spatial distortion.

Geometrically, **x** and **y** determine the bending direction and magnitude of the left and right vertical edges, while **z** and **w** determine those of the top and bottom horizontal edges. When a component is positive, the corresponding edge bulges outward from the component, creating a convex barrel distortion; when negative, the corresponding edge curves inward toward the component, creating a concave pincushion distortion. When the four component values are similar, the overall effect presents a uniform barrel distortion similar to that of a wide- angle lens; when **x**, **y** differ significantly from **z**, **w**, asymmetric distortion with horizontal or vertical stretching occurs.

Because extreme values may cause image folding (mesh patches overlapping and flipping) or sampling anomalies (texture coordinates exceeding the valid sampling range), it is recommended to keep **x**, **y**, **z**, and **w** within the range of [-1, 1].

**Type:** [Vector4](arkts-arkui-distortioncomponent-comp-vector4-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistortionParam-barrelDistortion: Vector4--><!--Device-DistortionParam-barrelDistortion: Vector4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bottomLeft

```TypeScript
bottomLeft: Vector2
```

Coordinate of the bottom-left corner. Value principle: the coordinate value is a ratio relative to the component size, where 0 indicates 0% and 1 indicates 100%. Recommended value range: [0, 1]. The value must comply with spatial logic to avoid rendering anomalies.

**Type:** [Vector2](arkts-arkui-distortioncomponent-comp-vector2-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistortionParam-bottomLeft: Vector2--><!--Device-DistortionParam-bottomLeft: Vector2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## bottomRight

```TypeScript
bottomRight: Vector2
```

Coordinate of the bottom-right corner. Value principle: the coordinate value is a ratio relative to the component size, where 0 indicates 0% and 1 indicates 100%. Recommended value range: [0, 1]. The value must comply with spatial logic to avoid rendering anomalies.

**Type:** [Vector2](arkts-arkui-distortioncomponent-comp-vector2-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistortionParam-bottomRight: Vector2--><!--Device-DistortionParam-bottomRight: Vector2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## topLeft

```TypeScript
topLeft: Vector2
```

Coordinate of the top-left corner. Value principle: the coordinate value is a ratio relative to the component size, where 0 indicates 0% and 1 indicates 100%. Recommended value range: [0, 1]. The value must comply with spatial logic to avoid rendering anomalies.

**Type:** [Vector2](arkts-arkui-distortioncomponent-comp-vector2-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistortionParam-topLeft: Vector2--><!--Device-DistortionParam-topLeft: Vector2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## topRight

```TypeScript
topRight: Vector2
```

Coordinate of the top-right corner. Value principle: the coordinate value is a ratio relative to the component size, where 0 indicates 0% and 1 indicates 100%. Recommended value range: [0, 1]. The value must comply with spatial logic to avoid rendering anomalies.

**Type:** [Vector2](arkts-arkui-distortioncomponent-comp-vector2-t-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DistortionParam-topRight: Vector2--><!--Device-DistortionParam-topRight: Vector2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
