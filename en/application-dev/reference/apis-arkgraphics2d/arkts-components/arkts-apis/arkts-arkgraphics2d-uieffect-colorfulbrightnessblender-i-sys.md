# ColorfulBrightnessBlender (System API)

```TypeScript
interface ColorfulBrightnessBlender
```

Hue-preserving brightening and darkening blender, used to add the brightening and darkening effect to a specified component. This effect preserves hue by reconstructing it channel by channel when brightening or darkening the foreground, and can enhance saturation to avoid the desaturation issue of common brightening/darkening; it also uses a luma difference threshold to ensure the contrast between the foreground and background. Before calling ColorfulBrightnessBlender, you need to first create a ColorfulBrightnessBlender instance through createColorfulBrightnessBlender.

**Since:** 26.2.0

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## brightnessBlenderParam

```TypeScript
brightnessBlenderParam: BrightnessBlenderParam
```

Regular parameters for brightening and darkening, used to configure basic properties such as brightness mapping and saturation curves.

**Type:** [BrightnessBlenderParam](arkts-arkgraphics2d-graphics-uieffect-brightnessblenderparam-i-sys.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## options

```TypeScript
options?: ColorfulBrightnessBlenderOptions
```

Enhanced parameters for brightening and darkening, used to control the brightening/darkening direction, color enhancement strength, readability threshold, and HDR switch.

**Type:** [ColorfulBrightnessBlenderOptions](arkts-arkgraphics2d-uieffect-colorfulbrightnessblenderoptions-i-sys.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
