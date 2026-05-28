# Class (PngMetadata)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

PngMetadata.

PNG image metadata class, which is used to store image metadata.

**Since**: 26.0.0

## Modules to Import

```ts
import { image } from '@kit.ImageKit';
```

## Properties

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name                        | Type  | Read-Only| Optional| Description                                      |
| ---------------------------- | ------ | ---- | ---- | ------------------------------------------ |
| xPixelsPerMeter | number | Yes  | Yes  | Number of pixels per meter in the X direction of a PNG image.<br>The value is a positive integer.|
| software | string | Yes  | Yes  | Name and version number of the software used to create PNG images.|
| disclaimer | string | Yes  | Yes  | Disclaimer of a PNG image.|
| description | string | Yes  | Yes  | Description of a PNG image.|
| copyright | string | Yes  | Yes  | Copyright notice of a PNG image.|
| interlaceType | number | Yes  | Yes  | Interlace mode of a PNG image.<br>- **0**: no interlace mode. (The image is loaded sequentially from top to bottom and left to right.)<br>- **1**: interlace mode. (The image is displayed progressively through multiple scans, becoming clearer as loading proceeds.)|
| comment | string | Yes  | Yes  | Comment of a PNG image.|
| author | string | Yes  | Yes  | Author of a PNG image.|
| creationTime | string | Yes  | Yes  | Creation time of a PNG image.|
| modificationTime | string | Yes  | Yes  | Last modification time of a PNG image.|
| gamma | number | Yes  | Yes  | Gamma value of a PNG image.|
| yPixelsPerMeter | number | Yes  | Yes  | Number of pixels per meter in the Y direction of a PNG image.<br>The value is a positive integer.|
| sRGBIntent | number | Yes  | Yes  | Standard Red Green Blue (sRGB) rendering intent of a PNG image.<br>- **0**: perceptual intent<br>- **1**: relative colorimetric intent<br>- **2**: saturation intent<br>- **3**: absolute colorimetric intent|
| title | string | Yes  | Yes  | Title of a PNG image.|
| warning | string | Yes  | Yes  | Warning information of a PNG image.|
