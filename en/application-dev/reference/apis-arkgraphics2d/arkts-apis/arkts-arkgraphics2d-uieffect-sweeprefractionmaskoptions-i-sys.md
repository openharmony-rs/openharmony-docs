# SweepRefractionMaskOptions (System API)

Optional parameters for creating a SweepRefractionMask.

**Since:** 26.1.0

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## cornerRadius

```TypeScript
cornerRadius?: number
```

Normalized corner radius of the prism shape, effective when shapeType is ROUNDED_RECT. The value range is [0, 1], and values outside the range will be clamped during implementation. When the cornerRadius is 1.0, it equals to the component height.

**Type:** number

**Default:** {0.16}

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## prismHeight

```TypeScript
prismHeight?: number
```

Normalized height of the prism. The value range is [0.01, 2], and values outside the range will be clamped during implementation. When the prismHeight is 1.0, it equals to the component height.

**Type:** number

**Default:** {1.0}

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## prismWidth

```TypeScript
prismWidth?: number
```

Normalized width of the prism. The value range is [0.01, 2], and values outside the range will be clamped during implementation. When the prismWidth is 1.0, it equals to the component width.

**Type:** number

**Default:** {1.0}

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## shapeType

```TypeScript
shapeType?: PrismShapeType
```

Prism shape type.

**Type:** [PrismShapeType](arkts-arkgraphics2d-uieffect-prismshapetype-e-sys.md)

**Default:** {PrismShapeType.ROUNDED_RECT}

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## sweepCenterX

```TypeScript
sweepCenterX?: number
```

Normalized X coordinate of the sweep center. The value range is [0, 1], and values outside the range will be clamped during implementation. 0.0 refers to the left edge, 1.0 refers to the right edge, default value is 0.0.

**Type:** number

**Default:** {0.0}

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## sweepCenterY

```TypeScript
sweepCenterY?: number 
```

Normalized Y coordinate of the sweep center. The value range is [0, 1], and values outside the range will be clamped during implementation. 0.0 refers to the top edge, 1.0 refers to the bottom edge, default value is 0.0.

**Type:** number

**Default:** {0.0}

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
