# GlassMarbleSphereParam (System API)

```TypeScript
interface GlassMarbleSphereParam
```

Sphere shape parameters for the glass marble. Defines the geometry of the glass shape through a center position and a radius, all in normalized coordinates relative to the component bounds.

**Since:** 26.0.1

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## center

```TypeScript
center: [number, number]
```

Normalized center position of the sphere shape. [0, 0] represents the top-left corner and [1, 1] represents the bottom-right corner of the component bounds. Values outside [0, 1] will be clamped internally.

**Type:** [number, number]

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## radius

```TypeScript
radius: number
```

Normalized radius of the sphere shape. The value range is [0, 1]; out-of-range values will be clamped internally. A value of 1 means the sphere diameter equals the minimum of the component's width and height.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
