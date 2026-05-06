# Interfaces (Others)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## PositionArea<sup>7+</sup>

Describes area information in an image.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name  | Type              | Read Only|  Optional| Description                                                        |
| ------ | ------------------ | ---| -----|------------------------------------------------------- |
| pixels | ArrayBuffer        | No|   No | Pixels of the image. Only pixel data in BGRA_8888 format is supported.|
| offset | number             | No|   No |  Offset for data reading, in bytes.                                                    |
| stride | number             | No|   No | Number of bytes from one row of pixels in memory to the next row of pixels in memory. in bytes. The value of **stride** must be greater than or equal to the value of **region.size.width** multiplied by 4.                  |
| region | [Region](#region8) | No|   No |Region to read or write. The width of the region to write plus the X coordinate cannot be greater than the width of the original image. The height of the region to write plus the Y coordinate cannot be greater than the height of the original image.|

## ImageInfo

Describes image information.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name| Type         | Read Only| Optional| Description      |
| ---- | ------------- | --- |-----|---------- |
| size<sup>6+</sup> | [Size](#size) | No|  No |Image size.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.|
| density<sup>9+</sup> | number | No | No|Pixel density, in ppi.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.|
| stride<sup>11+</sup> | number | No | No | Number of bytes from one row of pixels in memory to the next row of pixels in memory. in bytes.stride >= region.size.width*4 <br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.|
| pixelFormat<sup>12+</sup> | [PixelMapFormat](arkts-apis-image-e.md#pixelmapformat7) | No |  No| Pixel format.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.|
| alphaType<sup>12+</sup> | [AlphaType](arkts-apis-image-e.md#alphatype9)  | No |  No |Alpha type.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.|
| mimeType<sup>12+</sup> | string  |  No |   No |Actual image format (MIME type).<br>The supported formats for image decoding and image encoding are different. Do not directly use the actual image format obtained after decoding as the value of **format** in [PackingOption](#packingoption) during image encoding.<br>You can use the **supportedFormats** property of [ImageSource](../../reference/apis-image-kit/arkts-apis-image-ImageSource.md#properties) and of [ImagePacker](../../reference/apis-image-kit/arkts-apis-image-ImagePacker.md#properties) to view the supported formats for decoding and encoding. |
| isHdr<sup>12+</sup> | boolean  |  No | No | Whether the image is an HDR image. The value **true** means an HDR image, and **false** means an SDR image. For [ImageSource](arkts-apis-image-ImageSource.md), this parameter specifies whether the source image is in HDR format. For [PixelMap](arkts-apis-image-PixelMap.md), this parameter specifies whether the decoded PixelMap is in HDR format.|

## Size

Describes the size of an image.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name  | Type  | Read Only|  Optional |Description          |
| ------ | ------ | -- |-----| -------------- |
| height | number | No |  No |Image height, in px.|
| width  | number | No |  No| Image width, in px.|

## HdrComposeOptions<sup>23+</sup>

Options for HDR image composition.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name        | Type  | Read Only| Optional| Description        |
| ------------ | ------ | ---- | ---- | ------------ |
| desiredPixelFormat | [PixelMapFormat](arkts-apis-image-e.md#pixelmapformat7)  | No  | Yes  | Pixel format for image composition. The RGBA_1010102, YCBCR_P010, and YCRCB_P010 formats are supported.|

## AuxiliaryPictureInfo<sup>13+</sup>

Describes the auxiliary picture information.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name                     | Type                                                        | Read Only| Optional| Description                                                        |
| ------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| auxiliaryPictureType      | [AuxiliaryPictureType](arkts-apis-image-e.md#auxiliarypicturetype13)              | No  | No  | Auxiliary picture type.                                          |
| size         | [Size](#size)                                                | No  | No  | Image size.|
| rowStride                 | number                                                       | No  | No  | Row stride. The unit is bytes.                                                      |
| pixelFormat | [PixelMapFormat](arkts-apis-image-e.md#pixelmapformat7)                           | No  | No  | Pixel format.|
| colorSpace                | [colorSpaceManager.ColorSpaceManager](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspacemanager) | No  | No  | Color space.                                              |

## SourceOptions<sup>9+</sup>

Defines image source initialization options.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name             | Type                              | Read Only| Optional| Description              |
| ----------------- | ---------------------------------- | ---- | ---- | ------------------ |
| sourceDensity     | number                             | No  | No  | Pixel density of the image resource, in ppi.<br>If **desiredSize** is not set in [DecodingOptions](#decodingoptions7) and **SourceOptions.sourceDensity** and **DecodingOptions.fitDensity** are not 0, the PixelMap output after decoding will be scaled.<br>The formula for calculating the width after scaling is as follows (the same applies to the height): (width * fitDensity + (sourceDensity >> 1)) / sourceDensity.|
| sourcePixelFormat | [PixelMapFormat](arkts-apis-image-e.md#pixelmapformat7) | No  | Yes  | Image pixel format. The default value is **UNKNOWN**.    |
| sourceSize        | [Size](#size)                      | No  | Yes  | Image pixel size. The default value is null.    |

## InitializationOptions<sup>8+</sup>

Defines PixelMap initialization options.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name                    | Type                              | Read Only|Optional|  Description          |
| ------------------------ | ---------------------------------- | ----| -----|  -------------- |
| alphaType<sup>9+</sup>   | [AlphaType](arkts-apis-image-e.md#alphatype9)           | No  | Yes| Alpha type. The default value is **IMAGE_ALPHA_TYPE_PREMUL**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.     |
| editable                 | boolean                            | No  | Yes| Whether the image pixels are editable. **true** if editable, **false** otherwise. The value **false** provides better image rendering and transmission performance. The default value is **false**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.|
| srcPixelFormat<sup>12+</sup>  | [PixelMapFormat](arkts-apis-image-e.md#pixelmapformat7) | No| Yes| Pixel format of the passed-in buffer data. The default value is **BGRA_8888**.|
| pixelFormat              | [PixelMapFormat](arkts-apis-image-e.md#pixelmapformat7) | No| Yes| Pixel format of the generated PixelMap. The default value is **RGBA_8888**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.    |
| scaleMode<sup>9+</sup>   | [ScaleMode](arkts-apis-image-e.md#scalemode9)           | No | Yes| Scale mode. The default value is **0**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.      |
| size                     | [Size](#size)                      | No | No|Image size.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.|

## DecodingOptions<sup>7+</sup>

Describes the image decoding options.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

| Name              | Type                              | Read Only| Optional| Description            |
| ------------------ | ---------------------------------- | ---- | ---- | ---------------- |
| sampleSize         | number                             | No  | Yes  | Sampling size of the thumbnail. The default value is **1**. Currently, the value can only be **1**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.|
| rotate             | number                             | No  | Yes  | Rotation angle. The unit is degrees. The default value is **0**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.      |
| editable           | boolean                            | No  | Yes  | Whether pixels are editable. **true** if editable, **false** otherwise. The default value is **false**.<br>If this parameter is set to **false**, the image rendering and transmission performance is improved, but the image cannot be edited. For example, the writePixels operation will fail.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12. |
| desiredSize        | [Size](#size)                      | No  | Yes  | Expected output size. The value must be a positive integer and defaults to the original image size. If the output size is different from the original size, the output is stretched or scaled to the specified size.<br>Note: If both **desiredSize** and **desiredRegion** are passed to the decoding API, you must also include **cropAndScaleStrategy** to determine whether to crop or scale first. **CROP_FIRST** is recommended.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.  |
| desiredRegion      | [Region](#region8)                 | No  | Yes  | Rectangle specified by **Region** in the decoded image. When the original image is large and only a specific part of the image is required, you can set this parameter to improve performance. The default value is the original image size.<br>Note: If both **desiredSize** and **desiredRegion** are passed to the decoding API, you must also include **cropAndScaleStrategy** to determine whether to crop or scale first. **CROP_FIRST** is recommended.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.      |
| desiredPixelFormat | [PixelMapFormat](arkts-apis-image-e.md#pixelmapformat7) | No  | Yes  | Pixel format for decoding. The default value is **RGBA_8888**. Only RGBA_8888, BGRA_8888, and RGB_565 are supported. RGB_565 is not supported for images with alpha channels, such as PNG, GIF, ICO, and WEBP.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.|
| index              | number                             | No  | Yes  | Index of the image to decode. The default value is **0**, indicating the first image. If this parameter is set to N, the (N+1)th image is used. For single-frame images, the value is always **0**. For multi-frame images such as animations, the value ranges from 0 to (Number of frames – 1).<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.  |
| fitDensity<sup>9+</sup> | number                        | No  | Yes  | Pixel density, in ppi. The default value is **0**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.<br>**Widget capability**: This API can be used in ArkTS widgets since API version 12.  |
| desiredColorSpace<sup>11+</sup> | [colorSpaceManager.ColorSpaceManager](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspacemanager) | No  | Yes  | Target color space. The default value is **UNKNOWN**.|
| desiredDynamicRange<sup>12+</sup> | [DecodingDynamicRange](arkts-apis-image-e.md#decodingdynamicrange12) | No  | Yes  | Desired dynamic range. The default value is **SDR**.<br>This property cannot be set for an image source created using [CreateIncrementalSource](arkts-apis-image-f.md#imagecreateincrementalsource9). By default, the image source is decoded as SDR content.<br>If the platform does not support HDR, the setting is invalid and the content is decoded as SDR content by default.|
| cropAndScaleStrategy<sup>18+</sup> | [CropAndScaleStrategy](arkts-apis-image-e.md#cropandscalestrategy18) | No  | Yes  | If **desiredRegion** and **desiredSize** are both specified, the order of cropping and scaling is determined.<br>Only **SCALE_FIRST** and **CROP_FIRST** are supported.|

## DecodingOptionsForPicture<sup>13+</sup>

Describes the image decoding options.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

| Name                    | Type                                                   | Read Only| Optional| Description                                                        |
| ------------------------ | ------------------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| desiredAuxiliaryPictures | Array\<[AuxiliaryPictureType](arkts-apis-image-e.md#auxiliarypicturetype13)> | No  | No  | Auxiliary picture type. If no auxiliary picture type is specified or an empty array is passed, the system decodes all available auxiliary picture types.<br>To exclude all auxiliary picture, you can decode the auxiliary picture to a PixelMap and use the PixelMap to create a Picture that contains only the main picture.|
| desiredSizeForMainPixelMap<sup>24+</sup> | [Size](#size) | No  | Yes  | Expected size of the main picture. The value must be a positive integer. The default value is the original size of the main picture, in pixels.<br>If the original size of the main picture is different from the specified size, the main picture is stretched or scaled to the specified size.<br>The width and height of the auxiliary picture are scaled in the same proportion as those of the main picture.<br>**Model restriction**: This API can be used only in the stage model.|
| desiredPixelFormat<sup>24+</sup> | [PixelMapFormat](arkts-apis-image-e.md#pixelmapformat7) | No  | Yes  | Pixel format for decoding. The default value is **RGBA_8888**.<br>Only RGBA_8888, BGRA_8888, RGB_565, NV12, and NV21 are supported.<br>If an unsupported pixel format is set, a decoding failure is returned.<br>**Model restriction**: This API can be used only in the stage model.|

## DecodingOptionsForThumbnail

Thumbnail decoding options.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

| Name                     | Type   | Read Only| Optional| Description                                                        |
| ------------------------- | ------- | ---- | ---- | ------------------------------------------------------------ |
| generateThumbnailIfAbsent | boolean | No  | Yes  | Whether to generate a thumbnail when the image does not have one. The value **true** indicates yes, and the value **false** indicates no. The default value is **true**.<br>If the image file does not contain a thumbnail and **generateThumbnailIfAbsent** is set to **false**, **undefined** is returned (error code [**7700303**](errorcode-image.md#7700303-image-does-not-contain-thumbnail-data) is reported).|
| maxGeneratedPixelDimension | number  | No  | Yes  | Maximum side length (the larger of the width and height) for generating thumbnails. The shorter side is scaled proportionally to the longer side. This parameter is valid only when **generateThumbnailIfAbsent** is set to **true**.<br>The value must be an integer. The default value is **512**. Both the width and height of the generated thumbnail are limited to **maxGeneratedPixelDimension**.<br>If the calculated thumbnail width or height is less than 1 pixel (rounded down to 0), no thumbnail will be generated.<br>The unit is px.|

## Region<sup>8+</sup>

Describes the region information.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name| Type         | Read Only| Optional| Description        |
| ---- | ------------- | ---- | ---- | ------------ |
| size<sup>7+</sup> | [Size](#size) | No  | No  | Region size.  |
| x<sup>7+</sup>    | number        | No  | No | X coordinate of the top-left corner of the region, in px.|
| y<sup>7+</sup>    | number        | No | No | Y coordinate of the top-left corner of the region, in px.|

## PackingOption

Describes the options for image encoding.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

| Name   | Type  | Read Only| Optional| Description                                               |
| ------- | ------ | ---- | ---- | --------------------------------------------------- |
| format  | string | No  | No  | Format of the packed image.<br>- When [the input is ImageSource or PixelMap](../../media/image/image-encoding.md), the following formats are supported: image/jpeg, image/webp, image/png, image/heic (or image/heif)<sup>12+</sup>, image/sdr_astc_4x4<sup>18+</sup>, image/sdr_sut_superfast_4x4<sup>18+</sup> (depending on the hardware), and image/hdr_astc_4x4<sup>20+</sup>.<br>- When [the input is Picture](../../media/image/image-picture-encoding.md), only image/jpeg and image/heic (or image/heif)<sup>12+</sup> are supported.<br>- GIF image encoding requires input of multiple **PixelMap** objects, with the format specified as image/gif. The encoding can be performed using [packToDataFromPixelmapSequence](./arkts-apis-image-ImagePacker.md#packtodatafrompixelmapsequence18) or [packToFileFromPixelmapSequence](./arkts-apis-image-ImagePacker.md#packtofilefrompixelmapsequence18).<br>**NOTE**: The JPEG format does not support the alpha channel. If the JPEG format with the alpha channel is used for data encoding, the transparent color turns black.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| quality | number | No  | No  | 1. Quality of the output image set. This parameter takes effect only for JPEG and HEIF images. The value range is [0, 100]. The value **0** means the lowest quality, and **100** means the highest quality. The higher the quality, the larger the space occupied by the generated image. WebP and PNG images are lossless.<br> 2. In the case of sdr_astc_4x4 encoding, the parameter can be set to **92** and **85**.<br>3. In the case of sut encoding, the parameter can be set to **92**.<br>4. (Available since API version 20) In the case of hdr_astc_4x4 encoding, the parameter can be set to **85**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| bufferSize<sup>9+</sup> | number | No  | Yes  | Size of the buffer for receiving the encoded data, in bytes. If this parameter is not set, the default value 25 MB is used. If the size of an image exceeds 25 MB, you must specify the size. The value of **bufferSize** must be greater than the size of the encoded image. The use of [packToFile](arkts-apis-image-ImagePacker.md#packtofile11) is not restricted by this parameter.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| desiredDynamicRange<sup>12+</sup> | [PackingDynamicRange](arkts-apis-image-e.md#packingdynamicrange12) | No  | Yes  | Desired dynamic range. The default value is **SDR**.|
| needsPackProperties<sup>12+</sup> | boolean | No  | Yes  | Whether encoding image property information, for example, Exif, is required. **true** if required, **false** otherwise. The default value is **false**.|
| maxEmbedThumbnailDimension | number | No| Yes| Maximum side length (the larger of the width and height) for generating thumbnails during encoding. The shorter side is scaled proportionally to the longer side. This parameter is valid only when **needsPackProperties** is set to **true**.<br>The value must be an integer. The default value is **0**.<br>If this parameter is not specified or the thumbnail width or height calculated based on the value of this parameter is 0, no thumbnail will be generated during encoding.<br>The unit is px.<br>**Since**: 26.0.0<br>**Model restriction**: This API can be used only in the stage model.|

## PackingOptionsForSequence<sup>18+</sup>

Defines the options for encoding animated images.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

| Name         | Type          | Read Only| Optional| Description                                                        |
| ------------- | -------------- | ---- | ---- | ------------------------------------------------------------ |
| frameCount    | number         | No  | No  | Number of frames specified in GIF encoding.                                       |
| delayTimeList | Array\<number> | No  | No  | Delay time of each frame in GIF encoding. The value must be greater than 0.<br>The unit is 10 milliseconds. For example, if this parameter is set to 10, the actual delay per frame is 100 ms.<br>If the array length is less than **frameCount**, the last value in the array will be used for the remaining frames.|
| disposalTypes | Array\<number> | No  | Yes  | Array that defines how each image frame transitions. If the array length is less than **frameCount**, the last value in the array will be used for the remaining frames. The values can be:<br>- **0**: No operation is required.<br>- **1**: Keeps the image unchanged.<br>- **2**: Restores the background color.<br>- **3**: Restores to the previous state.|
| loopCount     | number         | No  | Yes  | Number of times that the output image in GIF encoding loops. The value range is [0, 65535].<br>The value **0** means an infinite loop. If this field is not carried, loop playback is not performed.|

## ImagePropertyOptions<sup>11+</sup>

Describes the image properties.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

| Name        | Type  | Read Only| Optional| Description        |
| ------------ | ------ | ---- | ---- | ------------ |
| index        | number | No  | Yes  | Index of the image. The default value is **0**.  |
| defaultValue | string | No  | Yes  | Default property value. The default value is null.|

## Component<sup>9+</sup>

Describes the color components of an image.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name         | Type                            | Read Only| Optional| Description        |
| ------------- | -------------------------------- | ---- | ---- | ------------ |
| componentType | [ComponentType](arkts-apis-image-e.md#componenttype9) | Yes  | No  | Color component type.  |
| rowStride     | number                           | Yes  | No  | Row stride. The unit is bytes. The camera preview stream data needs to be read by stride. For details, see [Solution to Screen Artifacts During Camera Preview](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-deal-stride-solution).      |
| pixelStride   | number                           | Yes  | No  | Pixel stride. The unit is bytes.  |
| byteBuffer    | ArrayBuffer                      | Yes  | No  | Component buffer.|

## HdrStaticMetadata<sup>12+</sup>

Describes the static metadata keys, that is, the values available for **HDR_STATIC_METADATA** in [HdrMetadataKey](arkts-apis-image-e.md#hdrmetadatakey12).

**System capability**: SystemCapability.Multimedia.Image.Core

| Name         | Type      | Read Only| Optional| Description        |
| ------------- | ----------| -- | -- | ------------ |
| displayPrimariesX     | Array\<number>  | No| No| X coordinate of the three primary colors of the display device after normalization. The array length is 3. The unit is 0.00002. The value range is [0.0, 1.0]. |
| displayPrimariesY     | Array\<number>  | No| No| Y coordinate of the three primary colors of the display device after normalization. The array length is 3. The unit is 0.00002. The value range is [0.0, 1.0]. |
| whitePointX  | number  | No| No| X coordinate of the white point after normalization. The unit is 0.00002. The value range is [0.0, 1.0].  |
| whitePointY  | number   | No| No| Y coordinate of the white point after normalization. The unit is 0.00002. The value range is [0.0, 1.0].  |
| maxLuminance  | number  | No| No| Maximum luminance of the main monitor. The unit is nits. The maximum value is **65535**.  |
| minLuminance  | number   | No| No| Minimum luminance of the main monitor. The unit is nits. Actual value = Stored value × 0.0001. The maximum value is **6.5535**.  |
| maxContentLightLevel  | number  | No| No| Maximum luminance of the displayed content. The unit is nits. The maximum value is **65535**.  |
| maxFrameAverageLightLevel  | number  | No| No| Maximum average luminance of the displayed content. The unit is nits. The maximum value is **65535**.|

## GainmapChannel<sup>12+</sup>

Describes the data content of a single channel of the gain map. For details, see ISO 21496-1.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name         | Type      | Read Only| Optional| Description        |
| ------------- | ----------| -- | -- | ------------ |
| gainmapMax     | number   | No| No| Maximum value of the gain map. For details, see ISO 21496-1. |
| gainmapMin     | number   | No| No| Minimum value of the gain map. For details, see ISO 21496-1. |
| gamma  | number    | No| No| Gamma. For details, see ISO 21496-1.  |
| baseOffset  | number     | No| No| Offset of the base graphic. For details, see ISO 21496-1.  |
| alternateOffset  | number    | No| No| Offset of the alternative graphic that can be extracted. For details, see ISO 21496-1.   |

## ImageMetadata<sup>23+</sup>

Describes the image metadata set.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name                   | Type                   | Read Only| Optional| Description                           |
| ----------------------- | ----------------------- | ---- | ---- | ------------------------------- |
| exifMetadata            | [ExifMetadata](arkts-apis-image-ExifMetadata.md) | No  | Yes  | Exif metadata.                   |
| makerNoteHuaweiMetadata | [MakerNoteHuaweiMetadata](arkts-apis-image-MakerNoteHuaweiMetadata.md) | No  | Yes  | Photo metadata from Huawei cameras.|
| heifsMetadata | [HeifsMetadata](arkts-apis-image-HeifsMetadata.md) | No  | Yes  | HEIF image sequence metadata.|
| webPMetadata<sup>24+</sup> | [WebPMetadata](arkts-apis-image-WebPMetadata.md) | No  | Yes  | WebP image metadata class, which is used to store image metadata.|
| dngMetadata<sup>24+</sup> | [DngMetadata](#dngmetadata24) | No  | Yes  | DNG image metadata.|

## DngMetadata<sup>24+</sup>

DNG image metadata class, which is used to store image metadata.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name                        | Type| Read Only| Optional| Description                                      |
| ---------------------------- | ------ | ---- | ---- | ------------------------------------------ |
| dngVersion | number[] | Yes  | Yes| Version number of the DNG image.|
| dngBackwardVersion | number[] | Yes| Yes  | Minimum backward-compatible version number of the DNG file.|
| uniqueCameraModel | string | Yes| Yes| Unique model ID of the camera, which is used to distinguish different devices.|
| localizedCameraModel | string | Yes| Yes| Localized camera model name.|
| cfaPlaneColor | number[] | Yes| Yes| Color channel definition for each Color Filter Array (CFA) plane.|
| cfaLayout | number | Yes| Yes| CFA layout type.|
| linearizationTable | number[] | Yes| Yes| Linearization lookup table, which is used to map raw sensor values to the linear light intensity.|
| blackLevelRepeatDim | number[] | Yes| Yes| Black level repetition dimension.|
| blackLevel | number[] | Yes| Yes| Encoding level in zero illumination.|
| blackLevelDeltaH | number[] | Yes| Yes| Horizontal black level correction increment.|
| blackLevelDeltaV | number[] | Yes| Yes| Vertical black level correction increment.|
| whiteLevel | number[] | Yes| Yes| White level, indicating the maximum valid output of the sensor.|
| defaultScale | number[] | Yes| Yes| Default scaling ratio. The format is [*Horizontal scaling ratio*, *Vertical scaling ratio*].|
| defaultCropOrigin | number[] | Yes| Yes| Coordinates (x, y) of the upper left corner of the default crop area.|
| defaultCropSize | number[] | Yes| Yes| Width and height of the default crop area.|
| colorMatrix1 | number[] | Yes| Yes| Color transformation matrix under the first calibration illuminant.|
| colorMatrix2 | number[] | Yes| Yes| Color transformation matrix under the second calibration illuminant.|
| cameraCalibration1 | number[] | Yes| Yes| Camera transformation matrix under the first calibration illuminant.|
| cameraCalibration2 | number[] | Yes| Yes| Camera transformation matrix under the second calibration illuminant.|
| reductionMatrix1 | number[] | Yes| Yes| Dimension reduction matrix under the first calibration illuminant.|
| reductionMatrix2 | number[] | Yes| Yes| Dimension reduction matrix under the second calibration illuminant.|
| analogBalance | number[] | Yes| Yes| Analog gain balance coefficient.|
| asShotNeutral | number[] | Yes| Yes| Neutral white point at capture.|
| asShotWhiteXY | number[] | Yes| Yes| CIE (1931 color space) x-y chromaticity coordinates of the white point at capture.|
| baselineExposure | number | Yes| Yes| Baseline exposure compensation value, in EV.|
| baselineNoise | number | Yes| Yes| Baseline noise level.|
| baselineSharpness | number | Yes| Yes| Baseline sharpness gain.|
| bayerGreenSplit | number | Yes| Yes| Separation degree of the two green channels in a Bayer image.|
| linearResponseLimit | number | Yes| Yes| Linear response upper limit.|
| cameraSerialNumber | string | Yes| Yes| Camera serial number.|
| lensInfo | number[] | Yes| Yes| Lens information.|
| chromaBlurRadius | number | Yes| Yes| Chrominance blur radius, in pixels.|
| antiAliasStrength | number | Yes| Yes| Anti-aliasing filter strength.|
| shadowScale | number | Yes| Yes| Shadow region scaling factor.|
| dngPrivateData | ArrayBuffer | Yes| Yes| Vendor-specific data block.|
| makerNoteSafety | number | Yes| Yes| Whether the EXIF MakerNote is secure and can be retained. The value **1** indicates yes, and the value **0** indicates no.|
| calibrationIlluminant1 | number | Yes| Yes| Type of the first calibration illuminant.|
| calibrationIlluminant2 | number | Yes| Yes| Type of the second calibration illuminant.|
| bestQualityScale | number | Yes| Yes| Scaling ratio for the optimal image quality.|
| rawDataUniqueID | string | Yes| Yes| Unique ID of the raw image data.|
| originalRawFileName | string | Yes| Yes| Original raw file name.|
| originalRawFileData | ArrayBuffer | Yes| Yes| Complete data of the original raw file.|
| activeArea | number[] | Yes| Yes| Valid image area.|
| maskedAreas | number[] | Yes| Yes| List of masked areas.|
| asShotICCProfile | ArrayBuffer | Yes| Yes| ICC color profile used at capture.|
| asShotPreProfileMatrix | number[] | Yes| Yes| Pre-transformation matrix before the ICC color profile is applied.|
| currentICCProfile | ArrayBuffer | Yes| Yes| ICC color profile in use.|
| currentPreProfileMatrix | number[] | Yes| Yes| Pre-transformation matrix used before the current ICC color profile.|
| colorimetricReference | number | Yes| Yes| Chromaticity reference standard.|
| cameraCalibrationSignature | string | Yes| Yes| Camera calibration signature.|
| profileCalibrationSignature | string | Yes| Yes| Profile calibration signature.|
| extraCameraProfiles | number[] | Yes| Yes| List of additional camera profile indexes.|
| asShotProfileName | string | Yes| Yes| Name of the profile used at capture.|
| noiseReductionApplied | number | Yes| Yes| Applied noise reduction intensity level.|
| profileName | string | Yes| Yes| Color profile name.|
| profileHueSatMapDims | number[] | Yes| Yes| Dimensions of the hue/saturation mapping table.|
| profileHueSatMapData1 | number[] | Yes| Yes| First set of hue/saturation mapping table data.|
| profileHueSatMapData2 | number[] | Yes| Yes| Second set of hue/saturation mapping table data.|
| profileToneCurve | number[] | Yes| Yes| Tone curve of the profile.|
| profileEmbedPolicy | number | Yes| Yes| Profile embedding policy.|
| profileCopyright | string | Yes| Yes| Profile copyright information.|
| forwardMatrix1 | number[] | Yes| Yes| First forward transformation matrix.|
| forwardMatrix2 | number[] | Yes| Yes| Second forward transformation matrix.|
| previewApplicationName | string | Yes| Yes| Name of the application that generates the preview image.|
| previewApplicationVersion | string | Yes| Yes| Version of the application that generates the preview image.|
| previewSettingsName | string | Yes| Yes| Name of the preview image processing configuration.|
| previewSettingsDigest | string | Yes| Yes| MD5 digest of the preview image configuration.|
| previewColorSpace | number | Yes| Yes| Color space of the preview image.|
| previewDateTime | string | Yes| Yes| Preview image generation time.|
| rawImageDigest | string | Yes| Yes| MD5 digest of the raw image data.|
| originalRawFileDigest | string | Yes| Yes| MD5 digest of the original raw file data.|
| subTileBlockSize | number[] | Yes| Yes| Block length and width for image titled storage.|
| rowInterleaveFactor | number | Yes| Yes| Row interleaving factor.|
| profileLookTableDims | number[] | Yes| Yes| **ProfileLookTableData** dimensions.|
| profileLookTableData | number[] | Yes| Yes| Color table data.|
| opcodeList1 | ArrayBuffer | Yes| Yes| First operation code list.|
| opcodeList2 | ArrayBuffer | Yes| Yes| Second operation code list.|
| opcodeList3 | ArrayBuffer | Yes| Yes| Third operation code list.|
| noiseProfile | number[] | Yes| Yes| Noise profile parameters.|
| originalDefaultFinalSize | number[] | Yes| Yes| Original default final output dimensions.|
| originalBestQualityFinalSize | number[] | Yes| Yes| Original output dimensions for optimal image quality.|
| originalDefaultCropSize | number[] | Yes| Yes| Original default crop dimensions.|
| profileHueSatMapEncoding | number | Yes| Yes| Encoding mode of the hue/saturation mapping table.|
| profileLookTableEncoding | number | Yes| Yes| Color table encoding mode.|
| baselineExposureOffset | number | Yes| Yes| Baseline exposure offset, in EV.|
| defaultBlackRender | number | Yes| Yes| Default black field rendering mode.|
| newRawImageDigest | string | Yes| Yes| New MD5 digest of the update raw image data.|
| rawToPreviewGain | number | Yes| Yes| Gain ratio of the main raw image to the preview image.|
| defaultUserCrop | number[] | Yes| Yes| Default user crop area.|

## HdrGainmapMetadata<sup>12+</sup>

Describes the metadata keys used by a gain map, that is, the values available for **HDR_GAINMAP_METADATA** in [HdrMetadataKey](arkts-apis-image-e.md#hdrmetadatakey12). For details, see ISO 21496-1.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name         | Type      | Read Only| Optional| Description        |
| ------------- | ----------| -- | -- | ------------ |
| writerVersion     | number   | No| No| Version used by the metadata editor. |
| miniVersion     | number   | No| No| Minimum version that needs to be understood for metadata parsing. |
| gainmapChannelCount  | number    | No| No| Number of color channels of the gain map. When the value is 3, the metadata values of the RGB channels are different. When the value is 1, the metadata values of the RGB channels are the same. For details, see ISO 21496-1. |
| useBaseColorFlag  | boolean     | No| No| Whether the color space of the base graphic is used. For details, see ISO 21496-1. **true** if used, **false** otherwise.  |
| baseHeadroom  | number    | No| No|  Headroom of the base graphic, which means the additional brightness that can be added to the base graphic. For details, see ISO 21496-1.  |
| alternateHeadroom  | number     | No| No|  Headroom of the alternate graphic. For details, see ISO 21496-1. |
| channels  | Array<[GainmapChannel](#gainmapchannel12)> | No| No| Number of channels. The length is 3. For details, see ISO 21496-1.|

## ImageReceiverOptions<sup>23+</sup>

Defines the initialization options for **ImageReceiver**.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

| Name             | Type                              | Read Only| Optional| Description              |
| ----------------- | ---------------------------------- | ---- | ---- | ------------------ |
| size     | [Size](#size) | No  | Yes  | Image size (including width and height), in pixels. Both the width and height values must be greater than 0.<br>This parameter does not affect the size of the received image. The actual returned size is determined by the producer, for example, the camera.|
| capacity | number | No  | Yes  | Maximum number of images that can be accessed concurrently. The value must be a positive integer less than or equal to 64.<br>This parameter is used only as an expected value. The actual capacity depends on the device hardware.    |

## ImageBufferData<sup>23+</sup>

Saves the pointer to the image buffer data as well as the row stride and pixel stride information of different color components.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name             | Type             | Read Only| Optional| Description              |
| ----------------- | ----------------- | ---- | ---- | ------------------ |
| rowStride   | number[]  | Yes  | No  | Row strides of color components, in bytes.<br>This property is meaningless for encoded images such as JPEG images.<br>The camera preview stream data needs to be read by stride. For details, see [Solution to Screen Artifacts During Camera Preview](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-deal-stride-solution).|
| pixelStride | number[]  | Yes  | No  | Pixel strides of color components, in bytes.<br>This property is meaningless for encoded images such as JPEG images.    |
| byteBuffer  | ArrayBuffer | Yes  | No  | Image buffer.    |

## ImageRawData<sup>24+</sup>

Describes the image raw data.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name             | Type             | Read Only| Optional| Description              |
| ----------------- | ----------------- | ---- | ---- | ------------------ |
| buffer  | ArrayBuffer | No  | No  | Image buffer.    |
| bitsPerPixel | number  | No  | No  | Number of bits occupied by each pixel in the buffer data, in bits.    |

## GetImagePropertyOptions<sup>(deprecated)</sup>

Describes the image properties.

> **NOTE**
>
> This API is supported since API version 7 and is deprecated since API version 11. You are advised to use [ImagePropertyOptions](#imagepropertyoptions11) instead.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

| Name        | Type  | Read Only| Optional| Description        |
| ------------ | ------ | ---- | ---- | ------------ |
| index        | number | No  | Yes  | Index of the image. The default value is **0**.  |
| defaultValue | string | No  | Yes  | Default property value. The default value is null.|
