# GlassMarbleContentParam (System API)

```TypeScript
interface GlassMarbleContentParam
```

Content parameters for the glass marble. Controls how the content mask is blended inside the glass shape, including the content mask itself, tint color, scaling, saturation, and chromatic dispersion.

**Since:** 26.0.1

<!--Device-uiEffect-interface GlassMarbleContentParam--><!--Device-uiEffect-interface GlassMarbleContentParam-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## contentDispersion

```TypeScript
contentDispersion: number
```

Chromatic dispersion of the content blended inside the glass shape. Controls the color separation at the content edges. The value range is [0, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-GlassMarbleContentParam-contentDispersion: double--><!--Device-GlassMarbleContentParam-contentDispersion: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## contentMask

```TypeScript
contentMask: Mask
```

Content mask to blend additional content inside the glass shape. When provided, the content mask is sampled and composited with the glass material.

**Type:** [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-GlassMarbleContentParam-contentMask: Mask--><!--Device-GlassMarbleContentParam-contentMask: Mask-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## contentSaturation

```TypeScript
contentSaturation: number
```

Saturation of the content blended inside the glass shape. The value range is [0, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-GlassMarbleContentParam-contentSaturation: double--><!--Device-GlassMarbleContentParam-contentSaturation: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## contentScale

```TypeScript
contentScale: number
```

Scaling factor applied to the content blended inside the glass shape. The value range is [0, 1]; out-of-range values will be clamped internally.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-GlassMarbleContentParam-contentScale: double--><!--Device-GlassMarbleContentParam-contentScale: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## contentTintColor

```TypeScript
contentTintColor: Color
```

Tint color applied to the content blended inside the glass shape. The alpha channel is used as the mix coefficient between the original content color and the tint color.

**Type:** Color

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-GlassMarbleContentParam-contentTintColor: Color--><!--Device-GlassMarbleContentParam-contentTintColor: Color-End-->

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
