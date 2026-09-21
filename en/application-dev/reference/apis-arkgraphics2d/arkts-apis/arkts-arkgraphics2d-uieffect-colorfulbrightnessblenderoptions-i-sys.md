# ColorfulBrightnessBlenderOptions (System API)

```TypeScript
interface ColorfulBrightnessBlenderOptions
```

Optional enhanced configuration for the hue-preserving brightening and darkening blender, passed in as the options parameter of createColorfulBrightnessBlender. In addition to the regular BrightnessBlenderParam, it can be further fine-tuned for the brightening or darkening direction, color enhancement strength, input color influence, contrast against the background, and the HDR switch. If not passed, each item uses its default value.

**Since:** 26.2.0

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## darkenWeight

```TypeScript
darkenWeight?: number
```

Foreground darken weight, which controls the direction and strength of brightening/darkening. When set to 0, the foreground is brightened, the foreground tends to be brighter than the background to ensure readability; when set to 1, the foreground is darkened, the foreground tends to be darker than the background; values between 0 and 1 are a transition between brightening and darkening. The default value is 1. The value range is [0, 1], and values outside the range will be clamped during implementation.

**Type:** number

**Default:** 1

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## hdrEnabled

```TypeScript
hdrEnabled?: boolean
```

Whether to actively enable HDR. When set to true, HDR is actively enabled and the resulting brightness can exceed the SDR range (&gt;1.0), presenting higher brightness on HDR devices, suitable for HDR content; when set to false, HDR is not actively enabled and the result is limited to the SDR range (≤1.0), but HDR may still be passively triggered when the foreground or background itself is HDR. The default value is false.

**Type:** boolean

**Default:** false

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## lumaDiff

```TypeScript
lumaDiff?: number
```

Luma difference threshold to ensure readability, used to constrain the luma difference between the foreground and background to maintain sufficient contrast. When set to 0, no additional luma difference is enforced, the weakest readability constraint; the larger the value, the larger the enforced luma difference and the stronger the contrast; when set to 1, the maximum luma difference is enforced. The default value is 0. The value range is [0, 1], and values outside the range will be clamped during implementation.

**Type:** number

**Default:** 0

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## tintedColorPercent

```TypeScript
tintedColorPercent?: number
```

Input color influence, which controls the degree to which the input color participates in the brightening/darkening calculation. When set to 1, the input color fully participates in the calculation and the output result retains the color tendency of the input color; when set to 0, the input color does not participate in the calculation and the output result is not affected by the input color, performing brightening/darkening directly based on the background color; values between 0 and 1 are an interpolation transition between the two. The default value is 1. The value range is [0, 1], and values outside the range will be clamped during implementation.

**Type:** number

**Default:** 1

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## vibrancyStrength

```TypeScript
vibrancyStrength?: number
```

Color enhancement strength, which controls the degree of saturation enhancement for the foreground. When set to 0, no additional saturation is enhanced and the foreground retains its original saturation; the larger the value, the more obvious the saturation enhancement. When set to 1, the enhancement reaches its maximum and the colors are most vivid. The default value is 0. The value range is [0, 1], and values outside the range will be clamped during implementation.

**Type:** number

**Default:** 0

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
