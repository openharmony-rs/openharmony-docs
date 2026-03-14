# Constants
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 常量

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

| 名称                               | 类型   | 值   | 说明                                                         |
| ---------------------------------- | ------ | ---- | ------------------------------------------------------------ |
| XMAGE_WATERMARK_MODE_AT_THE_BOTTOM | ArkTS-Dyn: number<br>ArkTS-Sta: int | 9    | XMAGE水印固定位于图像底部中央。 |
| XMAGE_WATERMARK_MODE_BORDER        | ArkTS-Dyn: number<br>ArkTS-Sta: int | 10   | XMAGE水印会自动调整到边界位置，系统根据图像内容选择最适合的边界区域。 |
| CAPTURE_MODE_PROFESSIONAL | ArkTS-Dyn: number<br>ArkTS-Sta: int | 2    | 拍摄模式：专业模式。 |
| CAPTURE_MODE_FRONT_LENS_NIGHT_VIEW | ArkTS-Dyn: number<br>ArkTS-Sta: int | 7    | 拍摄模式：前置摄像头夜景模式。 |
| CAPTURE_MODE_PANORAMA | ArkTS-Dyn: number<br>ArkTS-Sta: int | 8    | 拍摄模式：全景模式。 |
| CAPTURE_MODE_TAIL_LIGHT | ArkTS-Dyn: number<br>ArkTS-Sta: int | 9 | 拍摄模式：尾灯模式。 |
| CAPTURE_MODE_LIGHT_GRAFFITI | ArkTS-Dyn: number<br>ArkTS-Sta: int | 10   | 拍摄模式：轻涂鸦模式。 |
| CAPTURE_MODE_SILKY_WATER | ArkTS-Dyn: number<br>ArkTS-Sta: int | 11   | 拍摄模式：缎面感水流模式。 |
| CAPTURE_MODE_STAR_TRACK | ArkTS-Dyn: number<br>ArkTS-Sta: int | 12   | 拍摄模式：星轨模式。 |
| CAPTURE_MODE_WIDEAPERTURE | ArkTS-Dyn: number<br>ArkTS-Sta: int | 19   | 拍摄模式：广角模式。 |
| CAPTURE_MODE_MOVING_PHOTO | ArkTS-Dyn: number<br>ArkTS-Sta: int | 20 | 拍摄模式：动态照片模式。 |
| CAPTURE_MODE_PORTRAIT | ArkTS-Dyn: number<br>ArkTS-Sta: int | 23   | 拍摄模式：人像模式。 |
| CAPTURE_MODE_REAR_LENS_NIGHT_VIEW | ArkTS-Dyn: number<br>ArkTS-Sta: int | 42   | 拍摄模式：后镜头夜景模式。 |
| CAPTURE_MODE_SUPER_MACRO | ArkTS-Dyn: number<br>ArkTS-Sta: int | 47   | 拍摄模式：超微距模式。 |
| CAPTURE_MODE_SNAP_SHOT | ArkTS-Dyn: number<br>ArkTS-Sta: int | 62   | 拍摄模式：抓拍模式。 |

**示例：**

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

