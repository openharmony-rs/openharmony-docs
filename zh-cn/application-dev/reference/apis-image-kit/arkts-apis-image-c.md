# Constants
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```

## 常量

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

| 名称                               | 类型   | 值   | 说明                                                         |
| ---------------------------------- | ------ | ---- | ------------------------------------------------------------ |
| XMAGE_WATERMARK_MODE_AT_THE_BOTTOM | ArkTS-Dyn: number<br>ArkTS-Sta: int | 9    | XMAGE水印模式：XMAGE水印固定位于图像底部中央。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| XMAGE_WATERMARK_MODE_BORDER        | ArkTS-Dyn: number<br>ArkTS-Sta: int | 10   | XMAGE水印模式：XMAGE水印会自动调整到边界位置，系统根据图像内容选择最适合的边界区域。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_PROFESSIONAL | ArkTS-Dyn: number<br>ArkTS-Sta: int | 2    | 拍摄模式：专业模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_FRONT_LENS_NIGHT_VIEW | ArkTS-Dyn: number<br>ArkTS-Sta: int | 7    | 拍摄模式：前置摄像头夜景模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_PANORAMA | ArkTS-Dyn: number<br>ArkTS-Sta: int | 8    | 拍摄模式：全景模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_TAIL_LIGHT | ArkTS-Dyn: number<br>ArkTS-Sta: int | 9 | 拍摄模式：尾灯模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_LIGHT_GRAFFITI | ArkTS-Dyn: number<br>ArkTS-Sta: int | 10   | 拍摄模式：轻涂鸦模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_SILKY_WATER | ArkTS-Dyn: number<br>ArkTS-Sta: int | 11   | 拍摄模式：缎面感水流模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_STAR_TRACK | ArkTS-Dyn: number<br>ArkTS-Sta: int | 12   | 拍摄模式：星轨模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_WIDEAPERTURE | ArkTS-Dyn: number<br>ArkTS-Sta: int | 19   | 拍摄模式：广角模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_MOVING_PHOTO | ArkTS-Dyn: number<br>ArkTS-Sta: int | 20 | 拍摄模式：动态照片模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_PORTRAIT | ArkTS-Dyn: number<br>ArkTS-Sta: int | 23   | 拍摄模式：人像模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_REAR_LENS_NIGHT_VIEW | ArkTS-Dyn: number<br>ArkTS-Sta: int | 42   | 拍摄模式：后镜头夜景模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_SUPER_MACRO | ArkTS-Dyn: number<br>ArkTS-Sta: int | 47   | 拍摄模式：超微距模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| CAPTURE_MODE_SNAP_SHOT | ArkTS-Dyn: number<br>ArkTS-Sta: int | 62   | 拍摄模式：抓拍模式。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |
| XMP_BASIC   | [XMPNamespace](arkts-apis-image-i.md#xmpnamespace) | uri: "`http://ns.adobe.com/xap/1.0/`"<br>prefix: "xmp"              | XMP基础命名空间。</br>**ArkTS-Dyn起始版本：** 26.0.0</br>**ArkTS-Sta起始版本：** 26.0.0 |
| XMP_RIGHTS  | [XMPNamespace](arkts-apis-image-i.md#xmpnamespace) | uri: "`http://ns.adobe.com/xap/1.0/rights/`"<br>prefix: "xmpRights" | XMP版权与权限命名空间。</br>**ArkTS-Dyn起始版本：** 26.0.0</br>**ArkTS-Sta起始版本：** 26.0.0 |
| EXIF        | [XMPNamespace](arkts-apis-image-i.md#xmpnamespace) | uri: "`http://ns.adobe.com/exif/1.0/`"<br>prefix: "exif"            | EXIF元数据命名空间。</br>**ArkTS-Dyn起始版本：** 26.0.0</br>**ArkTS-Sta起始版本：** 26.0.0 |
| DUBLIN_CORE | [XMPNamespace](arkts-apis-image-i.md#xmpnamespace) | uri: "`http://purl.org/dc/elements/1.1/`"<br>prefix: "dc"           | Dublin Core元数据命名空间。</br>**ArkTS-Dyn起始版本：** 26.0.0</br>**ArkTS-Sta起始版本：** 26.0.0 |
| TIFF        | [XMPNamespace](arkts-apis-image-i.md#xmpnamespace) | uri: "`http://ns.adobe.com/tiff/1.0/`"<br>prefix: "tiff"            | TIFF图像格式参数命名空间。</br>**ArkTS-Dyn起始版本：** 26.0.0</br>**ArkTS-Sta起始版本：** 26.0.0 |

## 示例

```ts
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

### XMAGE水印模式

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function SetXmageWatermarkMode(imageSourceObj : image.ImageSource) {
  let makerNoteHuaweiMetadata = image.MakerNoteHuaweiMetadata.createInstance();
  // 设置XMAGE水印模式为底部中央。
  makerNoteHuaweiMetadata.xmageWatermarkMode = image.XMAGE_WATERMARK_MODE_AT_THE_BOTTOM;
  console.info(`Succeeded in setting the XMAGE watermark mode. Mode: ${makerNoteHuaweiMetadata.xmageWatermarkMode}.`);
  await imageSourceObj.writeImageMetadata({ makerNoteHuaweiMetadata: makerNoteHuaweiMetadata }).then(() => {
    console.info(`Succeeded in writing image metadata.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to write image metadata. Code: ${error.code}, message: ${error.message}.`);
  });
}
```

### 拍摄模式

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function SetCaptureMode(imageSourceObj : image.ImageSource) {
  let makerNoteHuaweiMetadata = image.MakerNoteHuaweiMetadata.createInstance();
  // 设置拍摄模式为专业模式。
  makerNoteHuaweiMetadata.captureMode = image.CAPTURE_MODE_PROFESSIONAL;
  console.info(`Succeeded in setting the capture mode. Mode: ${makerNoteHuaweiMetadata.captureMode}.`);
  await imageSourceObj.writeImageMetadata({ makerNoteHuaweiMetadata: makerNoteHuaweiMetadata }).then(() => {
    console.info(`Succeeded in writing image metadata.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to write image metadata. Code: ${error.code}, message: ${error.message}.`);
  });
}
```

### XMP Namespaces

可以参考XMPMetadata中的[setValue](arkts-apis-image-XMPMetadata.md#setvalue)和[getTag](arkts-apis-image-XMPMetadata.md#gettag)等方法的示例来使用这些命名空间。