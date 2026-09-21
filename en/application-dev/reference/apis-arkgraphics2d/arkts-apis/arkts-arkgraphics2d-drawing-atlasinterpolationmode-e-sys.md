# AtlasInterpolationMode (System API)

```TypeScript
enum AtlasInterpolationMode
```

Defines the interpolation mode for sprite sheet frame animation.

**Since:** 26.0.1

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## NONE

```TypeScript
NONE = 0
```

No interpolation. Each frame is displayed independently as a discrete step.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## FRAME_BLEND

```TypeScript
FRAME_BLEND = 1
```

Inter-frame interpolation. Smooth transition between adjacent frames.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
