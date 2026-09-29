# RoundRectShapeOptions

```TypeScript
interface RoundRectShapeOptions extends ShapeSize
```

Represents the parameters of the constructor used to create a **RectShape** object with rounded corners.

This API inherits from [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md).

**Inheritance/Implementation:** RoundRectShapeOptions extends [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md)

**Since:** 12

<!--Device-unnamed-interface RoundRectShapeOptions extends ShapeSize--><!--Device-unnamed-interface RoundRectShapeOptions extends ShapeSize-End-->

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

If the type is number, the value range is [0, +∞); if the type is string, the value is specified by [Length](arkts-arkui-length-t.md).

Unit: vp

Default value: **0vp**

If an abnormal value is set, **0vp** is used.

**Type:** number &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-RoundRectShapeOptions-radiusHeight?: number | string--><!--Device-RoundRectShapeOptions-radiusHeight?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radiusWidth

```TypeScript
radiusWidth?: number | string
```

Radius width of the rectangle border corners.

If the type is number, the value range is [0, +∞); if the type is string, the value is specified by [Length](arkts-arkui-length-t.md).

Unit: vp

Default value: **0vp**

If an abnormal value is set, **0vp** is used.

**Type:** number &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-RoundRectShapeOptions-radiusWidth?: number | string--><!--Device-RoundRectShapeOptions-radiusWidth?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
