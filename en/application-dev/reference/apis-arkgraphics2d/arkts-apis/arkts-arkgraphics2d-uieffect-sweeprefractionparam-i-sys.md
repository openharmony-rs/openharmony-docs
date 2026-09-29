# SweepRefractionParam (System API)

```TypeScript
interface SweepRefractionParam
```

Required parameters for creating a SweepRefractionMask.

**Since:** 26.0.1

<!--Device-uiEffect-interface SweepRefractionParam--><!--Device-uiEffect-interface SweepRefractionParam-End-->

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

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SweepRefractionParam-chromaDelta: double--><!--Device-SweepRefractionParam-chromaDelta: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## edgeThickness

```TypeScript
edgeThickness: number
```

Normalized edge thickness of the prism. The value range is [1, 1000], and values outside the range will be clamped during implementation.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SweepRefractionParam-edgeThickness: double--><!--Device-SweepRefractionParam-edgeThickness: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## maskRadius

```TypeScript
maskRadius: number
```

Normalized radius of the prism mask. The value range is [0, 10], and values outside the range will be clamped during implementation. When the maskRadius is 1.0, it equals to the component height.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SweepRefractionParam-maskRadius: double--><!--Device-SweepRefractionParam-maskRadius: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## refractAmount

```TypeScript
refractAmount: number
```

Refraction intensity of the prism. The value range is [0, 1], and values outside the range will be clamped during implementation.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SweepRefractionParam-refractAmount: double--><!--Device-SweepRefractionParam-refractAmount: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## rippleWidth

```TypeScript
rippleWidth: number
```

Width of the sweep ripple. The value range is [0.01, 1], and values outside the range will be clamped during implementation.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SweepRefractionParam-rippleWidth: double--><!--Device-SweepRefractionParam-rippleWidth: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## sweepOffset

```TypeScript
sweepOffset: number
```

Position offset of the sweep. The value range is [-2, 2], and values outside the range will be clamped during implementation.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SweepRefractionParam-sweepOffset: double--><!--Device-SweepRefractionParam-sweepOffset: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
