# ShapeSize

Describes the size of a shape.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## height

```TypeScript
height?: number | string
```

Height of the shape.

When the parameter type is number, the valid value range is [0, +∞). When the parameter type is string, the value must conform to the [Length](arkts-arkui-length-t.md) type specification.

Unit: vp.

If the value is invalid, 0 vp is used.

**Type:** number &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: number | string
```

Width of the shape.

When the parameter type is number, the valid value range is [0, +∞). When the parameter type is string, the value must conform to the [Length](arkts-arkui-length-t.md) type specification.

Unit: vp.

If the value is invalid, 0 vp is used.

**Type:** number &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
