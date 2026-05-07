# @ohos.multimedia.image (图片处理)(系统接口)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
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

创建SDR的PixelMap对象。当图片为带有3通道GainMap的HDR图片时，会将其基础图扩展为BT.2020色域的SDR图。使用Promise异步回调。

> **说明：**
>
>- 对SDR图片源，按图片自带的色彩空间解码，输出SDR图。
>- 对带有单通道GainMap的HDR图片源，解码其基础图（SDR图），忽略GainMap。
>- 对带有3通道GainMap的HDR图片源，解码其基础图（SDR图），并将输出SDR图的色域扩展为[colorspace](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspace).DISPLAY_BT2020_SRGB。

**系统接口：** 此接口为系统接口。

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
```ts
async function CreateWideGamutSdrPixelMap(context: Context) {
  // 此处'sdr.jpg'仅作示例，请开发者自行替换。
  let filePath: string = context.filesDir + "/sdr.jpg";
  let sdrImageSource = image.createImageSource(filePath);
  let pixelmap = sdrImageSource.createWideGamutSdrPixelMap();
  if (pixelmap != undefined) {
    console.info('Succeeded in creating sdr pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }

  // 此处'singleChannelGainmapFilePath.jpg'仅作示例，请开发者自行替换。
  let singleChannelGainmapFilePath: string = context.filesDir + "/singleChannelGainmapFilePath.jpg";
  let singleChannelGainmapImageSource = image.createImageSource(singleChannelGainmapFilePath);
  let singleChannelGainmapPixelmap = singleChannelGainmapImageSource.createWideGamutSdrPixelMap();
  if (singleChannelGainmapPixelmap != undefined) {
    console.info('Succeeded in creating sdr pixelMap object by using singleChannelGainmapImageSource.');
  } else {
    console.error('Failed to create pixelMap.');
  }
  // 此处'threeChannelGainmapFilePath.jpg'仅作示例，请开发者自行替换。
  let threeChannelGainmapFilePath: string = context.filesDir + "/threeChannelGainmapFilePath.jpg";
  let threeChannelGainmapImageSource = image.createImageSource(threeChannelGainmapFilePath);
  let threeChannelGainmapPixelmap = threeChannelGainmapImageSource.createWideGamutSdrPixelMap();
  if (threeChannelGainmapPixelmap != undefined) {
    console.info('Succeeded in creating sdr pixelMap using DISPLAY_BT2020_SRGB.');
  } else {
    console.error('Failed to create pixelMap.');
  }
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

### modifyImageAllProperties<sup>24+</sup>

modifyImageAllProperties(records: Record\<string, string\|null>): Promise\<void>

批量修改图片属性。使用Promise异步回调。

Exif属性中除"JPEGInterchangeFormat"/"JPEGInterchangeFormatLength"/"GIFLoopCount"字段外，其他均支持修改。

> **说明：**
>
> - 调用该接口修改属性会改变属性字节长度，建议通过传入文件描述符来创建[image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource7)实例或通过传入的uri创建[image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource)实例。
> - 支持修改JPEG、PNG、HEIF和WEBP文件类型的图片属性，图片需要包含Exif信息。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名  | 类型   | 必填 | 说明         |
| ------- | ------ | ---- | ------------ |
| records | Record\<string, string \| null>|是| 包含图片属性名和属性值的键值对集合。|

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Non-system applications are not allowed to use system APIs.  |
| 7700102  | Unsupported MIME type.                                       |
| 7700202  | Unsupported metadata. For example, the property key is not supported, or the property value is invalid. |
| 7700304  | Failed to write image properties to the file.                |

**示例：**

```ts
async function ModifyImageAllProperties(imageSource: image.ImageSource) {
  try {
    let record: Record<string, string | null> = {
      "HwMnotePhysicalAperture": "13",
    }
    await imageSource.modifyImageAllProperties(record);
  } catch (err) {
    console.error('[modifyImageAllProperties]', `modify image property failed.err: ${err.code}, errorMessage: ${err.message}`);
  }
}
```
