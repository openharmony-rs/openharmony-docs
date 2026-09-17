# ImageSource

The **ImageSource** class provides APIs to obtain image information.

Before calling any API in ImageSource, you must use [image.createImageSource](arkts-image-image-createimagesource-f.md) to create an ImageSource instance.

All APIs in ImageSource cannot be called concurrently.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 6

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createWideGamutSdrPixelMap

```TypeScript
createWideGamutSdrPixelMap(): Promise<PixelMap>
```

Decodes to a SDR PixelMap, using a as wide gamut as possible. For a SDR ImageSource, decodes to a SDR PixelMap using its native color space. For a HDR ImageSource with a single-channel gainmap, decodes its base(SDR) image and ingores its gainmap. For a HDR ImageSource with a three-channel gainmap, decodes to a SDR PixelMap using CM_DISPLAY_BT2020_SRGB color space.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Decoded PixelMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-abnormal-image-source) | Bad source. |
| [7700102](../errorcode-image.md#7700102-unsupported-mime-type) | Unsupported MIME type. |
| [7700103](../errorcode-image.md#7700103-image-oversized) | Image too large. |
| [7700301](../errorcode-image.md#7700301-decoding-failure) | Decoding failed. |

**Examples**

```TypeScript
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

## isJpegProgressive

```TypeScript
isJpegProgressive(): Promise<boolean>
```

Checks whether a JPEG image is progressive. This API uses a promise to return the result.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise object. The value **true** indicates that the JPEG image is progressive, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7700101](../errorcode-image.md#7700101-abnormal-image-source) | Bad source. |
| [7700102](../errorcode-image.md#7700102-unsupported-mime-type) | Unsupported MIME type. |

**Examples**

```TypeScript
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

## modifyImageAllProperties

```TypeScript
modifyImageAllProperties(records: Record<string, string|null>): Promise<void>
```

Modify the value of properties in an image with the specified keys.The HwMnote read-only key is supported.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| records | Record&lt;string, string &#124; null&gt; | Yes | Property Records whose values are to be modified, when the value is set to null the tag will be removed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [7700102](../errorcode-image.md#7700102-unsupported-mime-type) | Unsupported MIME type. |
| [7700202](../errorcode-image.md#7700202-unsupported-metadata) | Unsupported metadata. For example, the property key is not supported, or the property value is invalid. |
| [7700304](../errorcode-image.md#7700304-failed-to-write-image-information-to-the-file) | Failed to write image properties to the file. |

**Examples**

```TypeScript
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
