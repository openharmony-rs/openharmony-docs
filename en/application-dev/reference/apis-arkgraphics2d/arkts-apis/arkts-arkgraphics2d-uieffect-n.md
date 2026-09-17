# uiEffect

This module provides basic capabilities for component effects, including blur, brightening, and more. Effects are categorized into the Filter and VisualEffect classes, and effects of the same class can be cascaded under an instance of that effect class. Using this module, you can quickly implement complex visual effects without needing to master underlying image processing algorithms, reducing development complexity and improving user experience. In actual development, blur can be used for background blurring, and brightening can be used for bright screen display, etc.

- [Filter](arkts-arkgraphics2d-uieffect-filter-i.md): Used to add specified Filter effects to a component.  
- [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md): Used to add specified VisualEffect effects to a component.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createFilter](arkts-arkgraphics2d-uieffect-createfilter-f.md) | Creates a Filter instance for adding multiple filter effects to a component. |
| [createEffect](arkts-arkgraphics2d-uieffect-createeffect-f.md) | Creates a VisualEffect instance for adding multiple VisualEffect effects to a component. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createBrightnessBlender](arkts-arkgraphics2d-uieffect-createbrightnessblender-f-sys.md) | Creates a BrightnessBlender instance for adding a brightness effect to a component. |
| [createHdrBrightnessBlender](arkts-arkgraphics2d-uieffect-createhdrbrightnessblender-f-sys.md) | Creates an HdrBrightnessBlender instance for adding an HDR-enabled brightness effect to a component. |
| [createHdrDarkenBlender](arkts-arkgraphics2d-uieffect-createhdrdarkenblender-f-sys.md) | Creates an HdrDarkenBlender instance for HDR layer darken blending effect. |
| [createColorfulBrightnessBlender](arkts-arkgraphics2d-uieffect-createcolorfulbrightnessblender-f-sys.md) | Creates a ColorfulBrightnessBlender instance to add a hue-preserving brightening and darkening effect to a component. This effect preserves hue by reconstructing it channel by channel when brightening or darkening the foreground, and can enhance saturation to avoid the desaturation issue of common brightening/darkening. |
<!--DelEnd-->

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Mask effect class, used as input for Filter and VisualEffect. Different types of Mask provide different grayscale distribution patterns, such as wave ring masks, radial gradients, pixel map masks, etc. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Filter effect class, used to apply corresponding effects to specified components. Before calling Filter methods, you need to first create a Filter instance through createFilter. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i-sys.md) | Filter effect class, used to apply corresponding effects to specified components. Before calling Filter methods, you need to first create a Filter instance through createFilter. |
| [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md) | VisualEffect class, used to apply background color blending, border lighting, color gradient, and other effects to a component. Before calling VisualEffect methods, you need to first create a VisualEffect instance through createEffect. |
| [BrightnessParam](arkts-arkgraphics2d-uieffect-brightnessparam-i-sys.md) | Detailed description of the material brightness parameters. |
| [HeatDistortionEffectParam](arkts-arkgraphics2d-uieffect-heatdistortioneffectparam-i-sys.md) | The parameters of heat distortion effect. |
| [BlurBubblesRiseEffectParam](arkts-arkgraphics2d-uieffect-blurbubblesriseeffectparam-i-sys.md) | The parameters of blur bubbles rise effect. |
| [LiquidMaterialEffectParam](arkts-arkgraphics2d-uieffect-liquidmaterialeffectparam-i-sys.md) | Material effect parameters, used to control the display properties of the material such as refraction, reflection, perturbation, and overlay color. |
| [WarpedRingParam](arkts-arkgraphics2d-uieffect-warpedringparam-i-sys.md) | WarpedRingParam specifies the ring's radius, width, variation, rotation, 3D orientation and noise evolution. |
| [BrightnessBlender](arkts-arkgraphics2d-uieffect-brightnessblender-i-sys.md) | Brightness blender, used to add a brightness effect to a specified component. Before calling BrightnessBlender, you need to first create a BrightnessBlender instance through createBrightnessBlender. |
| [HdrBrightnessBlender](arkts-arkgraphics2d-uieffect-hdrbrightnessblender-i-sys.md) | HDR-enabled brightness blender (inherited from BrightnessBlender), used to add a brightness effect to a specified component. Before calling HdrBrightnessBlender, you need to first create an HdrBrightnessBlender instance through createHdrBrightnessBlender. The parameters of this blender can be referenced from BrightnessBlender. |
| [HdrDarkenBlender](arkts-arkgraphics2d-uieffect-hdrdarkenblender-i-sys.md) | HDR-adaptive darken blender, used to add a darken effect to a specified component. Before calling HdrDarkenBlender, you need to first create an HdrDarkenBlender instance through createHdrDarkenBlender. |
| [ColorfulBrightnessBlenderOptions](arkts-arkgraphics2d-uieffect-colorfulbrightnessblenderoptions-i-sys.md) | Optional enhanced configuration for the hue-preserving brightening and darkening blender, passed in as the options parameter of createColorfulBrightnessBlender. In addition to the regular BrightnessBlenderParam, it can be further fine-tuned for the brightening or darkening direction, color enhancement strength, input color influence, contrast against the background, and the HDR switch. If not passed, each item uses its default value. |
| [ColorfulBrightnessBlender](arkts-arkgraphics2d-uieffect-colorfulbrightnessblender-i-sys.md) | Hue-preserving brightening and darkening blender, used to add the brightening and darkening effect to a specified component. This effect preserves hue by reconstructing it channel by channel when brightening or darkening the foreground, and can enhance saturation to avoid the desaturation issue of common brightening/darkening; it also uses a luma difference threshold to ensure the contrast between the foreground and background. Before calling ColorfulBrightnessBlender, you need to first create a ColorfulBrightnessBlender instance through createColorfulBrightnessBlender. |
| [Color](arkts-arkgraphics2d-uieffect-color-i-sys.md) | RGBA color description. |
| [SweepRefractionParam](arkts-arkgraphics2d-uieffect-sweeprefractionparam-i-sys.md) | Required parameters for creating a SweepRefractionMask. |
| [SweepRefractionMaskOptions](arkts-arkgraphics2d-uieffect-sweeprefractionmaskoptions-i-sys.md) | Optional parameters for creating a SweepRefractionMask. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [Blender](arkts-arkgraphics2d-uieffect-blender-t-sys.md) | Blender type, used to describe the blending effect. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [TileMode](arkts-arkgraphics2d-uieffect-tilemode-e-sys.md) | Pixel fill mode enumeration. |
| [WaterRippleMode](arkts-arkgraphics2d-uieffect-waterripplemode-e-sys.md) | Water ripple scene mode enumeration. |
| [FlyMode](arkts-arkgraphics2d-uieffect-flymode-e-sys.md) | Fly-in or fly-out deformation scene mode enumeration. |
| [PrismShapeType](arkts-arkgraphics2d-uieffect-prismshapetype-e-sys.md) | Enumerates the prism shape types for SweepRefractionMask. |
<!--DelEnd-->
