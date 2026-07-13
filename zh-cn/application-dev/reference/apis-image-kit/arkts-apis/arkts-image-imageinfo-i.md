# ImageInfo

表示图片信息。

**起始版本：** 6

**系统能力：** SystemCapability.Multimedia.Image.Core

## alphaType

```TypeScript
alphaType: AlphaType
```

透明度。

**类型：** AlphaType

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## density

```TypeScript
density: number
```

像素密度。单位：ppi（像素/英寸）。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## isHdr

```TypeScript
isHdr: boolean
```

true表示图片为高动态范围（HDR），false表示图片非高动态范围（SDR）。对于[ImageSource](arkts-image-imagesource-i.md)，代表源图片是否为HDR；对于
[PixelMap](arkts-image-pixelmap-i.md)，代表解码后的PixelMap是否为HDR。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## mimeType

```TypeScript
mimeType: string
```

图片真实格式（MIME type）。

图片解码和图片编码支持格式的范围不同，请避免直接将解码得到的图片真实格式作为图片编码时[PackingOption](arkts-image-packingoption-i.md)的format。

可以使用ImageSource[属性](../../../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#属性)中的supportedFormats和
ImagePacker[属性](../../../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#属性)中的supportedFormats查看解码和编码支持
的格式范围。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## pixelFormat

```TypeScript
pixelFormat: PixelMapFormat
```

像素格式。

**类型：** PixelMapFormat

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## size

```TypeScript
size: Size
```

图片大小。

**类型：** Size

**起始版本：** 6

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## stride

```TypeScript
stride: number
```

跨距，内存中每行像素所占的空间。单位：字节（Byte）。stride >= size.width * 4，不满足时数据读取异常。

**类型：** number

**起始版本：** 11

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

