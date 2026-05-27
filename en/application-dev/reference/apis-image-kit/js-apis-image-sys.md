# @ohos.multimedia.image (Image Processing) (System API)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

The module provides APIs for image processing. You can use the APIs to create a PixelMap object with specified properties or read image pixel data (even in an area).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.multimedia.image (Image Processing)](arkts-apis-image.md).

## Modules to Import

```ts
import { image } from '@kit.ImageKit';
```

## DecodingOptions<sup>7+</sup>

Describes the image decoding options.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

| Name              | Type             | Read-Only| Optional| Description            |
| ----------------- | ----------------- | ---- | ---- | ---------------- |
| resolutionQuality<sup>12+</sup> | [ResolutionQuality](#resolutionquality12) | No  | Yes  | Image quality.|

## ResolutionQuality<sup>12+</sup>

Enumerates the image quality levels.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name                        | Value     | Description      |
| ---------------------------- | ------ | ---------- |
| LOW     | 1     | Low image quality, requiring a short decoding time.<br>This is a system API.|
| MEDIUM             | 2    | Medium image quality, requiring a medium decoding time<br>This is a system API.|
| HIGH             | 3    | High image quality, requiring a long decoding time.<br>This is a system API.|

## image.createPictureByHdrAndSdrPixelMap<sup>20+</sup>

createPictureByHdrAndSdrPixelMap(hdrPixelMap: PixelMap, sdrPixelMap: PixelMap): Promise\<Picture>

Creates a Picture object based on an HDR PixelMap and an SDR PixelMap. The system uses the HDR PixelMap and SDR PixelMap to generate a gain map. The returned Picture object contains the SDR PixelMap and the generated gain map, both in RGBA8888 format. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name      | Type               | Mandatory| Description            |
| ------------ | ------------------- | ---- | ---------------- |
| hdrPixelMap | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | HDR PixelMap, with 16-bit or 10-bit depth, in FP16/RGBA1010102/YCBCR_P010 format, and BT2020_HLG color space.|
| sdrPixelMap | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | SDR PixelMap, with 8-bit depth, in RGBA8888/NV21 format, and P3 color space.|

**Returns**

| Type              | Description             |
| ------------------ | ----------------- |
|Promise\<[Picture](arkts-apis-image-Picture.md)> | Picture object that contains the SDR PixelMap and gainmap, both in RGBA8888 format.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 7600201      | Unsupported operation. HdrPixelMap's PixelMapFormat is not RGBA_F16\RGBA_1010102\YCBCR_P010, or its color space is not BT2020_HLG. Or sdrPixelMap's PixelMapFormat is not RGBA_8888\NV21\NV12, or its color space is not P3. |

**Example**

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
    desiredDynamicRange : image.DecodingDynamicRange.HDR, // Decode an SDR PixelMap into an HDR PixelMap using AIHDR.
  }
  let sdrPixelMap = await imageSource.createPixelMap(options1);
  let hdrPixelMap = await imageSource.createPixelMap(options2);

  // Obtain the gain map generated and encode the gain map.
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

Provides APIs to obtain image information.

Before calling any API in ImageSource, you must use [image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource) to create an ImageSource instance.

All APIs in ImageSource cannot be called concurrently.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

### createWideGamutSdrPixelMap<sup>20+</sup>

createWideGamutSdrPixelMap(): Promise\<PixelMap>

Creates an SDR PixelMap object. When the image is an HDR image with a 3-channel gain map, its base image will be extended to an SDR image in the BT.2020 color space. This API uses a promise to return the result.

> **NOTE**
>
>- For an SDR image source, this API uses its native color space for decoding and outputs an SDR image.
>- For an HDR image source with a single-channel gain map, this API decodes its base image (SDR image) and ignores the gain map.
>- For an HDR image source with a three-channel gain map, this API decodes its base image (SDR image) and extends the color gamut of the output SDR image to [ColorSpace](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspace).DISPLAY_BT2020_SRGB.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Returns**

| Type                            | Description                       |
| -------------------------------- | --------------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)> | Promise used to return the PixelMap object.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 7700101  | Bad source.                                                  |
| 7700102  | Unsupported MIME type.                                       |
| 7700103  | Image too large.                                             |
| 7700301  | Decoding failed.                                             |

**Example**
```ts
async function CreateWideGamutSdrPixelMap(context: Context) {
  // 'sdr.jpg' is only an example. Replace it with the actual one.
  let filePath: string = context.filesDir + "/sdr.jpg";
  let sdrImageSource = image.createImageSource(filePath);
  let pixelmap = sdrImageSource.createWideGamutSdrPixelMap();
  if (pixelmap != undefined) {
    console.info('Succeeded in creating sdr pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }

  // 'singleChannelGainmapFilePath.jpg' is only an example. Replace it with the actual one.
  let singleChannelGainmapFilePath: string = context.filesDir + "/singleChannelGainmapFilePath.jpg";
  let singleChannelGainmapImageSource = image.createImageSource(singleChannelGainmapFilePath);
  let singleChannelGainmapPixelmap = singleChannelGainmapImageSource.createWideGamutSdrPixelMap();
  if (singleChannelGainmapPixelmap != undefined) {
    console.info('Succeeded in creating sdr pixelMap object by using singleChannelGainmapImageSource.');
  } else {
    console.error('Failed to create pixelMap.');
  }
  // 'threeChannelGainmapFilePath.jpg' is only an example. Replace it with the actual one.
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

Checks whether a JPEG image is progressive. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Returns**

| Type              | Description             |
| ------------------ | ----------------- |
|Promise\<boolean> | Promise object. The value **true** indicates that the JPEG image is progressive, and the value **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 7600201      | Bad source.|
| 7600202      | Unsupported MIME type.|

**Example**
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

Modifies image properties in batches. This API uses a promise to return the result.

All Exif attributes except **JPEGInterchangeFormat**, **JPEGInterchangeFormatLength**, and **GIFLoopCount** can be modified.

> **NOTE**
>
> - Calling this API to modify properties alters the property byte length. You are advised to create an [image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource7) instance by passing a file descriptor or an [image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource) instance by passing a URI.
> - This API applies only to JPEG, PNG, HEIF, and WEBP images that contain Exif information.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type  | Mandatory| Description        |
| ------- | ------ | ---- | ------------ |
| records | Record\<string, string \| null>|Yes| Key-value pairs of image property names and property values.|

**Returns**

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| Error Code| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Non-system applications are not allowed to use system APIs.  |
| 7700102  | Unsupported MIME type.                                       |
| 7700202  | Unsupported metadata. For example, the property key is not supported, or the property value is invalid. |
| 7700304  | Failed to write image properties to the file.                |

**Example**

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
