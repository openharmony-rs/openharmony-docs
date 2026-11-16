# Interface (ImageSource)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=7a61e77be4a6f0c2a53fec86e36cc9974b9916a8 translatedAt=2026-11-06T01:54:39.026Z pushedAt=2026-11-12T02:33:52.914Z nl=1 -->

The **ImageSource** class is used to obtain image-related information.

Before calling the methods of **ImageSource**, you need to create an **ImageSource** instance through [image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource).

None of the methods of **ImageSource** supports concurrent calls.

Because images occupy a large amount of memory, you should call [release](#release) to release the memory in a timely manner after the **ImageSource** instance is no longer used. When releasing the instance, ensure that all asynchronous methods of the instance have been executed and that the instance will no longer be used.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { image } from '@kit.ImageKit';
```

## Attributes

**System capability**: SystemCapability.Multimedia.Image.ImageSource

| Name             | Type           | Read-Only | Optional | Description                                                         |
| ---------------- | -------------- | ---- | ---- | ------------------------------------------------------------ |
| supportedFormats | Array\<string> | Yes   | No   | Supported image formats.<br>Including PNG, JPEG, BMP, GIF, WebP, DNG, HEIC<sup>12+</sup>, WBMP<sup>23+</sup>, HEIFS<sup>23+</sup>, and TIFF<sup>23+</sup>. Since API version 26.0.0, AVIF and AVIS formats are also supported.<br>The decoding capability of some formats depends on the specific device hardware. You are advised to call [image.getImageSourceSupportedFormats](arkts-apis-image-f.md#imagegetimagesourcesupportedformats20) to dynamically query the decoding capability of the current device before calling. |

## getImageInfo

getImageInfo(index: number, callback: AsyncCallback\<ImageInfo>): void

Obtains the image information of the image with the specified index. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name     | Type                                   | Mandatory | Description                                     |
| -------- | -------------------------------------- | ---- | ---------------------------------------- |
| index    | number                                 | Yes   | Index of the image when the ImageSource is created. The default value is **0**, which indicates the first image. When the value is N, it indicates the (N+1)th image. For a single-frame image, the value of **index** can only be **0**. For a multi-frame image such as an animated image, the value range of **index** is [0, (frame count - 1)].                   |
| callback | AsyncCallback<[ImageInfo](arkts-apis-image-i.md#imageinfo)> | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the image information obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageInfo(0, (error: BusinessError, imageInfo: image.ImageInfo) => {
    if (error) {
      console.error(`Failed to obtain the image information.code is ${error.code}, message is ${error.message}`);
    } else {
      console.info('Succeeded in obtaining the image information.');
    }
  })
}
```

## getImageInfo

getImageInfo(callback: AsyncCallback\<ImageInfo>): void

Obtains image information. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name   | Type                                   | Mandatory | Description                                     |
| -------- | -------------------------------------- | ---- | ---------------------------------------- |
| callback | AsyncCallback<[ImageInfo](arkts-apis-image-i.md#imageinfo)> | Yes   | Callback invoked to return the result. If the operation is successful, **err** is **undefined** and **data** is the image information obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageInfo((err: BusinessError, imageInfo: image.ImageInfo) => {
    if (err) {
      console.error(`Failed to obtain the image information.code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('Succeeded in obtaining the image information.');
    }
  })
}
```

## getImageInfo

getImageInfo(index?: number): Promise\<ImageInfo>

Obtains image information. This API uses a promise to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type   | Mandatory | Description                                  |
| ----- | ------ | ---- | ------------------------------------- |
| index | number | No   | Sequence number of the image when the ImageSource instance is created. The default value is **0**, indicating the first image. When the value is N, it indicates the (N+1)th image. For a single-frame image, the value of index can only be **0**. For a multi-frame image such as an animated image, the value range of index is [0, (frame count - 1)]. |

**Return value**

| Type                             | Description                   |
| -------------------------------- | ---------------------- |
| Promise<[ImageInfo](arkts-apis-image-i.md#imageinfo)> | Promise used to return the image information. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageInfo(0)
    .then((imageInfo: image.ImageInfo) => {
      console.info('Succeeded in obtaining the image information.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to obtain the image information.code is ${error.code}, message is ${error.message}`);
    })
}
```

## getImageInfoSync<sup>12+</sup>

getImageInfoSync(index?: number): ImageInfo

Obtains the image information of the image with the specified index and returns the image information synchronously.

> **NOTE**
>
> This is a synchronous method. It blocks the current thread when called, and therefore is not recommended for use in the main thread, which may cause application lag, frame loss, or delayed response. For details about the scenarios, see [Introduction to Time-Consuming Task Concurrency Scenarios](../../arkts-utils/time-consuming-task-overview.md).

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name  | Type   | Mandatory | Description                                  |
| ----- | ------ | ---- | ------------------------------------- |
| index | number | No   | Index of the image when the ImageSource is created. The default value is 0, indicating the first image. When the value is N, it indicates the (N+1)th image. For a single-frame image, the value can only be 0. For a multi-frame image such as an animated image, the value ranges from 0 to (frame count - 1). |

**Return value**

| Type                             | Description                   |
| -------------------------------- | ---------------------- |
| [ImageInfo](arkts-apis-image-i.md#imageinfo) | Image information obtained synchronously. |

**Example**

```ts
function GetImageInfoSync(context : Context) {
  // Here 'test.jpg' is only an example. Replace it with an actual image; otherwise, the ImageSource creation fails and the subsequent operations cannot be performed normally.
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let imageInfo = imageSource.getImageInfoSync(0);
  if (imageInfo == undefined) {
    console.error('Failed to obtain the image information.');
  } else {
    console.info('Succeeded in obtaining the image information.');
    console.info('imageInfo.size.height:' + imageInfo.size.height);
    console.info('imageInfo.size.width:' + imageInfo.size.width);
  }
}
```

## getImageProperty<sup>11+</sup>

getImageProperty(key:PropertyKey, options?: ImagePropertyOptions): Promise\<string>

Obtains the value of the specified property key of the image at the given index. This API uses a promise to return the result.

This API supports only JPEG, PNG, HEIF<sup>12+</sup>, WEBP<sup>23+</sup>, and DNG<sup>23+</sup> files (support varies by hardware device), and the files must contain Exif information.

> **NOTE**
>
> An application uses [PhotoAccessHelper](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md) to query images in the media library and obtains image data through the returned PhotoAsset. Before using this API to read GPS-related fields such as GPS_LATITUDE, GPS_LONGITUDE, GPS_ALTITUDE, GPS_TIME_STAMP, and GPS_DATE_STAMP in [PropertyKey](arkts-apis-image-e.md#propertykey7), the application must declare and request the [ohos.permission.MEDIA_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionmedia_location) permission from the user. If all the preceding fields return 0 or are empty, check whether the permission has been granted and whether the original image contains GPS information.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name  | Type                                                 | Mandatory | Description                                 |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------ |
| key     | [PropertyKey](arkts-apis-image-e.md#propertykey7)                                               | Yes   | Name of the image property.                         |
| options | [ImagePropertyOptions](arkts-apis-image-i.md#imagepropertyoptions11) | No   | Image properties, including the image index and the default property value. |

**Return value**

| Type             | Description                                                              |
| ---------------- | ----------------------------------------------------------------- |
| Promise\<string> | Promise object that returns the image property value. If the value fails to be obtained, the default property value is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 401  | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed;              |
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980103 | The image data is not supported.         |
| 62980110 | The image source data is incorrect.      |
| 62980111 | The image source data is incomplete. |
| 62980112 | The image format does not match.       |
| 62980113| Unknown image format.The image data provided is not in a recognized or supported format, or it may be corrupted.            |
| 62980115 | Invalid image parameter.      |
| 62980118 | Failed to create the image plugin.   |
| 62980122 | Failed to decode the image header.   |
| 62980123| The image does not support EXIF decoding. |
| 62980135| The EXIF value is invalid.             |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  let options: image.ImagePropertyOptions = { index: 0, defaultValue: '9999' }
  imageSourceObj.getImageProperty(image.PropertyKey.BITS_PER_SAMPLE, options)
    .then((data: string) => {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }).catch((error: BusinessError) => {
    console.error(`Failed to get the value of the specified attribute key of the image, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## getImageProperties<sup>12+</sup>

getImageProperties(key: Array&#60;PropertyKey&#62;): Promise<Record<PropertyKey, string|null>>

Obtains the values of the specified property keys in an image in batches. This API uses a promise to return the result asynchronously.

This API supports only JPEG, PNG, HEIF, WEBP<sup>23+</sup>, and DNG<sup>23+</sup> files (support varies with hardware devices), and the files must contain Exif information.

> **NOTE**
>
> The application uses [PhotoAccessHelper](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md) to query images in the media library and obtains image data through the returned PhotoAsset. Before using this API to read GPS-related fields such as GPS_LATITUDE, GPS_LONGITUDE, GPS_ALTITUDE, GPS_TIME_STAMP, and GPS_DATE_STAMP in [PropertyKey](arkts-apis-image-e.md#propertykey7), declare and request the [ohos.permission.MEDIA_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionmedia_location) permission from the user. If all the preceding fields return 0 or are empty, check whether the permission has been granted and whether the original image contains GPS information.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name  | Type                                                 | Mandatory | Description                                 |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------ |
| key     | Array\<[PropertyKey](arkts-apis-image-e.md#propertykey7)>                                 | Yes   | Array of image property names.                         |

**Return value**

| Type             | Description                                                              |
| ---------------- | ----------------------------------------------------------------- |
| Promise\<Record<[PropertyKey](arkts-apis-image-e.md#propertykey7), string \| null>> | Promise object used to return the image property values. If the values fail to be obtained, null is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 401  | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed;     |
| 62980096| The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980110| The image source data is incorrect.            |
| 62980113| Unknown image format.The image data provided is not in a recognized or supported format, or it may be corrupted.            |
| 62980116| Failed to decode the image.            |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperties(imageSourceObj : image.ImageSource) {
  let key = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  imageSourceObj.getImageProperties(key).then((data) => {
    console.info(JSON.stringify(data));
  }).catch((err: BusinessError | BusinessError[]) => {
    if (Array.isArray(err)) {
      (err as BusinessError[]).forEach(e => {
        console.error(`Failed to get the properties, error.code ${e.code}, error.message ${e.message}`);
      });
    } else {
      console.error(`Failed to get the properties, error.code ${err.code}, error.message ${err.message}`);
    }
  });
}
```

## getImagePropertySync<sup>20+</sup>

getImagePropertySync(key:PropertyKey): string

Obtains the value of the specified property key in the image Exif and returns the result synchronously.

> **NOTE**
>
> - This method supports only JPEG, PNG, HEIF, WEBP<sup>23+</sup>, and DNG<sup>23+</sup> files (support varies with hardware devices), and the files must contain Exif information.
>
> - Exif information is the metadata of an image, including the shooting time, camera model, aperture, focal length, ISO, and so on.
>
> - An application uses [PhotoAccessHelper](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md) to query images in the media library and obtains image data through the returned PhotoAsset. Before using this API to read GPS-related fields such as GPS_LATITUDE, GPS_LONGITUDE, GPS_ALTITUDE, GPS_TIME_STAMP, and GPS_DATE_STAMP in [PropertyKey](arkts-apis-image-e.md#propertykey7), the application must declare and request the [ohos.permission.MEDIA_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionmedia_location) permission from the user. If the preceding fields are all 0 or empty, check whether the permission has been granted and whether the original image contains GPS information.
>
> - This method is synchronous and blocks the current thread when called. It is not recommended to call it in the main thread, which may cause the application to lag, drop frames, or respond slowly. For details about the scenarios, see [Introduction to Time-Consuming Task Concurrency](../../arkts-utils/time-consuming-task-overview.md).

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name  | Type                                                 | Mandatory | Description                                 |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------ |
| key     | [PropertyKey](arkts-apis-image-e.md#propertykey7)                                               | Yes   | Image property name.                         |

**Return value**

| Type             | Description                                                              |
| ---------------- | ----------------------------------------------------------------- |
| string | Value of the specified property key in the image Exif (the default value of the property is returned if the value fails to be obtained). For details about the function of each value, see [PropertyKey](arkts-apis-image-e.md#propertykey7). |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 7700101  | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed.|
| 7700102 | Unsupported MIME type.|
| 7700202 | Unsupported metadata. For example, key is not supported.|

**Example**

```ts
function GetImagePropertySync(context : Context) {
  let resourceMgr = context.resourceManager;
  if (resourceMgr == null) {
    return;
  }
  let fd = resourceMgr.getRawFdSync("example.jpg");

  const imageSourceObj = image.createImageSource(fd);
  console.info("getImagePropertySync");
  let bits_per_sample = imageSourceObj.getImagePropertySync(image.PropertyKey.BITS_PER_SAMPLE);
  console.info("bits_per_sample : " + bits_per_sample);
}
```

## modifyImageProperty<sup>11+</sup>

modifyImageProperty(key: PropertyKey, value: string): Promise\<void>

Modifies the value of an image property by the specified key. This API uses a promise to return the result asynchronously.

This API supports only JPEG, PNG, HEIF<sup>12+</sup>, and WEBP<sup>23+</sup> files (support varies with hardware devices), and the files must contain Exif information.

> **NOTE**
>
> - Calling modifyImageProperty to modify a property changes the byte length of the property. Calling modifyImageProperty on an ImageSource created from a buffer will cause the buffer content to be overwritten. Currently, an ImageSource created from a buffer does not support this API. Use an ImageSource created from an fd or a path instead.
> 
> - When calling modifyImageProperty to modify an Exif field, ensure that the corresponding image file has write permission. Otherwise, the field modification will fail.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name  | Type   | Mandatory | Description         |
| ------- | ------ | ---- | ------------ |
| key     | [PropertyKey](arkts-apis-image-e.md#propertykey7)   | Yes   | Image property name. |
| value   | string | Yes   | Attribute value.     |

**Return value**

| Type           | Description                        |
| -------------- | --------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 401  | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;    |
| 62980123| The image does not support EXIF decoding.             |
| 62980133| The EXIF data is out of range.             |
| 62980135| The EXIF value is invalid.             |
| 62980146| The EXIF data failed to be written to the file.        |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.modifyImageProperty(image.PropertyKey.IMAGE_WIDTH, "120").then(() => {
    imageSourceObj.getImageProperty(image.PropertyKey.IMAGE_WIDTH).then((width: string) => {
      console.info(`ImageWidth is :${width}`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get the Image Width, error.code ${error.code}, error.message ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to modify the Image Width, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## modifyImageProperties<sup>12+</sup>

modifyImageProperties(records: Record<PropertyKey, string|null>): Promise\<void>

Modifies the values of image properties in batches by using the specified keys. This API uses a promise to return the result.

This API supports only JPEG, PNG, HEIF, and WEBP<sup>23+</sup> files (support varies with hardware devices), and the files must contain Exif information.

> **NOTE**
>
> - Calling modifyImageProperties to modify a property changes the byte length of the property. Calling modifyImageProperties on an ImageSource created from a buffer will overwrite the buffer content. Currently, an ImageSource created from a buffer does not support this API. Use an ImageSource created from an fd or a path instead.
> - When calling modifyImageProperties to modify an Exif field, ensure that the corresponding image file has write permission. Otherwise, the field modification will fail.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name  | Type   | Mandatory | Description         |
| ------- | ------ | ---- | ------------ |
| records     | Record<[PropertyKey](arkts-apis-image-e.md#propertykey7), string \| null>   | Yes   | Array of image property names and property values. |

**Return value**

| Type           | Description                        |
| -------------- | --------------------------- |
| Promise\<void> |  Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 401  | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed;      |
| 62980123| The image does not support EXIF decoding.             |
| 62980135| The EXIF value is invalid.             |
| 62980146| The EXIF data failed to be written to the file.             |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperties(imageSourceObj : image.ImageSource) {
  let keyValues: Record<PropertyKey, string|null> = {
    [image.PropertyKey.IMAGE_WIDTH] : "1024",
    [image.PropertyKey.IMAGE_LENGTH] : "1024"
  };
  let checkKey = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  imageSourceObj.modifyImageProperties(keyValues).then(() => {
    imageSourceObj.getImageProperties(checkKey).then((data) => {
      console.info(`Image Width and Image Height:${data}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
  });
}
```

## modifyImagePropertiesEnhanced<sup>22+</sup>

modifyImagePropertiesEnhanced(records: Record\<string, string | null\>): Promise\<void\>

Modifies image properties in batches. This API uses a promise to return the result.

> **NOTE**
>
> - Calling this API to modify properties changes the byte length of the properties. It is recommended that you create an [image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource7) instance by passing in a file descriptor, or create an [image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource) instance by passing in a URI.
> - This API completes batch data modification in memory and then writes the data to the file at one time, which is more efficient than [modifyImageProperties](#modifyimageproperties12).
> - This API supports modifying the image properties of JPEG, PNG, HEIF, and WEBP files. The image must contain Exif information.
> - When calling modifyImagePropertiesEnhanced to modify Exif fields, ensure that the corresponding image file has write permission. Otherwise, the field modification fails.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------ | ---- | ------------ |
| records | Record\<string, string \| null>| Yes | Set of key-value pairs containing image property names and property values. |

**Return value**

| Type | Description |
| -------------- | --------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 7700102 | Unsupported MIME type.             |
| 7700202 | Unsupported metadata. For example, the property key is not supported, or the property value is invalid.             |
| 7700304 | Failed to write image properties to the file.             |

**Example**
```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImagePropertiesEnhanced(imageSourceObj : image.ImageSource) {
  let keyValues: Record<string, string|null> = {
    "ImageWidth" : "1024",
    "ImageLength" : "1024"
  };
  let checkKey = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  imageSourceObj.modifyImagePropertiesEnhanced(keyValues).then(() => {
    imageSourceObj.getImageProperties(checkKey).then((data) => {
      console.info(`Image Width and Image Height:${data}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
  });
}
```

## readImageMetadata<sup>23+</sup>

readImageMetadata(propertyKeys?: string[], index?: number): Promise\<ImageMetadata>

Reads the metadata of an image source, with the metadata fields specified by propertyKeys. This API uses a promise to return the result asynchronously.

This API supports only JPEG, PNG, HEIF, WebP, DNG, GIF, TIFF, HEIFS, JFIF, and AVIS files (support varies with hardware devices), and the files must contain Exif information.

> **NOTE**
>
> - When an application uses [PhotoAccessHelper](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md) to query images in the media library and obtains image data through the returned PhotoAsset, propertyKeys should be set to GPS-related Exif tag strings such as GPSLatitude, GPSLongitude, GPSAltitude, GPSTimeStamp, and GPSDateStamp when this API is used. Before reading these fields, declare and request the [ohos.permission.MEDIA_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionmedia_location) permission from the user. If all the preceding fields return 0 or empty, check whether the permission has been granted and whether the original image contains GPS information.
> - When reading a DNG image, this API applies special handling to some propertyKeys. For the string values of the following fields, refer to the values in [PropertyKey](arkts-apis-image-e.md#propertykey7):
>   - NewSubfileType, ImageWidth, ImageLength, DefaultCropSize, Orientation, Compression, PhotometricInterpretation, PlanarConfiguration, RowsPerStrip, StripOffsets, StripByteCounts, SamplesPerPixel, BitsPerSample, YCbCrCoefficients, YCbCrSubSampling, YCbCrPositioning, ReferenceBlackWhite, XResolution, YResolution, and ResolutionUnit: return the field values related to the main image.
>   - ImageUniqueID: validated according to the specification. An empty string is returned if the value does not comply with the specification.
>   - ExifVersion, FlashpixVersion, and ColorSpace: an error code is returned if the tag does not exist in the image.
>   - DNGVersion: 1.0.0.0 is returned if the version number is earlier than 1.0.0.0.
>   - GPSVersionID: the GPS version number is cleared and 0 is returned if there is no valid GPS data.
>   - GPSAltitudeRef: set to 0xFFFFFFFF if GPSAltitude is not set.
>   - ISOSpeedRatings: if the tag value is 0 or 65535, the recommended exposure index is used first; if it does not exist, the standard output sensitivity, ISO speed, and exposure index are used in sequence.
>   - Since API version 24, reading DNG metadata is supported. For details about the properties to query, see [DngPropertyKey](arkts-apis-image-e.md#dngpropertykey24).
>   - Since API version 24, reading HEIFS metadata is supported. For details about the properties to query, see [HeifsPropertyKey](arkts-apis-image-e.md#heifspropertykey23).
>   - Since API version 26.0.0, reading PNG metadata is supported. For details about the properties to query, see [PngPropertyKey](arkts-apis-image-e.md#pngpropertykey).
>   - Since API version 26.0.0, reading JFIF metadata is supported. For details about the properties to query, see [JfifPropertyKey](arkts-apis-image-e.md#jfifpropertykey).
>   - Since API version 26.0.0, reading TIFF metadata is supported. For details about the properties to query, see [TiffPropertyKey](arkts-apis-image-e.md#tiffpropertykey).
>   - Since API version 26.0.0, reading GIF metadata is supported. For details about the properties to query, see [GifPropertyKey](arkts-apis-image-e.md#gifpropertykey20).
>   - Since API version 26.0.0, reading XMP metadata of JPEG, PNG, GIF, DNG, and TIFF images is supported. For details about how to operate XMP metadata, see [XMPMetadata](arkts-apis-image-XMPMetadata.md).
>   - Since API version 26.0.0, reading AVIS metadata is supported. For details about the properties to query, see [AvisPropertyKey](arkts-apis-image-e.md#avispropertykey).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name        | Type     | Mandatory | Description                      |
| ------------ | -------- | ---- | ------------------------- |
| propertyKeys | string[] | No   | Array of image property names. If propertyKeys is not specified, all supported metadata is returned.        |
| index        | number   | No   | Index of interest. The default value is 0. |

**Return value**

| Type                                                         | Description                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<[ImageMetadata](arkts-apis-image-i.md#imagemetadata23)> | Promise object that returns an ImageMetadata object, which contains the metadata objects corresponding to the image property names. The image property values can be obtained through the metadata objects in ImageMetadata. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message               |
| -------- | ---------------------- |
| 7700102  | Unsupported MIME type. |
| 7700202  | Unsupported metadata.  |
| 7700204  | Invalid parameter. Possible causes: 1. The index is negative. 2. The index is greater than or equal to the number of frames in the image.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadImageMetadata(imageSourceObj : image.ImageSource) {
  let propertyKeys = ["ImageWidth", "HwMnoteIsXmageSupported"];
  await imageSourceObj.readImageMetadata(propertyKeys).then((metaData: image.ImageMetadata) => {
    if (metaData != undefined && metaData.exifMetadata != undefined &&
      metaData.makerNoteHuaweiMetadata != undefined) {
      console.info("ImageWidth: " + metaData.exifMetadata.imageWidth +
        " HwMnoteIsXmageSupported: " + metaData.makerNoteHuaweiMetadata.isXmageSupported);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to read image metadata. error.code is ${error.code}, error.message is ${error.message}`);
  })
}
```

## writeImageMetadata<sup>23+</sup>

writeImageMetadata(imageMetadata: ImageMetadata): Promise\<void>

Batch modifies image properties. This API uses a promise to return the result.

> **NOTE**
>
> - Calling this API to modify properties changes the byte length of the properties. It is recommended that you create an [image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource7) instance by passing a file descriptor or create an [image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource) instance by passing a URI.
> - This method completes the batch data modification in memory and then writes the data to the file at one time, which is more efficient than [modifyImageProperties](#modifyimageproperties12).
> - This method supports modifying the image properties of JPEG, PNG, and HEIF files. The image must contain Exif information. Before modifying the properties, query the supportedFormats property to check whether the device supports Exif read and write for the HEIF format.
> - Since API version 26.0.0, modifying the XMP metadata of JPEG, PNG, and GIF images is supported. For details about how to operate XMP metadata, see [XMPMetadata](arkts-apis-image-XMPMetadata.md).
> - When calling writeImageMetadata to modify Exif fields, ensure that the corresponding image file has write permission. Otherwise, the field modification fails.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name          | Type                                                   | Mandatory | Description             |
| ------------- | ------------------------------------------------------ | --------- | ----------------------- |
| imageMetadata | [ImageMetadata](arkts-apis-image-i.md#imagemetadata23) | Yes       | Metadata set of the image. If all property values in imageMetadata are empty, all Exif metadata is cleared. |

**Return value**

| Type           | Description                      |
| -------------- | -------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message               |
| -------- | ---------------------- |
| 7700102  | Unsupported MIME type. |
| 7700202  | Unsupported metadata.  |
| 7700204  | Invalid parameter. Possible causes: The imageSource object is released.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function WriteImageMetadata(imageSourceObj : image.ImageSource) {
  let propertyKeys = ["ImageWidth", "HwMnoteIsXmageSupported"];
  let metaData = await imageSourceObj.readImageMetadata(propertyKeys);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    metaData.exifMetadata.imageLength = 3072;
  }
  await imageSourceObj.writeImageMetadata(metaData).then(() => {
    console.info(`Succeeded in writing image metadata.`);
  }).catch((error: BusinessError) => {
    console.error(`Failed to write image metadata. error.code is ${error.code}, error.message is ${error.message}`);
  });
}
```

## readImageMetadataByType<sup>24+</sup>

readImageMetadataByType(metadataTypes?: MetadataType[], index?: number): Promise\<ImageMetadata>

Reads the metadata of an image source, with the metadata types specified by metadataTypes. If metadataTypes is not specified, all supported metadata is returned. This API uses a promise to return the result asynchronously.

This API supports only JPEG, PNG, HEIF, WebP, DNG, GIF, TIFF, HEIFS, JFIF, and AVIS files (support varies with hardware devices).

> **NOTE**
>
> - The EXIF_METADATA metadata type applies to JPEG, PNG, HEIF, WEBP, and DNG images.
> - The HEIFS_METADATA metadata type applies to HEIFS images.
> - If the passed MetadataType does not match the image format, error code 7700102 is returned.
> - Since API version 24, reading DNG metadata is supported. For details about the properties to query, see [DngPropertyKey](arkts-apis-image-e.md#dngpropertykey24).
> - Since API version 24, reading HEIFS metadata is supported. For details about the properties to query, see [HeifsPropertyKey](arkts-apis-image-e.md#heifspropertykey23).
> - Since API version 26.0.0, reading PNG metadata is supported. For details about the properties to query, see [PngPropertyKey](arkts-apis-image-e.md#pngpropertykey).
> - Since API version 26.0.0, reading JFIF metadata is supported. For details about the properties to query, see [JfifPropertyKey](arkts-apis-image-e.md#jfifpropertykey).
> - Since API version 26.0.0, reading TIFF metadata is supported. For details about the properties to query, see [TiffPropertyKey](arkts-apis-image-e.md#tiffpropertykey).
> - Since API version 26.0.0, reading GIF metadata is supported. For details about the properties to query, see [GifPropertyKey](arkts-apis-image-e.md#gifpropertykey20).
> - Since API version 26.0.0, reading XMP metadata of JPEG, PNG, GIF, DNG, and TIFF images is supported. For how to operate XMP metadata, see [XMPMetadata](arkts-apis-image-XMPMetadata.md).
> - Since API version 26.0.0, reading AVIS metadata is supported. For details about the properties to query, see [AvisPropertyKey](arkts-apis-image-e.md#avispropertykey).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name          | Type            | Mandatory | Description                      |
| ------------- | -------------- | ---- | ------------------------- |
| metadataTypes | [MetadataType](arkts-apis-image-e.md#metadatatype13)[] | No   | Array of metadata types. If this parameter is omitted, all supported metadata is obtained. |
| index         | number         | No   | Index of the image frame, indicating the frame whose metadata is to be obtained. The default value is 0.<br>- For a single-frame image, the value of index can only be 0.<br>- For a multi-frame image such as an animated image, the value range of index is [0, frame count - 1]. |

**Return value**

| Type                                                         | Description                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<[ImageMetadata](arkts-apis-image-i.md#imagemetadata23)> | Promise object. The returned ImageMetadata object contains the corresponding metadata object, through which the image property values can be obtained. |

**Error codes**

For details about the following error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message               |
| -------- | ---------------------- |
| 7700102  | Unsupported MIME type. |
| 7700202  | Unsupported metadata.  |
| 7700204  | Invalid parameter. Possible causes: 1.The index is negative.2. The index is greater than or equal to the number of frames in the image. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function ReadImageMetadataByType(imageSource : image.ImageSource, type: image.MetadataType) {
  let types: image.MetadataType[] = [type];
  await imageSource.readImageMetadataByType(types, 0).then((metaData: image.ImageMetadata) => {
    if (metaData != undefined && metaData.exifMetadata != undefined) {
      console.info("ImageWidth: " + metaData.exifMetadata.imageWidth);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to read image metadata by type. error.code is ${error.code}, error.message is ${error.message}`);
  })
}
```

## createImageRawData<sup>24+</sup>

createImageRawData(): Promise\<ImageRawData>

Obtains the raw data of an image. This API uses a promise to return the result asynchronously. Currently, only the raw data of DNG images is supported.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Return value**

| Type           | Description                      |
| -------------- | ------------------------- |
| Promise\<[ImageRawData](arkts-apis-image-i.md#imagerawdata24)> | Promise used to return an ImageRawData object, which contains the data buffer and pixel bit depth. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message               |
| -------- | ---------------------- |
| 7700101  | Bad source.  |
| 7700102  | Unsupported MIME type. |

**Example**
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function createImageRawData(imageSourceObj: image.ImageSource) {
  await imageSourceObj.createImageRawData().then((data: image.ImageRawData) => {
    console.info(`createImageRawData successfully. length: ${data.buffer.byteLength}, bitPerPixel:${data.bitsPerPixel}`);
    if (data.bitsPerPixel == 16) {
      let array: Uint16Array = new Uint16Array();
      let value: string = "";
      array = new Uint16Array(data.buffer);
      for (let i = 0; i < array.length && i < 10; i++) {
        value += array[i] + ', ';
      }
      console.info(`get dng rawdata is:${value}.`);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to create image rawData. error.code is ${error.code}, error.message is ${error.message}`);
  });
}
```

## updateData<sup>9+</sup>

updateData(buf: ArrayBuffer, isFinished: boolean, offset: number, length: number): Promise\<void>

Updates the incremental data. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name     | Type        | Mandatory | Description         |
| ---------- | ----------- | ---- | ------------ |
| buf        | ArrayBuffer         | Yes   | Buffer that stores the incremental data.           |
| isFinished | boolean             | Yes   | Whether the data update is complete. The value **true** indicates that the data update is complete and the current buffer stores the last segment of data; the value **false** indicates that the data update is not complete and more data needs to be updated.|
| offset      | number              | Yes   | Offset of the first address of the data in the current buffer relative to the first address of the entire image file, in bytes.             |
| length     | number              | Yes   | Length of the current buffer, in bytes.            |

**Return value**

| Type           | Description                       |
| -------------- | -------------------------- |
| Promise\<void> | Promise that returns no value.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function UpdateDatay(imageSourceObj : image.ImageSource) {
  const array: ArrayBuffer = new ArrayBuffer(100);
  try {
    // This API is asynchronous. Ensure the execution sequence when calling it.
    await imageSourceObj.updateData(array, false, 0, 10);
    console.info('Succeeded in updating data.');
  } catch (err) {
    const e: BusinessError = err as BusinessError;
    console.error(`Failed to update data.code is ${e.code},message is ${e.message}`);
  }
}
```


## updateData<sup>9+</sup>

updateData(buf: ArrayBuffer, isFinished: boolean, offset: number, length: number, callback: AsyncCallback\<void>): void

Updates incremental data. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name       | Type                | Mandatory | Description                 |
| ---------- | ------------------- | ---- | -------------------- |
| buf        | ArrayBuffer         | Yes  | Buffer that stores the incremental data.           |
| isFinished | boolean             | Yes  | Whether the data update is complete. The value **true** indicates that the data update is complete and the current buffer stores the last segment of data; the value **false** indicates that the data update is not complete and more data needs to be updated. |
| offset      | number              | Yes  | Offset of the start address of the data in the current buffer relative to the start address of the entire image file, in bytes.             |
| length     | number              | Yes  | Length of the current buffer, in bytes.            |
| callback   | AsyncCallback\<void> | Yes  |  Callback used to return the result. If the incremental data is updated successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function UpdateDatay(imageSourceObj : image.ImageSource) {
  const array: ArrayBuffer = new ArrayBuffer(100);
  imageSourceObj.updateData(array, false, 0, 10, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update data.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in updating data.');
    }
  })
}
```

## createPicture<sup>13+</sup>

createPicture(options?: DecodingOptionsForPicture): Promise\<Picture>

Creates a Picture object based on the image decoding options. This API uses a promise to return the result.

Since an image occupies a large amount of memory, call [release](./arkts-apis-image-Picture.md#release13) to release the memory in a timely manner after the Picture object is no longer used.

Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------------------------------------------------------ | ---- | ---------- |
| options | [DecodingOptionsForPicture](arkts-apis-image-i.md#decodingoptionsforpicture13) | No | Decoding options. |

**Return value**

| Type | Description |
| ---------------------------- | -------------------------- |
| Promise\<[Picture](arkts-apis-image-Picture.md)> | Promise used to return the Picture object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| -------- | ------------------------------------------------------------ |
| 401 | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 7700203 | Unsupported options. For example, unsupported desiredPixelFormat causes a failure in converting an image into the desired pixel format. <br>Applicable versions: 24+ |
| 7700301 | Decode failed. |

**Example**

```ts
async function CreatePicture(imageSourceObj : image.ImageSource) {
  let options: image.DecodingOptionsForPicture = {
    desiredAuxiliaryPictures: [image.AuxiliaryPictureType.GAINMAP] // GAINMAP is the auxiliary picture type to be decoded. 
  };
  let pictureObj: image.Picture = await imageSourceObj.createPicture(options);
  if (pictureObj != null) {
    console.info('Succeeded in creating picture.');
  } else {
    console.error('Failed to create picture.');
  }
}
```

## createPictureAtIndex<sup>20+</sup>

createPictureAtIndex(index: number): Promise\<Picture>

Creates a Picture object from the image at the specified index. This API uses a promise to return the result.

> **NOTE**
>
> - GIF and HEIF<sup>23+</sup> image sequence formats are supported. Since API version 26.0.0, the AVIS format is also supported.
> - Because an image occupies a large amount of memory, call [release](./arkts-apis-image-Picture.md#release13) to release the memory in a timely manner when the Picture object is no longer used.
> - Before releasing the object, ensure that all asynchronous methods of the object have been executed and the object will no longer be used.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name  | Type   | Mandatory | Description                                                        |
| ----- | ------ | --------- | ------------------------------------------------------------------ |
| index | number | Yes       | Index of the image to decode. The valid value range is [0, (frame count - 1)]. |

**Return value**

| Type                         | Description                         |
| ---------------------------- | ----------------------------------- |
| Promise\<[Picture](arkts-apis-image-Picture.md)> | Promise object used to return the Picture. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message                                                      |
| -------- | ------------------------------------------------------------ |
| 7700101  | Bad source. |
| 7700102  | Unsupported MIME type. |
| 7700103  | Image too large. |
| 7700203  | Unsupported options. For example, index is invalid. |
| 7700301  | Decoding failed. |

**Example**

```ts
async function CreatePictures(imageSourceObj : image.ImageSource) {
  let frameCount: number = await imageSourceObj.getFrameCount();
  for (let index = 0; index < frameCount; index++) {
    try {
      let pictureObj: image.Picture = await imageSourceObj.createPictureAtIndex(index);
      console.info('Succeeded in creating picture for frame: ' + index);
    } catch (error) {
      console.error('Failed to create picture for frame: ' + index);
    }
  }
}
```

## createPixelMap<sup>7+</sup>

createPixelMap(options?: DecodingOptions): Promise\<PixelMap>

Creates a PixelMap object based on the image decoding options. This API uses a promise to return the result.

The system automatically selects shared memory or DMA memory. Since API version 15, when a memory type needs to be specified, call [createPixelMapUsingAllocator](#createpixelmapusingallocator15) and set **allocatorType** to **image.AllocatorType.DMA** or **image.AllocatorType.SHARE_MEMORY**. For details, see [System Default Memory Allocation Mode](../../media/image/image-allocator-type.md#default-memory-allocation-method).

> **NOTE**
>
> - This method is not thread-safe and does not support concurrent invocation on the same ImageSource instance.
> - Because an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner when the PixelMap object is no longer used.
> - When releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name    | Type                                 | Mandatory | Description       |
| ------- | ------------------------------------ | --------- | ----------------- |
| options | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7) | No        | Decoding options. |

**Return value**

| Type                             | Description                  |
| -------------------------------- | ---------------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)> | Promise that returns the PixelMap. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap(imageSourceObj : image.ImageSource) {
  imageSourceObj.createPixelMap().then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating pixelMap object through image decoding parameters.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create pixelMap object through image decoding parameters, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## createPixelMap<sup>7+</sup>

createPixelMap(callback: AsyncCallback\<PixelMap>): void

Creates a PixelMap object with default parameters. This API uses an asynchronous callback to return the result.

The system automatically selects shared memory or DMA memory. Since API version 15, when a memory type needs to be specified, call [createPixelMapUsingAllocator](#createpixelmapusingallocator15) and set **allocatorType** to **image.AllocatorType.DMA** or **image.AllocatorType.SHARE_MEMORY**. For details, see [Default Memory Allocation Method](../../media/image/image-allocator-type.md#default-memory-allocation-method).

> **NOTE**
>
> - This method is not thread-safe and does not support concurrent calls on the same ImageSource instance.
> - Since an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner when the PixelMap object is no longer used.
> - When releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name     | Type                                  | Mandatory | Description                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<[PixelMap](arkts-apis-image-PixelMap.md)> | Yes   | Callback used to return the result. If the PixelMap object is created successfully, err is undefined and data is the obtained PixelMap object; otherwise, err is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap(imageSourceObj : image.ImageSource) {
  imageSourceObj.createPixelMap((err: BusinessError, pixelMap: image.PixelMap) => {
    if (err) {
      console.error(`Failed to create pixelMap.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in creating pixelMap object.');
    }
  })
}
```

## createPixelMap<sup>7+</sup>

createPixelMap(options: DecodingOptions, callback: AsyncCallback\<PixelMap>): void

Creates a PixelMap object based on the image decoding options. This API uses an asynchronous callback to return the result.

The system automatically selects shared memory or DMA memory. Since API version 15, when a specific memory type is required, call [createPixelMapUsingAllocator](#createpixelmapusingallocator15) and set **allocatorType** to **image.AllocatorType.DMA** or **image.AllocatorType.SHARE_MEMORY**. For details, see [Default Memory Allocation Mode](../../media/image/image-allocator-type.md#default-memory-allocation-method).

> **NOTE**
>
> - This method is not thread-safe. Do not call it concurrently on the same ImageSource instance.
> - Because an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner when the PixelMap object is no longer used.
> - Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name     | Type                                  | Mandatory | Description                       |
| -------- | ------------------------------------- | --------- | -------------------------- |
| options  | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7)  | Yes   | Decoding options.                 |
| callback | AsyncCallback<[PixelMap](arkts-apis-image-PixelMap.md)> | Yes   | Callback invoked to return the result. If the PixelMap object is created successfully, err is undefined and data is the obtained PixelMap object; otherwise, err is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap(imageSourceObj : image.ImageSource) {
  let decodingOptions: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 1, height: 2 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 1, height: 2 }, x: 0, y: 0 },
    // If both desiredSize and desiredRegion are passed to the decoding API, also pass cropAndScaleStrategy to specify the order of scaling and cropping. CROP_FIRST is recommended.
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  imageSourceObj.createPixelMap(decodingOptions, (err: BusinessError, pixelMap: image.PixelMap) => {
    if (err) {
      console.error(`Failed to create pixelMap.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in creating pixelMap object.');
    }
  })
}
```

## createPixelMapSync<sup>12+</sup>

createPixelMapSync(options?: DecodingOptions): PixelMap

Creates a **PixelMap** object synchronously based on the image decoding options.

Because an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in time when the **PixelMap** object is no longer used.

Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

The system automatically selects shared memory or DMA memory. Since API version 15, to specify the memory type, call [createPixelMapUsingAllocatorSync](#createpixelmapusingallocatorsync15) and set **allocatorType** to **image.AllocatorType.DMA** or **image.AllocatorType.SHARE_MEMORY**. For details, see [Default Memory Allocation Mode of the System](../../media/image/image-allocator-type.md#default-memory-allocation-method).

> **NOTE**
>
> This method is synchronous and blocks the current thread when called. It is not recommended to call it in the main thread, as this may cause the application to freeze, drop frames, or respond slowly. For details about the scenarios, see [Introduction to Concurrent Processing of Time-Consuming Tasks](../../arkts-utils/time-consuming-task-overview.md).

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name   | Type                                  | Mandatory | Description                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| options  | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7)  | No   | Image decoding options.                 |

**Return value**

| Type                             | Description                  |
| -------------------------------- | --------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | **PixelMap** object used to return the creation result synchronously. |

**Example**

```ts
function CreatePixelMapSync(context : Context) {
  // 'test.jpg' is used as an example only. Replace it with your own file; otherwise, the imageSource creation fails and subsequent operations cannot be performed properly.
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let decodingOptions: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 1, height: 2 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 1, height: 2 }, x: 0, y: 0 },
    // If both desiredSize and desiredRegion are passed to the decoding API, also pass cropAndScaleStrategy to specify the order of scaling and cropping. CROP_FIRST is recommended.
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  let pixelmap = imageSource.createPixelMapSync(decodingOptions);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}
```

## createPixelMapList<sup>10+</sup>

createPixelMapList(options?: DecodingOptions): Promise<Array\<PixelMap>>

Creates an array of PixelMap objects based on the image decoding parameters. This API uses a promise to return the result asynchronously.

For an animated image (such as a GIF or WebP), this API returns the image data of each frame. For a static image, this API returns the image data of the only frame.

> **NOTE**
>
> - This method is not thread-safe and does not support concurrent invocation on the same ImageSource instance.
> - Because an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner after the PixelMap object is no longer used.
> - When releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.
> - This API decodes all frames at once. When there are too many frames or a single frame is too large (for example, a 100-frame GIF animated image of 2000×3000 pixels), a large amount of memory is occupied, which may cause system memory shortage. In this case, you are advised to use the Image component to display the animated image. The Image component decodes frames one by one and therefore occupies less memory than this API.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name   | Type                                  | Mandatory | Description                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| options  | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7)  | No   | Decoding parameters.                 |

**Return value**

| Type                             | Description                  |
| -------------------------------- | --------------------- |
| Promise<Array<[PixelMap](arkts-apis-image-PixelMap.md)>> | Array of PixelMap objects returned asynchronously. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 62980096| The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.              |
| 62980099 | The shared memory data is abnormal. |
| 62980101 | The image data is abnormal. |
| 62980103| The image data is not supported.             |
| 62980106 | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| 62980109 | Failed to crop the image. |
| 62980111| The image source data is incomplete.           |
| 62980115 | Invalid image parameter. |
| 62980116 | Failed to decode the image. |
| 62980118| Failed to create the image plugin.             |
| 62980137 | Invalid media operation. |
| 62980173 | The DMA memory does not exist. |
| 62980174 | The DMA memory data is abnormal. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapList(imageSourceObj : image.ImageSource) {
  let decodeOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 198, height: 202 },
    rotate: 0,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    index: 0,
  };
  imageSourceObj.createPixelMapList(decodeOpts).then((pixelMapList: Array<image.PixelMap>) => {
    console.info('Succeeded in creating pixelMapList object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create pixelMapList object, error code is ${err}`);
  })
}
```

## createPixelMapList<sup>10+</sup>

createPixelMapList(callback: AsyncCallback<Array\<PixelMap>>): void

Creates an array of PixelMap objects with the default options. This API uses an asynchronous callback to return the result.

For an animated image (such as a GIF or WebP), this API returns the image data of each frame. For a static image, this API returns the image data of the only frame.

> **NOTE**
>
> - This method is not thread-safe. Concurrent invocation on the same ImageSource instance is not supported.
> - Since images occupy a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner after the PixelMap object is no longer used.
> - Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.
> - This API decodes all frames at once. When there are too many frames or a single frame is too large, it occupies a large amount of memory and may cause system memory shortage. In this case, you are advised to use the Image component to display the animated image. The Image component decodes frames one by one and therefore occupies less memory than this API.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name     | Type                                  | Mandatory | Description                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<Array<[PixelMap](arkts-apis-image-PixelMap.md)>> | Yes   | Callback invoked to return the array of PixelMap objects. If the operation is successful, err is undefined and data is the obtained array of PixelMap objects. Otherwise, err is an error object.  |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980099 | The shared memory data is abnormal.  |
| 62980101 | The image data is abnormal.          |
| 62980103 | The image data is not supported.         |
| 62980106 | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| 62980109 | Failed to crop the image.            |
| 62980111 | The image source data is incomplete. |
| 62980115 | Invalid image parameter.      |
| 62980116 | Failed to decode the image.         |
| 62980118 | Failed to create the image plugin.   |
| 62980137 | Invalid media operation.     |
| 62980173 | The DMA memory does not exist.        |
| 62980174 | The DMA memory data is abnormal.    |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapList(imageSourceObj : image.ImageSource) {
  imageSourceObj.createPixelMapList((err: BusinessError, pixelMapList: Array<image.PixelMap>) => {
    if (err) {
      console.error(`Failed to create pixelMapList object, error code is ${err}`);
    } else {
      console.info('Succeeded in creating pixelMapList object.');
    }
  })
}
```

## createPixelMapList<sup>10+</sup>

createPixelMapList(options: DecodingOptions, callback: AsyncCallback<Array\<PixelMap>>): void

Creates a PixelMap array based on the image decoding options. This API uses an asynchronous callback to return the result.

For an animated image (such as a GIF or WebP), this API returns the data of each frame. For a static image, this API returns the data of the only frame.

> **NOTE**
>
> - This method is not thread-safe. Do not call it concurrently on the same ImageSource instance.
> - Since images occupy a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner after the PixelMap object is no longer used.
> - Before releasing the object, ensure that all asynchronous methods of the object have been executed and the object will no longer be used.
> - This API decodes all frames at a time. When there are too many frames or a single frame is too large, a large amount of memory is occupied, which may cause memory shortage. In this case, you are advised to use the Image component to display the animated image. The Image component decodes frames one by one and therefore occupies less memory than this API.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name   | Type                 | Mandatory | Description                               |
| -------- | -------------------- | ---- | ---------------------------------- |
| options | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7) | Yes | Decoding options. |
| callback | AsyncCallback<Array<[PixelMap](arkts-apis-image-PixelMap.md)>> | Yes   | Callback invoked to return the result. If the PixelMap object array is created successfully, err is undefined and data is the obtained PixelMap object array. Otherwise, err is an error object.  |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.            |
| 62980099 | The shared memory data is abnormal.  |
| 62980101 | The image data is abnormal.         |
| 62980103 | The image data is not supported.        |
| 62980106 | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| 62980109 | Failed to crop the image.           |
| 62980111 | The image source data is incomplete. |
| 62980115 | Invalid image parameter.      |
| 62980116 | Failed to decode the image.         |
| 62980118 | Failed to create the image plugin.  |
| 62980137 | Invalid media operation.      |
| 62980173 | The DMA memory does not exist.         |
| 62980174 | The DMA memory data is abnormal.     |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapList(imageSourceObj : image.ImageSource) {
  let decodeOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 198, height: 202 },
    rotate: 0,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    index: 0,
  };
  imageSourceObj.createPixelMapList(decodeOpts, (err: BusinessError, pixelMapList: Array<image.PixelMap>) => {
    if (err) {
      console.error(`Failed to create pixelMapList object, error code is ${err}`);
    } else {
      console.info('Succeeded in creating pixelMapList object.');
    }
  })
}
```

## createPixelMapUsingAllocator<sup>15+</sup>

createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType): Promise\<PixelMap>

Creates a PixelMap object asynchronously based on the image decoding parameters using the specified allocator. This API uses a promise to return the result. For details about how to use this API, see [Image Decoding Memory Optimization (ArkTS)](../../media/image/image-allocator-type.md).

> **NOTE**
>
> - This method is not thread-safe and does not support concurrent invocation on the same ImageSource instance.
> - Because an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner when the PixelMap object is no longer used.
> - When releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.
> - When the process where the caller resides has sandbox isolation enabled and AllocatorType.DMA is specified, or DMA memory is selected by AllocatorType.AUTO, configure the SELinux permission for accessing DMA memory-related resources for the sandbox process. Otherwise, the API call may be blocked or fail due to SELinux policy interception.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name        | Type                                 | Mandatory | Description                     |
| ------------- | ------------------------------------ | ---- | ------------------------ |
| options        | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7) | No   | Decoding parameters.               |
| allocatorType | [AllocatorType](arkts-apis-image-e.md#allocatortype15)   | No   | Memory type of the pixel map. The default value is **AllocatorType.AUTO**, in which case the system automatically selects shared memory or DMA memory. To specify a memory type, set this parameter to **AllocatorType.DMA** or **AllocatorType.SHARE_MEMORY**. |

**Return value**

| Type                             | Description                        |
| -------------------------------- | --------------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)> | Promise that returns the PixelMap. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types;3.Parameter verification failed. |
| 7700101  | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| 7700102  | Unsupported mimetype.                                        |
| 7700103  | Image too large.  This status code is thrown when an error occurs during the process of checking size. |
| 7700201  | Unsupported allocator type, e.g., use share memory to decode a HDR image as only DMA supported hdr metadata. |
| 7700203  | Unsupported options, e.g., cannot convert image into desired pixel format. |
| 7700301  | Failed to decode image.                                      |
| 7700302  | Failed to allocate memory.                                   |

**Example**

```ts
async function CreatePixelMapUsingAllocator(context : Context) {
  // 'test.jpg' is used only as an example. Replace it with the actual image; otherwise, the failure to create the imageSource will prevent subsequent operations from being executed properly.
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let decodingOptions: image.DecodingOptions = {
    editable: true,
    desiredSize: { width: 3072, height: 4096 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 3072, height: 4096 }, x: 0, y: 0 },
    // If both the desiredSize and desiredRegion parameters are passed to the decoding API, also pass the cropAndScaleStrategy parameter to specify the order of scaling and cropping. CROP_FIRST is recommended.
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  let pixelmap = imageSource.createPixelMapUsingAllocator(decodingOptions, image.AllocatorType.AUTO);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}
```

## createPixelMapUsingAllocatorSync<sup>15+</sup>

createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap

Synchronously creates a **PixelMap** object based on the image decoding options and the specified allocator. For details about how to use this API, see [Image Decoding Memory Optimization (ArkTS)](../../media/image/image-allocator-type.md).

Since an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner when the **PixelMap** object is no longer used.

Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

> **NOTE**
>
> - This is a synchronous method that blocks the current thread when called. It is not recommended to call it in the main thread, as doing so may cause the application to freeze, drop frames, or respond slowly. For details about the scenarios, see [Overview of Time-Consuming Task Concurrency Scenarios](../../arkts-utils/time-consuming-task-overview.md).
> - When the process of the caller has sandbox isolation enabled and **AllocatorType.DMA** is specified, or DMA memory is selected by **AllocatorType.AUTO**, configure the SELinux permission for accessing DMA memory-related resources for the sandbox process. Otherwise, the API call may be blocked or fail due to SELinux policy interception.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name        | Type                                 | Mandatory | Description                     |
| ------------- | ------------------------------------ | ---- | ------------------------ |
| options        | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7) | No   | Decoding options.               |
| allocatorType | [AllocatorType](arkts-apis-image-e.md#allocatortype15)   | No   | Memory type of the **PixelMap**. The default value is **AllocatorType.AUTO**, in which case the system automatically selects shared memory or DMA memory. To specify a memory type, set this parameter to **AllocatorType.DMA** or **AllocatorType.SHARE_MEMORY**. |

**Return value**

| Type                   | Description                   |
| ---------------------- | ---------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | Used to synchronously return the creation result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types;3.Parameter verification failed. |
| 7700101  | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| 7700102  | Unsupported mimetype.                                        |
| 7700103  | Image too large.  This status code is thrown when an error occurs during the process of checking size. |
| 7700201  | Unsupported allocator type, e.g., use share memory to decode a HDR image as only DMA supported hdr metadata. |
| 7700203  | Unsupported options, e.g., cannot convert image into desired pixel format. |
| 7700301  | Failed to decode image.                                      |
| 7700302  | Failed to allocate memory.                                   |

**Example**

```ts
async function CreatePixelMapUsingAllocator(context : Context) {
  // 'test.jpg' is used as an example only. Replace it with your own file; otherwise, the imageSource creation fails and subsequent operations cannot be performed properly.
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let decodingOptions: image.DecodingOptions = {
    editable: true,
    desiredSize: { width: 3072, height: 4096 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 3072, height: 4096 }, x: 0, y: 0 },
    // If both the desiredSize and desiredRegion parameters are passed to the decoding API, pass the cropAndScaleStrategy parameter to specify the order of scaling and cropping. CROP_FIRST is recommended.
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  let pixelmap = imageSource.createPixelMapUsingAllocatorSync(decodingOptions, image.AllocatorType.AUTO);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}
```

## createThumbnail

createThumbnail(options?: DecodingOptionsForThumbnail): Promise\<PixelMap \| undefined>

Creates a thumbnail PixelMap object based on the image decoding options. This API uses a promise to return the result.

Currently, thumbnail PixelMap objects can be created for images in JPEG and HEIF formats.

The thumbnail contained in the image file is decoded first. If the image file does not contain a thumbnail, the original image is decoded.

> **NOTE**
>
> - Concurrent calls on the same ImageSource instance are not supported.
> - Since an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner when the PixelMap object is no longer used.
> - Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name    | Type                                                         | Mandatory | Description       |
| ------- | ------------------------------------------------------------ | --------- | ----------------- |
| options | [DecodingOptionsForThumbnail](arkts-apis-image-i.md#decodingoptionsforthumbnail) | No        | Decoding options that control whether to generate a thumbnail and the target size of the generated thumbnail.<br>Default behavior:<br>- When the image contains a thumbnail, the original thumbnail is decoded, and the width and height of the returned PixelMap object are the same as those of the original thumbnail.<br>- When the original image file does not contain a thumbnail, the original image is decoded and then downsampled based on the decoding options to generate a thumbnail. The width and height of the generated thumbnail PixelMap object are both limited to 512 pixels or less. |

**Return value**

| Type                                                         | Description                        |
| ------------------------------------------------------------ | ---------------------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md) \| undefined> | Promise that returns the PixelMap. |

**Error codes**

For details about the error codes, see [Image error codes](errorcode-image.md).

| ID | Error Message                                       |
| -------- | ---------------------------------------------- |
| 7700102  | Unsupported mimetype.                          |
| 7700103  | Image too large.                               |
| 7700204  | Invalid parameter, e.g, invalid generate size. |
| 7700301  | Decode failed.                                 |
| 7700303  | Image does not carry thumbnail data.           |
| 7700305  | Thumbnail generation failed.                   |

**Example**

```ts
async function CreateThumbnail(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
  try {
    if (!imageSource) {
      console.error('CreateThumbnail: imageSource is null or undefined');
      return undefined;
    }
    const imageInfo = await imageSource.getImageInfo();
    const supportedMimeTypes = ['image/jpeg', 'image/heif', 'image/heic'];
    if (!supportedMimeTypes.includes(imageInfo.mimeType)) {
      console.error(`CreateThumbnail: Unsupported MIME type: ${imageInfo.mimeType}`);
      return undefined;
    }

    const decodingOptions: image.DecodingOptionsForThumbnail = {
      generateThumbnailIfAbsent: true,
      maxGeneratedPixelDimension: 200,
    };

    const pixelmap = await imageSource.createThumbnail(decodingOptions);
    if (pixelmap) {
      console.info('Succeeded in creating thumbnail pixelMap object.');
      return pixelmap;
    } else {
      console.error('Failed to create thumbnail pixelMap.');
      return undefined;
    }
  } catch (error) {
    console.error('CreateThumbnail error:', JSON.stringify(error));
    return undefined;
  }
}
```

## createThumbnailSync

createThumbnailSync(options?: DecodingOptionsForThumbnail): PixelMap \| undefined

Creates a thumbnail synchronously based on the image decoding options. Returns the [PixelMap](arkts-apis-image-PixelMap.md) object corresponding to the creation result.

Currently, this API supports creating a thumbnail PixelMap object for images in JPEG and HEIF formats.

The thumbnail contained in the image file is decoded first. If the image file does not contain a thumbnail, the original image is decoded.

> **NOTE**
>
> - Because an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to release the memory in a timely manner after the PixelMap object is no longer used.
> - Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.
> - This API is a synchronous method and blocks the current thread when called. It is not recommended to call it in the main thread, as doing so may cause the application to freeze, drop frames, or respond slowly. For details about the applicable scenarios, see [Introduction to Concurrent Processing of Time-Consuming Tasks](../../arkts-utils/time-consuming-task-overview.md).

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | ------------------------------------------------------------ | ---- | ---------- |
| options | [DecodingOptionsForThumbnail](arkts-apis-image-i.md#decodingoptionsforthumbnail) | No | Decoding options that control whether to generate a thumbnail and the target size of the generated thumbnail.<br>Default behavior:<br>- When the image contains a thumbnail, the original thumbnail is decoded, and the width and height of the returned PixelMap object are consistent with those of the original thumbnail.<br>- When the original image file does not contain a thumbnail, the original image is decoded and then downsampled based on the decoding options to generate a thumbnail. The width and height of the generated thumbnail PixelMap object are both limited to 512 pixels or less. |

**Return value**

| Type | Description |
| ----------------------------------------------------- | ---------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) \| undefined | Used to return the creation result synchronously. |

**Error codes**

For details about the following error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message                                       |
| -------- | ---------------------------------------------- |
| 7700102  | Unsupported mimetype.                          |
| 7700103  | Image too large.                               |
| 7700204  | Invalid parameter, e.g, invalid generate size. |
| 7700301  | Decode failed.                                 |
| 7700303  | Image does not carry thumbnail data.           |
| 7700305  | Thumbnail generation failed.                   |

**Example**

```ts
async function CreateThumbnailSync(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
  try {
    if (!imageSource) {
      console.error('CreateThumbnailSync: imageSource is null or undefined');
      return undefined;
    }
    const imageInfo = await imageSource.getImageInfo();
    const supportedMimeTypes = ['image/jpeg', 'image/heif', 'image/heic'];
    if (!supportedMimeTypes.includes(imageInfo.mimeType)) {
      console.error(`CreateThumbnailSync: Unsupported MIME type: ${imageInfo.mimeType}`);
      return undefined;
    }

    const decodingOptionsForThumbnail: image.DecodingOptionsForThumbnail = {
      generateThumbnailIfAbsent: true,
      maxGeneratedPixelDimension: 200,
    };

    const pixelmap = imageSource.createThumbnailSync(decodingOptionsForThumbnail);

    if (pixelmap) {
      console.info('Succeeded in creating thumbnail pixelMap object.');
      return pixelmap;
    } else {
      console.error('Failed to create thumbnail pixelMap.');
      return undefined;
    }
  } catch (error) {
    console.error('CreateThumbnailSync error:', JSON.stringify(error));
    return undefined;
  }
}
```

## getDelayTimeList<sup>10+</sup>

getDelayTimeList(callback: AsyncCallback<Array\<number>>): void

Obtains the image delay time array. This API uses an asynchronous callback to return the result. It is used only for GIF images and WebP images.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name     | Type                 | Mandatory | Description                               |
| -------- | -------------------- | --------- | ----------------------------------------- |
| callback | AsyncCallback<Array\<number>> | Yes       | Callback used to return the image delay time array. If the operation is successful, **err** is **undefined** and **data** is the obtained image delay time array. Otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 62980096| The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.              |
| 62980110| The image source data is incorrect.             |
| 62980111| The image source data is incomplete.            |
| 62980115 | Invalid image parameter. |
| 62980116| Failed to decode the image. |
| 62980118| Failed to create the image plugin. |
| 62980122| Failed to decode the image header. |
| 62980149 | Invalid MIME type for the image source. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetDelayTimeList(imageSourceObj : image.ImageSource) {
  imageSourceObj.getDelayTimeList((err: BusinessError, delayTimes: Array<number>) => {
    if (err) {
      console.error(`Failed to get delayTimes object.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting delayTimes object.');
    }
  })
}
```

## getDelayTimeList<sup>10+</sup>

getDelayTimeList(): Promise<Array\<number>>

Obtains the image delay time array. This API uses a promise to return the result asynchronously. It is applicable only to GIF and WebP images.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Return value**

| Type           | Description                        |
| -------------- | --------------------------- |
| Promise<Array\<number>> | Promise used to return the delay time array. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980110 | The image source data is incorrect.      |
| 62980111 | The image source data is incomplete. |
| 62980115 | Invalid image parameter.      |
| 62980116 | Failed to decode the image.          |
| 62980118 | Failed to create the image plugin.  |
| 62980122 | Failed to decode the image header.   |
| 62980149 | Invalid MIME type for the image source.      |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetDelayTimeList(imageSourceObj : image.ImageSource) {
  imageSourceObj.getDelayTimeList().then((delayTimes: Array<number>) => {
    console.info('Succeeded in getting delayTimes object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get delayTimes object.code is ${err.code},message is ${err.message}`);
  })
}
```

## getFrameCount<sup>10+</sup>

getFrameCount(callback: AsyncCallback\<number>): void

Obtains the frame count of an image. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name   | Type                 | Mandatory | Description                               |
| -------- | -------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback\<number> | Yes   | Callback invoked to return the result. If the operation is successful, **err** is **undefined** and **data** is the frame count obtained; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 62980096| The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980111| The image source data is incomplete. |
| 62980112| The image format does not match. |
| 62980113| Unknown image format.The image data provided is not in a recognized or supported format, or it may be corrupted.            |
| 62980115| Invalid image parameter. |
| 62980116| Failed to decode the image. |
| 62980118| Failed to create the image plugin. |
| 62980122| Failed to decode the image header. |
| 62980137| Invalid media operation. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetFrameCount(imageSourceObj : image.ImageSource) {
  imageSourceObj.getFrameCount((err: BusinessError, frameCount: number) => {
    if (err) {
      console.error(`Failed to get frame count.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting frame count.');
    }
  })
}
```

## getFrameCount<sup>10+</sup>

getFrameCount(): Promise\<number>

Obtains the frame count of the image. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Return value**

| Type           | Description                        |
| -------------- | --------------------------- |
| Promise\<number> | Promise used to return the frame count of the image. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980111 | The image source data is incomplete. |
| 62980112 | The image format does not match.        |
| 62980113| Unknown image format.The image data provided is not in a recognized or supported format, or it may be corrupted.            |
| 62980115 | Invalid image parameter.      |
| 62980116 | Failed to decode the image.          |
| 62980118 | Failed to create the image plugin.   |
| 62980122 | Failed to decode the image header.  |
| 62980137 | Invalid media operation.      |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetFrameCount(imageSourceObj : image.ImageSource) {
  imageSourceObj.getFrameCount().then((frameCount: number) => {
    console.info('Succeeded in getting frame count.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get frame count.code is ${err.code},message is ${err.message}`);
  })
}
```

## getDisposalTypeList<sup>12+</sup>

getDisposalTypeList(): Promise\<Array\<number>>

Obtains the disposal mode array of image frames. This API uses a promise to return the result asynchronously. This API is used only for GIF images.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Return value**

| Type           | Description                        |
| -------------- | --------------------------- |
| Promise\<Array\<number>> | Promise used to return the disposal mode array of image frames. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.      |
| 62980101 | The image data is abnormal. |
| 62980137 | Invalid media operation.        |
| 62980149 | Invalid MIME type for the image source.      |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetDisposalTypeList(imageSourceObj : image.ImageSource) {
  imageSourceObj.getDisposalTypeList().then((disposalTypes: Array<number>) => {
    console.info('Succeeded in getting disposalTypes object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get disposalTypes object.code ${err.code},message is ${err.message}`);
  })
}
```

## release

release(callback: AsyncCallback\<void>): void

Releases this ImageSource instance. This API uses an asynchronous callback to return the result.

Because an image occupies a large amount of memory, you should proactively call this method to release the memory in a timely manner after the ImageSource instance is no longer used.

Before releasing the instance, ensure that all asynchronous methods of the instance have been executed and that the instance will no longer be used.

**Atomic service API**: This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback\<void> | Yes | Callback invoked when the resource is released. If the release is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(imageSourceObj : image.ImageSource) {
  imageSourceObj.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the image source instance.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing the image source instance.');
    }
  })
}
```

