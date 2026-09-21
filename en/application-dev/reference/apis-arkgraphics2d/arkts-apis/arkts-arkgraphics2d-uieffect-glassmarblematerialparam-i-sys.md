# GlassMarbleMaterialParam (System API)

```TypeScript
interface GlassMarbleMaterialParam
```

Material parameters for the glass marble. Controls material properties (background color, opacity, reflection map, shadow, caustic) and shape scaling.

**Since:** 26.0.1

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## averageBgColor

```TypeScript
averageBgColor: Color
```

Average background color. The alpha channel is not used.

**Type:** Color

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## causticEdgeSoftness

```TypeScript
causticEdgeSoftness: number
```

Edge softness of the caustic (focused light). The value range is [0, 1]; a value of 0 produces a hard edge, and 1 produces a fully soft edge. Out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## causticOffset

```TypeScript
causticOffset: number
```

Vertical offset of the caustic (focused light), normalized to the shape radius. The value range is [-1, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## causticOpacity

```TypeScript
causticOpacity: number
```

Overall opacity of the caustic (focused light). The value range is [0, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## causticRadius

```TypeScript
causticRadius: number
```

Radius of the caustic (focused light), normalized to the shape radius. The value range is [0, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## opacity

```TypeScript
opacity: number
```

Overall opacity of the glass effect. The value range is [0, 1]; a value of 0 is fully transparent, 1 is fully opaque. Out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## reflectionMap

```TypeScript
reflectionMap: image.PixelMap
```

Reflection map used for environment reflections on the glass surface. Created through the image module as a PixelMap instance.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## shadowEdgeSoftness

```TypeScript
shadowEdgeSoftness: number
```

Edge softness of the shadow. The value range is [0, 1]; a value of 0 produces a hard edge, and 1 produces a fully soft edge. Out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## shadowOffset

```TypeScript
shadowOffset: number
```

Vertical offset of the shadow, normalized to the shape radius. The value range is [-1, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## shadowOpacity

```TypeScript
shadowOpacity: number
```

Overall opacity of the shadow. The value range is [0, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## shadowRadius

```TypeScript
shadowRadius: number
```

Radius of the shadow, normalized to the shape radius. The value range is [0, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## shapeScale

```TypeScript
shapeScale: number
```

Scaling factor applied to the glass shape. The value range is [0, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
