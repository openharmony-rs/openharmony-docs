# SweepRefractionParam (System API)

Required parameters for creating a SweepRefractionMask.

**Since:** 26.1.0

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## chromaDelta

```TypeScript
chromaDelta: number
```

Chromatic dispersion delta. The value range is [0, 0.5], and values outside the range will be clamped during implementation.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## edgeThickness

```TypeScript
edgeThickness: number
```

Normalized edge thickness of the prism. The value range is [1, 1000], and values outside the range will be clamped during implementation.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## maskRadius

```TypeScript
maskRadius: number
```

Normalized radius of the prism mask. The value range is [0, 10], and values outside the range will be clamped during implementation. When the maskRadius is 1.0, it equals to the component height.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## refractAmount

```TypeScript
refractAmount: number
```

Refraction intensity of the prism. The value range is [0, 1], and values outside the range will be clamped during implementation.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## rippleWidth

```TypeScript
rippleWidth: number
```

Width of the sweep ripple. The value range is [0.01, 1], and values outside the range will be clamped during implementation.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## sweepOffset

```TypeScript
sweepOffset: number
```

Position offset of the sweep. The value range is [-2, 2], and values outside the range will be clamped during implementation.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
