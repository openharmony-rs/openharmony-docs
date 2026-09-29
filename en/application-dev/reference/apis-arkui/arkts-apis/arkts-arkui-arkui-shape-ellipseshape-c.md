# EllipseShape

```TypeScript
export declare class EllipseShape extends BaseShape<EllipseShape>
```

Represents an ellipse shape used in the **clipShape** and **maskShape** APIs.

This API inherits from [BaseShape](arkts-arkui-arkui-shape-baseshape-c.md).

**Inheritance/Implementation:** EllipseShape extends BaseShape<EllipseShape>

**Since:** 12

<!--Device-unnamed-export declare class EllipseShape extends BaseShape<EllipseShape>--><!--Device-unnamed-export declare class EllipseShape extends BaseShape<EllipseShape>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ShapeSize)
```

A constructor used to create an **EllipseShape** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-EllipseShape-constructor(options?: ShapeSize)--><!--Device-EllipseShape-constructor(options?: ShapeSize)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ShapeSize](arkts-arkui-arkui-shape-shapesize-i.md) | No | Size of the shape, which is used to customize the width and height of the ellipse. If not specified, the default value of **width** and **height** is 0 vp. |
