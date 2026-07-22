# DecodingOptions

图像解码设置选项。

**起始版本：** 7

<!--Device-image-interface DecodingOptions--><!--Device-image-interface DecodingOptions-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## cropAndScaleStrategy

```TypeScript
cropAndScaleStrategy?: CropAndScaleStrategy
```

解码参数如果同时设置desiredRegion与desiredSize，由此决定裁剪与缩放操作的先后策略。

仅支持设置：SCALE_FIRST、CROP_FIRST。

**类型：** CropAndScaleStrategy

**起始版本：** 18

<!--Device-DecodingOptions-cropAndScaleStrategy?: CropAndScaleStrategy--><!--Device-DecodingOptions-cropAndScaleStrategy?: CropAndScaleStrategy-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## desiredColorSpace

```TypeScript
desiredColorSpace?: colorSpaceManager.ColorSpaceManager
```

目标色彩空间。默认值为UNKNOWN。

**类型：** colorSpaceManager.ColorSpaceManager

**起始版本：** 11

<!--Device-DecodingOptions-desiredColorSpace?: colorSpaceManager.ColorSpaceManager--><!--Device-DecodingOptions-desiredColorSpace?: colorSpaceManager.ColorSpaceManager-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## desiredDynamicRange

```TypeScript
desiredDynamicRange?: DecodingDynamicRange
```

目标动态范围，默认值为SDR。

通过[CreateIncrementalSource](arkts-image-image-createincrementalsource-f.md#createincrementalsource)创建的ImageSource不支持设置此属性，默认解码为SDR内容。

如果平台不支持HDR，设置无效，默认解码为SDR内容。

**类型：** DecodingDynamicRange

**起始版本：** 12

<!--Device-DecodingOptions-desiredDynamicRange?: DecodingDynamicRange--><!--Device-DecodingOptions-desiredDynamicRange?: DecodingDynamicRange-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## desiredPixelFormat

```TypeScript
desiredPixelFormat?: PixelMapFormat
```

解码的像素格式。默认值为RGBA_8888。仅支持设置：RGBA_8888、BGRA_8888和RGB_565。有透明通道图片格式不支持设置RGB_565，如PNG、GIF、ICO和WEBP。

**类型：** PixelMapFormat

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-DecodingOptions-desiredPixelFormat?: PixelMapFormat--><!--Device-DecodingOptions-desiredPixelFormat?: PixelMapFormat-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## desiredRegion

```TypeScript
desiredRegion?: Region
```

解码图像中由Region指定的矩形区域，当原始图像很大而只需要解码图像的一部分时，可以设置该参数，有助于提升性能，默认为原始大小。

注意：若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。

**类型：** Region

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-DecodingOptions-desiredRegion?: Region--><!--Device-DecodingOptions-desiredRegion?: Region-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## desiredSize

```TypeScript
desiredSize?: Size
```

期望输出大小，必须为正整数，若与原尺寸比例不一致，则会进行拉伸/缩放到指定尺寸，默认为原始尺寸。

注意：若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。

**类型：** Size

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-DecodingOptions-desiredSize?: Size--><!--Device-DecodingOptions-desiredSize?: Size-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## editable

```TypeScript
editable?: boolean
```

图像像素是否可被编辑。true表示可被编辑，false表示不可被编辑，默认值为false。

当取值为false时，可提升图像的渲染和传输性能，但是图像不可被二次编辑。例如，writePixels操作将失败。

**类型：** boolean

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-DecodingOptions-editable?: boolean--><!--Device-DecodingOptions-editable?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## fitDensity

```TypeScript
fitDensity?: number
```

图像像素密度。单位：ppi（像素/英寸）。默认值为0。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-DecodingOptions-fitDensity?: int--><!--Device-DecodingOptions-fitDensity?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## index

```TypeScript
index?: number
```

解码图片序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index取值只能为0，动图等多帧图片场景中index的取值范围为：[0, (帧数-1)]。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-DecodingOptions-index?: int--><!--Device-DecodingOptions-index?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## rotate

```TypeScript
rotate?: number
```

旋转角度。单位：角度（deg）。默认值为0。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-DecodingOptions-rotate?: int--><!--Device-DecodingOptions-rotate?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## sampleSize

```TypeScript
sampleSize?: number
```

缩略图采样大小，默认值为1。当前只能取1。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-DecodingOptions-sampleSize?: int--><!--Device-DecodingOptions-sampleSize?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

