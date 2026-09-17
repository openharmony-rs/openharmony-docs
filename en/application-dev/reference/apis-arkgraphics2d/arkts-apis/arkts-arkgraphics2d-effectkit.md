# @ohos.effectKit

The Image Effect module provides basic capabilities for processing images, including brightness adjustment, blurring, grayscale adjustment, and intelligent color picking. It is applicable to scenarios such as adding filter effects in image editing apps, blurring the background image of app startup pages, automatically extracting UI theme colors, and analyzing image color schemes.

This module is used for offline processing of image.PixelMap to obtain visual effects, while uiEffect (UI Effect Service) connects to the rendering service in real time to process screen frame buffers for dynamic visual effects.

This module provides the following classes:

- [Filter](arkts-arkgraphics2d-effectkit-filter-i.md): an effect class used to add a specified effect to the effect chain,  
enabling combined processing of multiple image effects through chained calls.  
- [Color](arkts-arkgraphics2d-effectkit-color-i.md): a class used to store the color picked.  
- [ColorPicker](arkts-arkgraphics2d-effectkit-colorpicker-i.md): a smart color picker.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md) | Creates a ColorPicker instance based on a pixel map. This API uses a promise to return the result. |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md) | Creates a ColorPicker instance for the selected region based on a pixel map. This API uses a promise to return the result. |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md) | Creates a ColorPicker instance based on a pixel map. This API uses an asynchronous callback to return the result. |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md) | Creates a ColorPicker instance for the selected region based on a pixel map. This API uses an asynchronous callback to return the result. |
| [createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md) | Creates a Filter instance based on the input PixelMap. You can then add various image effects through chained calls, and finally obtain the processed image via getEffectPixelMap. |

### Interfaces

| Name | Description |
| --- | --- |
| [Color](arkts-arkgraphics2d-effectkit-color-i.md) | A color class used to store the color picking result. It is suitable for scenarios such as obtaining the main color, the color with the largest proportion, and the color with the highest saturation from an image in conjunction with ColorPicker, helping developers conveniently obtain and pass image color picking results. |
| [ColorPicker](arkts-arkgraphics2d-effectkit-colorpicker-i.md) | A color picker class used to obtain the main color from image data. It is suitable for scenarios such as UI theme color extraction, image color scheme analysis, and intelligent color scheme recommendation, helping developers dynamically generate harmonious color schemes based on image content. Before calling the methods of ColorPicker, you need to create a ColorPicker instance via createColorPicker. |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | An image effect class used to add a specified effect to the effect chain through chained calls. It is suitable for scenarios such as image filter processing, visual effect enhancement, and image beautification. Before calling the methods of Filter, you need to create a Filter instance via createEffect. After adding effects, you need to call getEffectPixelMap to obtain the processed image. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ColorPicker](arkts-arkgraphics2d-effectkit-colorpicker-i-sys.md) | A color picker class used to obtain the main color from image data. It is suitable for scenarios such as UI theme color extraction, image color scheme analysis, and intelligent color scheme recommendation, helping developers dynamically generate harmonious color schemes based on image content. Before calling the methods of ColorPicker, you need to create a ColorPicker instance via createColorPicker. |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i-sys.md) | An image effect class used to add a specified effect to the effect chain through chained calls. It is suitable for scenarios such as image filter processing, visual effect enhancement, and image beautification. Before calling the methods of Filter, you need to create a Filter instance via createEffect. After adding effects, you need to call getEffectPixelMap to obtain the processed image. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [TileMode](arkts-arkgraphics2d-effectkit-tilemode-e.md) | Enumerates the tile modes of the shader effect. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [PictureComplexityDegree](arkts-arkgraphics2d-effectkit-picturecomplexitydegree-e-sys.md) | Enumerates the complexity degree of the image. |
| [PictureLightDegree](arkts-arkgraphics2d-effectkit-picturelightdegree-e-sys.md) | Enum for the brightness of image colors. |
| [PictureShadeDegree](arkts-arkgraphics2d-effectkit-pictureshadedegree-e-sys.md) | Enumerates the shade degrees of image colors. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [EllipticalMaskCenter](arkts-arkgraphics2d-effectkit-ellipticalmaskcenter-t-sys.md) | Defines the center point of the elliptical mask. |
| [EllipticalMaskRadius](arkts-arkgraphics2d-effectkit-ellipticalmaskradius-t-sys.md) | Defines the radius of the elliptical mask. |
<!--DelEnd-->
