# InitializationOptions

PixelMap的初始化选项。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Image.Core

## alphaType

```TypeScript
alphaType?: AlphaType
```

透明度。默认值为IMAGE_ALPHA_TYPE_PREMUL。

**类型：** AlphaType

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## editable

```TypeScript
editable?: boolean
```

图像像素是否可被编辑。true表示可被编辑，false表示不可被编辑。设为false时，可提升图像的渲染和传输性能，但是图像不可被二次编辑。例如，writePixels操作将失败。默认值为false。

**类型：** boolean

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## pixelFormat

```TypeScript
pixelFormat?: PixelMapFormat
```

生成的PixelMap的像素格式。默认值为RGBA_8888。

**类型：** PixelMapFormat

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## scaleMode

```TypeScript
scaleMode?: ScaleMode
```

缩放模式。默认值为FIT_TARGET_SIZE。

**类型：** ScaleMode

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## size

```TypeScript
size: Size
```

创建的图片尺寸，宽高值必须为正整数。

**类型：** Size

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## srcPixelFormat

```TypeScript
srcPixelFormat?: PixelMapFormat
```

传入的缓冲区数据的像素格式。默认值为BGRA_8888。

**类型：** PixelMapFormat

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

