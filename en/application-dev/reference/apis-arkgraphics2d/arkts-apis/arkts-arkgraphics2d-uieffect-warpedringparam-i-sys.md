# WarpedRingParam (System API)

WarpedRingParam specifies the ring's radius, width, variation, rotation, 3D orientation and noise evolution.

**Since:** 26.1.0

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## baseHalfWidth

```TypeScript
baseHalfWidth: number
```

Defines half the ring's thickness, measured from the centerline to either edge. The value is unrestricted, with a recommended range of [0, 0.5]. Values below 0 have no meaningful effect. When adjusting the effect, a step size of 0.01 is recommended for better results.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## noiseEvolution

```TypeScript
noiseEvolution: number
```

Defines the evolution of the noise pattern over time. The value is unrestricted, animate this value continuously to produce dynamic noise.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## radius

```TypeScript
radius: number
```

Defines the ring radius, measured from the ring's center to the midpoint of its thickness. The value is unrestricted, with a recommended range of [0, 1]. Values below 0 have no meaningful effect. When set to 1, the ring's diameter equals the minimum of the component's width and height.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## rotate3DProgress

```TypeScript
rotate3DProgress: number
```

Defines the progress of the ring's 3D orientation cycle. The input value is reduced modulo 1 to the range [0, 1). A value of 0 represents the original position, while 1 represents the position after one full rotation.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## rotateAngle

```TypeScript
rotateAngle: number
```

Defines the angle by which the ring is rotated around its center. The value is unrestricted, with a recommended range of [-2π, 2π]. Positive values rotate clockwise, while negative values rotate counterclockwise. When animated together with noiseEvolution, it makes the noise flow along the ring’s circumference.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## widthVariation

```TypeScript
widthVariation: number
```

Defines the amount of variation along the ring's circumference. The value is unrestricted, with a recommended range of [0, 1]. Values below 0 have no meaningful effect. Values closer to 0 produce a more circular ring.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
