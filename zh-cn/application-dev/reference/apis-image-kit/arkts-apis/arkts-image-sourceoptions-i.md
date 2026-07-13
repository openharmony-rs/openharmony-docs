# SourceOptions

ImageSource的初始化选项。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## sourceDensity

```TypeScript
sourceDensity: number
```

图片资源像素密度。单位：ppi（像素/英寸）。

在解码参数[DecodingOptions](arkts-image-decodingoptions-i.md)未设置desiredSize的前提下，当前参数SourceOptions.sourceDensity与
DecodingOptions.fitDensity非零时将对解码输出的pixelmap进行缩放。

缩放后宽计算公式如下(高同理)：(width * fitDensity + (sourceDensity >> 1)) / sourceDensity。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## sourcePixelFormat

```TypeScript
sourcePixelFormat?: PixelMapFormat
```

图片像素格式，默认值为UNKNOWN。

**类型：** PixelMapFormat

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## sourceSize

```TypeScript
sourceSize?: Size
```

图像像素大小，默认值为空。

**类型：** Size

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

