# createColorfulBrightnessBlender (System API)

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## createColorfulBrightnessBlender

```TypeScript
function createColorfulBrightnessBlender(brightnessBlenderParam: BrightnessBlenderParam,
    options?: ColorfulBrightnessBlenderOptions): ColorfulBrightnessBlender
```

Creates a ColorfulBrightnessBlender instance to add a hue-preserving brightening and darkening effect to a component. This effect preserves hue by reconstructing it channel by channel when brightening or darkening the foreground, and can enhance saturation to avoid the desaturation issue of common brightening/darkening.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.2.0.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightnessBlenderParam | [BrightnessBlenderParam](arkts-arkgraphics2d-graphics-uieffect-brightnessblenderparam-i-sys.md) | Yes | Regular parameters for brightening and darkening, used to configure basic properties such as brightness mapping and saturation curves. |
| options | [ColorfulBrightnessBlenderOptions](arkts-arkgraphics2d-uieffect-colorfulbrightnessblenderoptions-i-sys.md) | No | Enhanced parameters for brightening and darkening, used to control the brightening/darkening direction, color enhancement strength, readability threshold, and HDR switch. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColorfulBrightnessBlender](arkts-arkgraphics2d-uieffect-colorfulbrightnessblender-i-sys.md) | Returns the hue-preserving brightening and darkening blender. |