## release

release(): Promise\<void>

Releases this ImageSource instance. This API uses a promise to return the result asynchronously.

Since an image occupies a large amount of memory, you should proactively call this method to release the memory in a timely manner after the ImageSource instance is no longer used.

Before releasing the instance, ensure that all asynchronous methods of the instance have been executed and that the instance will no longer be used.

**Atomic service API**: This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Return value**

| Type           | Description                        |
| -------------- | --------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(imageSourceObj : image.ImageSource) {
  imageSourceObj.release().then(() => {
    console.info('Succeeded in releasing the image source instance.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the image source instance.code ${error.code},message is ${error.message}`);
  })
}
```

## getImageProperty<sup>(deprecated)</sup>

getImageProperty(key:string, options?: GetImagePropertyOptions): Promise\<string>

Obtains the value of the specified property key of the image at the given index. This API uses a promise to return the result.

This API supports only JPEG, PNG, HEIF<sup>12+</sup>, and WEBP<sup>23+</sup> files (support varies with hardware devices), and the files must contain Exif information.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 11. You are advised to use [getImageProperty](#getimageproperty11) instead.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name    | Type                                                 | Mandatory | Description                                 |
| ------- | ---------------------------------------------------- | --------- | ------------------------------------------- |
| key     | string                                               | Yes       | Image property name.                        |
| options | [GetImagePropertyOptions](arkts-apis-image-i.md#getimagepropertyoptionsdeprecated) | No        | Image properties, including the image index and the default property value. |

**Return value**

| Type             | Description                                                              |
| ---------------- | ------------------------------------------------------------------------- |
| Promise\<string> | Promise object used to return the image property value. If the value fails to be obtained, the default property value is returned. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageProperty("BitsPerSample")
    .then((data: string) => {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }).catch((error: BusinessError) => {
    console.error(`Failed to get the value of the specified attribute key of the image, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## getImageProperty<sup>(deprecated)</sup>

getImageProperty(key:string, callback: AsyncCallback\<string>): void

Obtains the value of the specified property key of the image at the given index. This API uses an asynchronous callback to return the result.

This API supports only JPEG, PNG, HEIF<sup>12+</sup>, and WEBP<sup>23+</sup> files (support varies with hardware devices), and the files must contain Exif information.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 11. You are advised to use [getImageProperty](#getimageproperty11) instead.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name     | Type                   | Mandatory | Description                                                         |
| -------- | ---------------------- | --------- | ------------------------------------------------------------ |
| key      | string                 | Yes       | Image property name.                                                 |
| callback | AsyncCallback\<string> | Yes       | Callback used to return the image property value. If the operation is successful, **err** is **undefined** and **data** is the obtained image property value. Otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageProperty("BitsPerSample", (error: BusinessError, data: string) => {
    if (error) {
      console.error('Failed to get the value of the specified attribute key of the image.');
    } else {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }
  })
}
```

## getImageProperty<sup>(deprecated)</sup>

getImageProperty(key:string, options: GetImagePropertyOptions, callback: AsyncCallback\<string>): void

Obtains the value of the specified image property key. This API uses an asynchronous callback to return the result.

This API supports only JPEG, PNG, HEIF<sup>12+</sup>, and WEBP<sup>23+</sup> files (support varies by hardware device), and the files must contain Exif information.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 11. You are advised to use [getImageProperty](#getimageproperty11) instead.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name     | Type                                                 | Mandatory | Description                                                          |
| -------- | ---------------------------------------------------- | --------- | ------------------------------------------------------------- |
| key      | string                                               | Yes       | Image property name.                                                  |
| options  | [GetImagePropertyOptions](arkts-apis-image-i.md#getimagepropertyoptionsdeprecated) | Yes       | Image properties, including the image index and the default property value.                          |
| callback | AsyncCallback\<string>                               | Yes       | Callback used to return the image property value. If the operation is successful, **err** is **undefined** and **data** is the obtained image property value. Otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  let property: image.GetImagePropertyOptions = { index: 0, defaultValue: '9999' }
  imageSourceObj.getImageProperty("BitsPerSample", property, (error: BusinessError, data: string) => {
    if (error) {
      console.error('Failed to get the value of the specified attribute key of the image.');
    } else {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }
  })
}
```

## modifyImageProperty<sup>(deprecated)</sup>

modifyImageProperty(key: string, value: string): Promise\<void>

Modifies the value of an image property by the specified key. This API uses a promise to return the result asynchronously.

This API supports only JPEG, PNG, HEIF<sup>12+</sup>, and WEBP<sup>23+</sup> files (support varies by hardware device), and the file must contain Exif information.

> **NOTE**
>
> - Calling modifyImageProperty to modify a property changes the byte length of the property. Calling modifyImageProperty on an ImageSource created from a buffer causes the buffer content to be overwritten. Currently, an ImageSource created from a buffer does not support this API. Use an ImageSource created from an fd or a path instead.
>
> - This API is supported since API version 9 and deprecated since API version 11. You are advised to use [modifyImageProperty](#modifyimageproperty11) instead.
> - When calling modifyImageProperty to modify an Exif field, ensure that the corresponding image file has write permission. Otherwise, the field modification fails.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name  | Type   | Mandatory | Description         |
| ----- | ------ | --------- | ------------------- |
| key   | string | Yes       | Image property name. |
| value | string | Yes       | Attribute value.     |

**Return value**

| Type           | Description                        |
| -------------- | ---------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.modifyImageProperty("ImageWidth", "120").then(() => {
    imageSourceObj.getImageProperty("ImageWidth").then((width: string) => {
      console.info(`ImageWidth is :${width}`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get the Image Width, error.code ${error.code}, error.message ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to modify the Image Width, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## modifyImageProperty<sup>(deprecated)</sup>

modifyImageProperty(key: string, value: string, callback: AsyncCallback\<void>): void

Modifies the value of an image property by the specified key. This API uses an asynchronous callback to return the result.

Only JPEG, PNG, HEIF<sup>12+</sup>, and WEBP<sup>23+</sup> files (support varies by hardware device) that contain Exif information are supported.

> **NOTE**
>
> - Calling **modifyImageProperty** to modify a property changes the byte length of the property. Calling **modifyImageProperty** on an **ImageSource** created from a buffer causes the buffer content to be overwritten. Currently, an **ImageSource** created from a buffer does not support this API. Use an **ImageSource** created from an fd or a path instead.
>
> - This API is supported since API version 9 and deprecated since API version 11. You are advised to use [modifyImageProperty](#modifyimageproperty11) instead.
> - When calling **modifyImageProperty** to modify an Exif field, ensure that the corresponding image file has write permission. Otherwise, the field modification fails.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name     | Type                | Mandatory | Description                           |
| -------- | ------------------- | --------- | ------------------------------------- |
| key      | string              | Yes       | Name of the image property.           |
| value    | string              | Yes       | Attribute value.                       |
| callback | AsyncCallback\<void> | Yes       | Callback function. If the image property value is modified successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.modifyImageProperty("ImageWidth", "120", (err: BusinessError) => {
    if (err) {
      console.error(`Failed to modify the Image Width.code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('Succeeded in modifying the Image Width.');
    }
  })
}
```
