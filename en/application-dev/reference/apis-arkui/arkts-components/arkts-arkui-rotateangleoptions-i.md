# RotateAngleOptions

Rotation parameter option of the rotation angle on each axis.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angleX

```TypeScript
angleX?: number | string
```

Rotation angle along the x-axis. A positive value indicates clockwise rotation relative to the rotation axis, and a negative value indicates counterclockwise rotation. The value can be of the string type, for example, **'90deg'**.

Default value: **0**.

Value range: (-∞, +∞).

**Type:** number &#124; string

**Default:** 0

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angleY

```TypeScript
angleY?: number | string
```

Rotation angle along the y-axis. A positive value indicates clockwise rotation relative to the rotation axis, and a negative value indicates counterclockwise rotation. The value can be of the string type, for example, **'90deg'**.

Default value: **0**.

Value range: (-∞, +∞).

**Type:** number &#124; string

**Default:** 0

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angleZ

```TypeScript
angleZ?: number | string
```

Rotation angle along the z-axis. A positive value indicates clockwise rotation relative to the rotation axis, and a negative value indicates counterclockwise rotation. The value can be of the string type, for example, **'90deg'**.

Default value: **0**.

Value range: (-∞, +∞).

**Type:** number &#124; string

**Default:** 0

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: number | string
```

X coordinate of the transformation center point (anchor).

Unit: vp

Default value: **'50%'**.

Value range: (-∞, +∞).

**Type:** number &#124; string

**Default:** '50%'

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number | string
```

Y coordinate of the transformation center point (anchor).

Unit: vp

Default value: **'50%'**.

Value range: (-∞, +∞).

**Type:** number &#124; string

**Default:** '50%'

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerZ

```TypeScript
centerZ?: number
```

Z-axis anchor, that is, the z-component of the 3D rotation center point.

Default value: **0**.

Unit: px

Value range: (-∞, +∞).

**Type:** number

**Default:** 0

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## perspective

```TypeScript
perspective?: number
```

Z-axis coordinate of the camera. The value indicates the viewing distance, that is, the distance between the camera and the z=0 plane. The positive and negative values of the parameter determine the camera observation direction. When perspective is set to 0, the system automatically calculates a proper camera Z-axis position. The value is negative.

The rotation axis and center point are defined based on the [component coordinate system](../../../ui/arkui-glossary.md#component-coordinate-system). When the component moves, the coordinate system does not follow it.

Default value: **0**.

Unit: px

Value range: (-∞, +∞).

**Type:** number

**Default:** 0

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
