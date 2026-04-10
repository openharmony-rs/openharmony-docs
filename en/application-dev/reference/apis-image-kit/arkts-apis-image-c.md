# Constants
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name                              | Type  | Value  | Description                                                        |
| ---------------------------------- | ------ | ---- | ------------------------------------------------------------ |
| XMAGE_WATERMARK_MODE_AT_THE_BOTTOM | number | 9    | The XMAGE watermark is fixed at the bottom center of the image.|
| XMAGE_WATERMARK_MODE_BORDER        | number | 10   | The XMAGE watermark automatically adjusts to a boundary position, with the system selecting the most suitable boundary area based on the image content.|
| CAPTURE_MODE_PROFESSIONAL | number | 2    | Capture mode: professional.|
| CAPTURE_MODE_FRONT_LENS_NIGHT_VIEW | number | 7    | Capture mode: front camera night mode.|
| CAPTURE_MODE_PANORAMA | number | 8    | Capture mode: panorama.|
| CAPTURE_MODE_TAIL_LIGHT | number | 9 | Capture mode: tail light.|
| CAPTURE_MODE_LIGHT_GRAFFITI | number | 10   | Capture mode: light graffiti.|
| CAPTURE_MODE_SILKY_WATER | number | 11   | Capture mode: silky water flow.|
| CAPTURE_MODE_STAR_TRACK | number | 12   | Capture mode: star track.|
| CAPTURE_MODE_WIDEAPERTURE | number | 19   | Capture mode: wide-angle.|
| CAPTURE_MODE_MOVING_PHOTO | number | 20 | Capture mode: moving photo.|
| CAPTURE_MODE_PORTRAIT | number | 23   | Capture mode: portrait.|
| CAPTURE_MODE_REAR_LENS_NIGHT_VIEW | number | 42   | Capture mode: rear camera night mode.|
| CAPTURE_MODE_SUPER_MACRO | number | 47   | Capture mode: super-macro.|
| CAPTURE_MODE_SNAP_SHOT | number | 62   | Capture mode: snapshot.|

**Example**:

```ts
import { image } from '@kit.ImageKit';

const defaultXmageWaterMarkModeAtTheBottom = image.XMAGE_WATERMARK_MODE_AT_THE_BOTTOM;
const defaultXmageWaterMarkModeBorder = image.XMAGE_WATERMARK_MODE_BORDER;
const defaultCaptureModeProfessional = image.CAPTURE_MODE_PROFESSIONAL;
const defaultCaptureModeFrontLensNightView = image.CAPTURE_MODE_FRONT_LENS_NIGHT_VIEW;
const defaultCaptureModePanorama = image.CAPTURE_MODE_PANORAMA;
const defaultCaptureModeTailLight = image.CAPTURE_MODE_TAIL_LIGHT;
const defaultCaptureModeLightGraffiti = image.CAPTURE_MODE_LIGHT_GRAFFITI;
const defaultCaptureModeSilkyWater = image.CAPTURE_MODE_SILKY_WATER;
const defaultCaptureModeStarTrack = image.CAPTURE_MODE_STAR_TRACK;
const defaultCaptureModeWideAperture = image.CAPTURE_MODE_WIDEAPERTURE;
const defaultCaptureModeMovingPhoto = image.CAPTURE_MODE_MOVING_PHOTO;
const defaultCaptureModePortrait = image.CAPTURE_MODE_PORTRAIT;
const defaultCaptureModeRearLensNightView = image.CAPTURE_MODE_REAR_LENS_NIGHT_VIEW;
const defaultCaptureModeSuperMacro = image.CAPTURE_MODE_SUPER_MACRO;
const defaultCaptureModeSnapShot = image.CAPTURE_MODE_SNAP_SHOT;
```
