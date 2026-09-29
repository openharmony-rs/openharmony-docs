# RotateOption

```TypeScript
interface RotateOption
```

Describes the rotation parameters.

**Since:** 7

<!--Device-matrix4-interface RotateOption--><!--Device-matrix4-interface RotateOption-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## angle

```TypeScript
angle?: number
```

Rotation angle, which is used to set the rotation amount of the component around the rotation axis. Pass this parameter when the component needs to be rotated. If not passed, the component is not rotated.

Unit: degree (°)

Default value: **0**

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RotateOption-angle?: number--><!--Device-RotateOption-angle?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: number
```

Additional x-axis offset of the center point of a single matrix transformation operation relative to the component transform center point (anchor point).

Unit: px

Default value: **0**

**Note:** 

When the value is **0**, the matrix transformation center in the x direction is exactly the component anchor point in the x direction. The value indicates the additional offset relative to the component anchor point in the x direction. For details about the implementation, see [Example 3: Implementing Rotation Around a Center Point](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-transformation.md#example-3-implementing-rotation-around-a-center-point).

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RotateOption-centerX?: number--><!--Device-RotateOption-centerX?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number
```

Additional y-axis offset of the center point of a single matrix transformation operation relative to the component transform center point (anchor point).

Unit: px

Default value: **0**

**Note:** 

When the value is **0**, the matrix transformation center in the y direction is exactly the component anchor point in the y direction. The value indicates the additional offset relative to the component anchor point in the y direction. For details about the implementation, see [Example 3: Implementing Rotation Around a Center Point](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-transformation.md#example-3-implementing-rotation-around-a-center-point).

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RotateOption-centerY?: number--><!--Device-RotateOption-centerY?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

X-coordinate of the rotation axis vector, which specifies the component of the rotation axis in the x direction. Pass this parameter when rotating around an axis with an x component. If not passed, the x component of the rotation axis defaults to **0**.

**Note:** The rotation vector is meaningful only when at least one of x, y, and z is not 0.

Default value: **0**

Value range: (-∞, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RotateOption-x?: number--><!--Device-RotateOption-x?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

Y-coordinate of the rotation axis vector, which specifies the component of the rotation axis in the y direction. Pass this parameter when rotating around an axis with a y component. If not passed, the y component of the rotation axis defaults to **0**.

**Note:** The rotation vector is meaningful only when at least one of x, y, and z is not 0.

Default value: **0**

Value range: (-∞, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RotateOption-y?: number--><!--Device-RotateOption-y?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: number
```

Z-coordinate of the rotation axis vector, which specifies the component of the rotation axis in the z direction. Pass this parameter when rotating around an axis with a z component. If not passed, the z component of the rotation axis defaults to **0**.

Default value: **0**

Value range: (-∞, +∞).

**Note:** The rotation vector is meaningful only when at least one of x, y, and z is not 0; otherwise, no rotation effect is produced.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RotateOption-z?: number--><!--Device-RotateOption-z?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
