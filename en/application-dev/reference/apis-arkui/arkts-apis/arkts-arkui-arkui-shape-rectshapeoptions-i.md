# RectShapeOptions

```TypeScript
interface RectShapeOptions extends ShapeSize
```

Represents the parameter of the constructor used to create a **RectShape** object.

This API inherits from [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md).

**Inheritance/Implementation:** RectShapeOptions extends [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md)

**Since:** 12

<!--Device-unnamed-interface RectShapeOptions extends ShapeSize--><!--Device-unnamed-interface RectShapeOptions extends ShapeSize-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## radius

```TypeScript
radius?: number | string | Array<number | string>
```

Radius of the rectangle border corners.

If the type is number, the value range is [0, +∞); if the type is string, the value is specified by [Length](arkts-arkui-length-t.md).

Unit: vp

If the value is invalid, 0 vp is used.

**Type:** number &#124; string &#124; Array&lt;number &#124; string&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-RectShapeOptions-radius?: number | string | Array<number | string>--><!--Device-RectShapeOptions-radius?: number | string | Array<number | string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
