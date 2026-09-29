# ShapeSize

```TypeScript
interface ShapeSize
```

Provides the size parameters of a shape.

**Since:** 12

<!--Device-unnamed-interface ShapeSize--><!--Device-unnamed-interface ShapeSize-End-->

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

If the type is number, the value range is [0, +∞); if the type is string, the value is specified by [Length](arkts-arkui-length-t.md).

Unit: vp

Default value: **0vp**

If an abnormal value is set, **0vp** is used.

If not set, the default value **0vp** is used.

**Type:** number &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ShapeSize-height?: number | string--><!--Device-ShapeSize-height?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: number | string
```

Width of the shape.

If the type is number, the value range is [0, +∞); if the type is string, the value is specified by [Length](arkts-arkui-length-t.md).

Unit: vp

Default value: **0vp**

If an abnormal value is set, **0vp** is used.

If not set, the default value **0vp** is used.

**Type:** number &#124; string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-ShapeSize-width?: number | string--><!--Device-ShapeSize-width?: number | string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
