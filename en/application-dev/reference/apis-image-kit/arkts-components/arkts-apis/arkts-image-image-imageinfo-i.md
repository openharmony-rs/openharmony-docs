# ImageInfo

Describes image information.

**Since:** 6

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## alphaType

```TypeScript
alphaType: AlphaType
```

Alpha type.

**Type:** [AlphaType](arkts-image-image-alphatype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## density

```TypeScript
density: number
```

Pixel density, in ppi.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## isHdr

```TypeScript
isHdr: boolean
```

Whether the image is an HDR image. The value **true** means an HDR image, and **false** means an SDR image. For [ImageSource](arkts-image-image-imagesource-i.md), this parameter specifies whether the source image is in HDR format. For [PixelMap](arkts-image-image-pixelmap-i.md), this parameter specifies whether the decoded PixelMap is in HDR format.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## mimeType

```TypeScript
mimeType: string
```

Actual image format (MIME type).

The supported formats for image decoding and image encoding are different. Do not directly use the actual image format obtained after decoding as the value of **format** in [PackingOption](arkts-image-image-packingoption-i.md) during image encoding.

You can use the **supportedFormats** property of ImageSource and ImagePacker to view the supported formats for decoding and encoding.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## pixelFormat

```TypeScript
pixelFormat: PixelMapFormat
```

Pixel format.

**Type:** [PixelMapFormat](arkts-image-image-pixelmapformat-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## size

```TypeScript
size: Size
```

Image size.

**Type:** Size

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## stride

```TypeScript
stride: number
```

Number of bytes from one row of pixels in memory to the next row of pixels in memory.stride &gt;= region.size.width* 4

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core
