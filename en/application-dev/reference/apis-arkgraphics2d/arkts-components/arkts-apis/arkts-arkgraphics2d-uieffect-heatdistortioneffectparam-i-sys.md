# HeatDistortionEffectParam (System API)

The parameters of heat distortion effect.

**Since:** 26.0.0

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## intensity

```TypeScript
intensity: number
```

The intensity of the heat distortion. The value range is [0, 1], and values outside the range will be clamped during implementation. 0 means no distortion, and 1 represents the maximum distortion level.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## noiseScale

```TypeScript
noiseScale: number
```

The noise scale of the heat distortion, controlling the fineness of the noise texture. The value range is [0.1, 5.0], and values outside the range will be clamped during implementation. A larger value results in a finer noise texture.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## progress

```TypeScript
progress: number
```

The animation progress of the heat distortion. The value range is [0, 1], and values outside the range will be clamped during implementation. 0 corresponds to the start of the animation, and 1 corresponds to the end of the animation.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## riseWeight

```TypeScript
riseWeight: number
```

The rise weight of the heat distortion, controlling the rising speed of bubbles. The value range is [0, 1], and values outside the range will be clamped during implementation. A larger value results in more obvious upward movement.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
