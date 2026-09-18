# RoundRectShapeOptions

Represents the parameter of the constructor used to create a **RectShape** object with rounded corners.

This API inherits from [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md).

**Inheritance/Implementation:** RoundRectShapeOptions extends [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## radiusHeight

```TypeScript
radiusHeight?: number | string
```

Radius height of the rectangle border corners.

When the parameter type is number, the valid value range is [0, +∞). When the parameter type is string, the value must conform to the [Length](arkts-arkui-length-t.md) type specification.

Unit: vp.

If the value is invalid, 0 vp is used.

**Type:** number &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radiusWidth

```TypeScript
radiusWidth?: number | string
```

Radius width of the rectangle border corners.

When the parameter type is number, the valid value range is [0, +∞). When the parameter type is string, the value must conform to the [Length](arkts-arkui-length-t.md) type specification.

Unit: vp.

If the value is invalid, 0 vp is used.

**Type:** number &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
