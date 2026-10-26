# RectLight

```TypeScript
export interface RectLight extends Light
```

Rectangular area light.

A rect light emits light from a rectangular area, simulating soft area lighting effects from one side of the rectangle by default. When twoSided is enabled, light is emitted from both sides.

**Inheritance/Implementation:** RectLight extends [Light](arkts-arkgraphics3d-scenenodes-light-i.md)

**Since:** 26.1.0

<!--Device-unnamed-export interface RectLight extends Light--><!--Device-unnamed-export interface RectLight extends Light-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## height

```TypeScript
height?: number
```

Height of the rectangular light emitting surface. The unit is the scene unit (such as cm, m, and km) in the world coordinate system. The value must be greater than 0.

**Type:** number

**Default:** 1.0

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RectLight-height?: double--><!--Device-RectLight-height?: double-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## twoSided

```TypeScript
twoSided?: boolean
```

Whether the rect light emits light from both sides of the rectangle. true if two-sided, false otherwise. When set to false, light is emitted only from the front side (determined by the node's rotation). Default value: Default value: false.

**Type:** boolean

**Default:** false

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RectLight-twoSided?: boolean--><!--Device-RectLight-twoSided?: boolean-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## width

```TypeScript
width?: number
```

Width of the rectangular light emitting surface. The unit is the scene unit (such as cm, m, and km) in the world coordinate system. Default value: Default value: 1.

**Type:** number

**Default:** 1.0

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RectLight-width?: double--><!--Device-RectLight-width?: double-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D
