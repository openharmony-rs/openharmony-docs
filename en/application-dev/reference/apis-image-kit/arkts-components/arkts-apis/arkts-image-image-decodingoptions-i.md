# DecodingOptions

Describes the image decoding options.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## cropAndScaleStrategy

```TypeScript
cropAndScaleStrategy?: CropAndScaleStrategy
```

If **desiredRegion** and **desiredSize** are both specified, the order of cropping and scaling is determined.

Only **SCALE_FIRST** and **CROP_FIRST** are supported.

**Type:** [CropAndScaleStrategy](arkts-image-image-cropandscalestrategy-e.md)

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## desiredColorSpace

```TypeScript
desiredColorSpace?: colorSpaceManager.ColorSpaceManager
```

Target color space. The default value is **UNKNOWN**.

**Type:** [colorSpaceManager.ColorSpaceManager](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## desiredDynamicRange

```TypeScript
desiredDynamicRange?: DecodingDynamicRange
```

Desired dynamic range. The default value is **SDR**.

This property cannot be set for an image source created using [CreateIncrementalSource](arkts-image-image-createincrementalsource-f.md). By default, the image source is decoded as SDR content.

If the platform does not support HDR, the setting is invalid and the content is decoded as SDR content by default.

**Type:** [DecodingDynamicRange](arkts-image-image-decodingdynamicrange-e.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## desiredPixelFormat

```TypeScript
desiredPixelFormat?: PixelMapFormat
```

Pixel format for decoding. The default value is **RGBA_8888**. Only RGBA_8888, BGRA_8888, and RGB_565 are supported. RGB_565 is not supported for images with alpha channels, such as PNG, GIF, ICO, and WEBP.

**Type:** [PixelMapFormat](arkts-image-image-pixelmapformat-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## desiredRegion

```TypeScript
desiredRegion?: Region
```

Rectangle specified by **Region** in the decoded image. When the original image is large and only a specific part of the image is required, you can set this parameter to improve performance. The default value is the original image size.

Note: If both **desiredSize** and **desiredRegion** are passed to the decoding API, you must also include **cropAndScaleStrategy** to determine whether to crop or scale first. **CROP_FIRST** is recommended.

**Type:** [Region](arkts-image-image-region-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## desiredSize

```TypeScript
desiredSize?: Size
```

Expected output size. The value must be a positive integer and defaults to the original image size. If the output size is different from the original size, the output is stretched or scaled to the specified size.

Note: If both **desiredSize** and **desiredRegion** are passed to the decoding API, you must also include **cropAndScaleStrategy** to determine whether to crop or scale first. **CROP_FIRST** is recommended.

**Type:** Size

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## editable

```TypeScript
editable?: boolean
```

Whether the image is editable. **true** if editable, **false** otherwise. The default value is **false**. If this option is set to **false**, the image cannot be edited again, and operations such as writing pixels will fail.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## fitDensity

```TypeScript
fitDensity?: number
```

Pixel density, in ppi. The default value is **0**.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## index

```TypeScript
index?: number
```

Index of the image to decode. The default value is **0**, indicating the first image. If this parameter is set to N, the (N+1)th image is used. For single-frame images, the value is always **0**. For multi-frame images such as animations, the value ranges from 0 to (Number of frames – 1).

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## rotate

```TypeScript
rotate?: number
```

Rotation angle. The default value is **0**.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## sampleSize

```TypeScript
sampleSize?: number
```

Sampling size of the thumbnail. The default value is **1**. Currently, the value can only be **1**.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource
