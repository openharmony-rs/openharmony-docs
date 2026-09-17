# PackingOption

Describes the options for image encoding.

**Since:** 6

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## backgroundColor

```TypeScript
backgroundColor?: number
```

The background color used when the image pixels are in RGBA format but the target encoding format does not support transparency, such as "image/jpeg" or "image/heif". The value must be a 24‑bit RGB integer expressed in hexadecimal notation (e.g., 0xRRGGBB). The alpha channel is ignored. Valid range: 0x000000 – 0xFFFFFF.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## bufferSize

```TypeScript
bufferSize?: number
```

Size of the buffer for receiving the encoded data, in bytes. If this parameter is not set, the default value 25 MB is used. If the size of an image exceeds 25 MB, you must specify the size. The value of **bufferSize** must be greater than the size of the encoded image. The use of [packToFile](arkts-image-image-imagepacker-i.md#packtofile) is not restricted by this parameter.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## desiredDynamicRange

```TypeScript
desiredDynamicRange?: PackingDynamicRange
```

Desired dynamic range. The default value is **SDR**.

**Type:** [PackingDynamicRange](arkts-image-image-packingdynamicrange-e.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## format

```TypeScript
format: string
```

Format of the packed image.

Currently, only the following formats are supported: image/jpeg, image/webp, image/png, image/heic (or image/heif)&lt;sup&gt;12+&lt;/sup&gt;, image/sdr_astc_4x4&lt;sup&gt;18+&lt;/sup&gt;, image/sdr_sut_superfast_4x4&lt;sup&gt;18+&lt;/sup&gt; (depending on the hardware), and image/hdr_astc_4x4&lt;sup&gt;20+&lt;/sup&gt;.

**NOTE:**  The JPEG format does not support the alpha channel. If the JPEG format with the alpha channel is used for data encoding, the transparent color turns black.

**Type:** string

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## maxEmbedThumbnailDimension

```TypeScript
maxEmbedThumbnailDimension?: number
```

This parameter is valid only when needsPackProperties is set to true. It specifies the maximum width and height of the thumbnail generated during encoding. If this parameter is not specified, no thumbnail will be generated during encoding. The value should be an integer. <br>Unit:px.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## needsPackGPS

```TypeScript
needsPackGPS?: boolean
```

Indicates whether to carry GPS information when encoding the EXIF metadata. Default value: true.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## needsPackProperties

```TypeScript
needsPackProperties?: boolean
```

Whether encoding image property information, for example, Exif, is required. **true** if required, **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## quality

```TypeScript
quality: number
```

Quality of the output image set. This parameter takes effect only for JPEG and HEIF images. The value range is [0, 100]. The value **0** means the lowest quality, and **100** means the highest quality. The higher the quality, the larger the space occupied by the generated image. WebP and PNG images are lossless.

In the case of sdr_astc_4x4 encoding, the parameter can be set to **92** and **85**.

In the case of sut encoding, the parameter can be set to **92**.

(Available since API version 20) In the case of hdr_astc_4x4 encoding, the parameter can be set to **85**.

**Type:** number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## sizeLimit

```TypeScript
sizeLimit?: PackingSizeLimit
```

Packing image size limit.

**Type:** [PackingSizeLimit](arkts-image-image-packingsizelimit-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## tiffPackingOptions

```TypeScript
tiffPackingOptions?: PackingOptionsForTiff
```

Options for tiff image packing.

**Type:** [PackingOptionsForTiff](arkts-image-image-packingoptionsfortiff-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker
