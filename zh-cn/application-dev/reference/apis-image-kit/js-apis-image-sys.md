# @ohos.multimedia.image (图片处理)(系统接口)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

本模块提供图片处理效果，包括通过属性创建PixelMap、读取图像像素数据、读取区域内的图片数据等。

> **说明：**
>
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.multimedia.image (图片处理)](arkts-apis-image.md)。

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```

## DecodingOptions<sup>7+</sup>

图像解码设置选项。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

| 名称               | 类型              | 只读 | 可选 | 说明             |
| ----------------- | ----------------- | ---- | ---- | ---------------- |
| resolutionQuality<sup>12+</sup> | [ResolutionQuality](#resolutionquality12) | 否   | 是   | 画质效果等级。 |

## ResolutionQuality<sup>12+</sup>

枚举，画质效果等级类型。

**系统能力：** SystemCapability.Multimedia.Image.Core

| 名称                         | 值      | 说明       |
| ---------------------------- | ------ | ---------- |
| LOW     | 1     | 低画质效果，解码耗时短。<br/>此接口为系统接口。|
| MEDIUM             | 2    | 中等画质效果，解码耗时中等。<br/>此接口为系统接口。|
| HIGH             | 3    | 最高等级画质效果，解码耗时长。<br/>此接口为系统接口。|

## image.createPictureByHdrAndSdrPixelMap<sup>20+</sup>

createPictureByHdrAndSdrPixelMap(hdrPixelMap: PixelMap, sdrPixelMap: PixelMap): Promise\<Picture>

根据HDR PixelMap和SDR PixelMap创建Picture对象。系统将使用HDR和SDR PixelMap生成一个增益图（gainmap），返回的Picture对象将包含SDR PixelMap和生成的gainmap PixelMap，像素格式为RGBA8888。使用Promise异步回调。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名       | 类型                | 必填 | 说明             |
| ------------ | ------------------- | ---- | ---------------- |
| hdrPixelMap | [PixelMap](arkts-apis-image-PixelMap.md) | 是   | HDR PixelMap，位深16bit或10bit，像素格式为FP16/RGBA1010102/YCBCR_P010，色彩空间是BT2020_HLG。 |
| sdrPixelMap | [PixelMap](arkts-apis-image-PixelMap.md) | 是   | SDR PixelMap，位深8bit，像素格式为RGBA8888/NV21，色彩空间是P3。 |

**返回值：**

| 类型               | 说明              |
| ------------------ | ----------------- |
|Promise\<[Picture](arkts-apis-image-Picture.md)> | 返回Picture包含sdr和gainmap，像素格式为RGBA8888。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 7600201      | Unsupported operation. HdrPixelMap's PixelMapFormat is not RGBA_F16\RGBA_1010102\YCBCR_P010, or its color space is not BT2020_HLG. Or sdrPixelMap's PixelMapFormat is not RGBA_8888\NV21\NV12, or its color space is not P3. |

**示例：**

```ts
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePictureTest(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg"); // SDR
  let imageSource: image.ImageSource = image.createImageSource(rawFile);
  let options1: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.SDR,
  }
  let options2: image.DecodingOptions = {
    desiredDynamicRange : image.DecodingDynamicRange.HDR, // 通过AIHDR将SDR解码为HDR。
  }
  let sdrPixelMap = await imageSource.createPixelMap(options1);
  let hdrPixelMap = await imageSource.createPixelMap(options2);

  // 获取计算生成的gainmap并编码。
  let picture: image.Picture = await image.createPictureByHdrAndSdrPixelMap(hdrPixelMap, sdrPixelMap);
  if (picture != null) {
    console.info('Create picture succeeded');
  } else {
    console.error('Create picture failed');
  }
  const imagePackerObj = image.createImagePacker();
  let packOpts : image.PackingOption = { format : "image/jpeg", quality: 98};
  packOpts.desiredDynamicRange = image.PackingDynamicRange.AUTO;
  const path: string = context.filesDir + "/hdr-test.jpg";
  let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  imagePackerObj.packToFile(picture, file.fd, packOpts).then(() => {
  }).catch((error : BusinessError) => {
    console.error('Failed to pack the image. And the error is: ' + error);
  })
}
```

## ImageSource

ImageSource类，用于获取图片相关信息。

在调用ImageSource的方法前，需要先通过[image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource)构建一个ImageSource实例。

ImageSource的所有方法均不支持并发调用。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-apis-image-ImageSource.md#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

### createWideGamutSdrPixelMap<sup>20+</sup>

createWideGamutSdrPixelMap(): Promise\<PixelMap>

使用更广的色域解码SDR图片。使用Promise异步回调。

> **说明：**
>
>- 对SDR图片源，使用图片自带色彩空间解码。
>- 对带有单通道增益图的HDR图片源，解码图片的基础图（SDR图），忽略增益图。
>- 对带有3通道增益图的HDR图片源，使用CM_DISPLAY_BT2020_SRGB色彩空间解码。

**系统接口：** 该接口为系统接口。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型                             | 说明                        |
| -------------------------------- | --------------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)> | Promise对象，返回PixelMap。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 7700101  | Bad source.                                                  |
| 7700102  | Unsupported MIME type.                                       |
| 7700103  | Image too large.                                             |
| 7700301  | Decoding failed.                                             |

**示例：**

<!--code_no_check-->
```ts
import { common } from '@kit.AbilityKit';
import image from '@ohos.multimedia.image';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
let filePath: string = context.filesDir + "/sdr.jpg";
let sdrImageSource = image.createImageSource(filePath);
let pixelmap = imageSource.createWideGamutSdrPixelMap();
if (pixelmap != undefined) {
  console.info('Succeeded in creating sdr pixelMap object.');
} else {
  console.error('Failed to create pixelMap.');
}

let singleChannelGainmapFilePath: string = context.filesDir + "/singleChannelGainmapFilePath.jpg";
let singleChannelGainmapImageSource = image.createImageSource(singleChannelGainmapFilePath);
let singleChannelGainmapPixelmap = singleChannelGainmapImageSource.createWideGamutSdrPixelMap();
if (singleChannelGainmapPixelmap != undefined) {
  console.info('Succeeded in creating sdr pixelMap object by using singleChannelGainmapImageSource.');
} else {
  console.error('Failed to create pixelMap.');
}

let threeChannelGainmapFilePath: string = context.filesDir + "/threeChannelGainmapFilePath.jpg";
let threeChannelGainmapImageSource = image.createImageSource(threeChannelGainmapFilePath);
let threeChannelGainmapPixelmap = threeChannelGainmapImageSource.createWideGamutSdrPixelMap();
if (threeChannelGainmapPixelmap != undefined) {
  console.info('Succeeded in creating a sdr pixelMap using CM_DISPLAY_BT2020_SRGB.');
} else {
  console.error('Failed to create pixelMap.');
}
```

### isJpegProgressive<sup>22+</sup>

isJpegProgressive(): Promise\<boolean>

判断Jpeg图片是否是渐进式图片。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**返回值：**

| 类型               | 说明              |
| ------------------ | ----------------- |
|Promise\<boolean> | Promise对象。返回true表示Jpeg图片是渐进式；返回false表示Jpeg图片不是渐进式。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 7600201      | Bad source.|
| 7600202      | Unsupported MIME type.|

**示例：**
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function IsJpegProgressive(imageSource : image.ImageSource) {
  imageSource.isJpegProgressive()
    .then((isProgressive: boolean) => {
      console.info("isJpegProgressive: " + isProgressive);
    }).catch((error: BusinessError) => {
      console.error(`Failed to obtain the jpeg image isprogressive error.code is ${error.code}, message is ${error.message}`);
    })
}
```