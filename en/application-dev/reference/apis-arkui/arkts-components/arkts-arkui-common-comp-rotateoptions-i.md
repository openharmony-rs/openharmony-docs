# RotateOptions

```TypeScript
declare interface RotateOptions
```

Defines component rotation parameters.

**Since:** 7

<!--Device-unnamed-declare interface RotateOptions--><!--Device-unnamed-declare interface RotateOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: number | string
```

Angle to rotate. A positive angle indicates a clockwise rotation, and a negative angle indicates a counterclockwise rotation. The value can be of the string type, for example, **'90deg'**.

**Type:** number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RotateOptions-angle: number | string--><!--Device-RotateOptions-angle: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: number | string
```

X coordinate of the transformation center point (anchor). The value can be of the string type, for example, **'50'** and **'50%'**.

Unit: vp

**Type:** number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RotateOptions-centerX?: number | string--><!--Device-RotateOptions-centerX?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number | string
```

Y coordinate of the transformation center point (anchor). The value can be of the string type, for example, **'50'** and **'50%'**.

Unit: vp

**Type:** number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-RotateOptions-centerY?: number | string--><!--Device-RotateOptions-centerY?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerZ

```TypeScript
centerZ?: number
```

Z-axis anchor, that is, the z-component of the 3D rotation center point.

Default value: **0**.

Unit: px

**Type:** number

**Default:** 0

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-RotateOptions-centerZ?: number--><!--Device-RotateOptions-centerZ?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## perspective

```TypeScript
perspective?: number
```

Z-axis coordinate of the camera. The value indicates the viewing distance, that is, the distance between the camera and the z=0 plane. The positive and negative values of the parameter determine the camera observation direction. When perspective is set to 0, the system automatically calculates a proper camera Z-axis position. The value is negative.

The rotation axis and center point are defined based on the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system). When the component moves, the coordinate system does not follow it.

Default value: **0**.

Unit: px

**Type:** number

**Default:** 0

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-RotateOptions-perspective?: number--><!--Device-RotateOptions-perspective?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

X coordinate of the rotation axis vector.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RotateOptions-x?: number--><!--Device-RotateOptions-x?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

Y coordinate of the rotation axis vector.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RotateOptions-y?: number--><!--Device-RotateOptions-y?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: number
```

Z coordinate of the rotation axis vector.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RotateOptions-z?: number--><!--Device-RotateOptions-z?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
