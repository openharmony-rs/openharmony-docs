# PhotoAsset

PhotoAsset provides APIs for encapsulating file asset attributes.

**Since:** 10

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cancelPhotoRequest

```TypeScript
cancelPhotoRequest(requestId: string): void
```

Cancels a task for obtaining media thumbnails.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestId | string | Yes | ID of the task to cancel. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## commitEditedAsset

```TypeScript
commitEditedAsset(editData: string, uri: string, callback: AsyncCallback<void>): void
```

Commits the edited image or video asset. This API uses an asynchronous callback to return the result.

The edited file is transferred to the media library based on the URI, which is **FileUri** of the edited file in the application sandbox directory. For details, see [File URI](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fileuri.md).

> **NOTE:** 
> 
> The commit operation overwrites the previous edited data.

**Since:** 11

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editData | string | Yes | New data to commit. |
| uri | string | Yes | URI of the committed image or video in the application sandbox. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## commitEditedAsset

```TypeScript
commitEditedAsset(editData: string, uri: string): Promise<void>
```

Commits the edited image or video asset. This API uses a promise to return the result.

The edited file is transferred to the media library based on the URI, which is **FileUri** of the edited file in the application sandbox directory. For details, see [File URI](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fileuri.md).

> **NOTE:** 
> 
> The commit operation overwrites the previous edited data.

**Since:** 11

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| editData | string | Yes | New data to commit. |
| uri | string | Yes | URI of the committed image or video in the application sandbox. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

See [commitEditedAsset](#commiteditedasset)

## convertImageFormat

```TypeScript
convertImageFormat(title: string, imageFormat: SupportedImageFormat): Promise<PhotoAsset>
```

Duplicates an image within the same album (either user-created or application-specific) and converts it to the specified format. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| title | string | Yes | Title of the new image. |
| imageFormat | [SupportedImageFormat](arkts-medialibrary-photoaccesshelper-supportedimageformat-e-sys.md) | Yes | Format of the new image. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Promise used to return the PhotoAsset instance representing the new image file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameters validate failed, possible causes:<br>1. The original file does not exist locally in PhotoAsset; <br>2. The original file format is not within the supported range; <br>3. The original file is a temporary file or is being edited; <br>4. The title is the same with an image in the same album; <br>5. PhotoAsset is a photo in the trash or a hidden photo; <br>6. The title does not meet the parameter specifications. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error.It is recommended to retry and check the logs.Possible causes:<br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('convertImageFormatDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAsset = await fetchResult.getFirstObject();
  try {
    let newPhotoAsset = await photoAsset.convertImageFormat('test', photoAccessHelper.SupportedImageFormat.AVFILE_FORMAT_JPG);
    console.error(`convertImageFormat success.`);
  } catch (err) {
    console.error(`convertImageFormat failed. error: ${err.code}, ${err.message}`);
  }
}
```

## createTemporaryCompatibleDuplicate

```TypeScript
createTemporaryCompatibleDuplicate(): Promise<void>
```

Creates a JPEG-compatible copy for a third-party application that does not support HEIF/HEIC image encoding. This API uses a promise to return the result.

**Since:** 21

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameters validate failed, possible causes:<br>1. The original file does not exist locally in PhotoAsset; <br>2. The original file format is not within the supported range; <br>3. The original file is a temporary file or is being edited; |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error.It is recommended to retry and check the logs.Possible causes:<br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('createTemporaryCompatibleDuplicatePromiseDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    await photoAsset.createTemporaryCompatibleDuplicate();
  } catch (err) {
    console.error(`createTemporaryCompatibleDuplicatePromiseDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getAnalysisData

```TypeScript
getAnalysisData(analysisType: AnalysisType): Promise<string>
```

Obtains analysis data. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| analysisType | [AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md) | Yes | Smart analysis type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns analysis info into a json string |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## getEditData

```TypeScript
getEditData(): Promise<MediaAssetEditData>
```

Obtains the edited data of this asset. This API uses a promise to return the result.

If the asset has never been edited, an empty string is returned.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[MediaAssetEditData](arkts-medialibrary-photoaccesshelper-mediaasseteditdata-c-sys.md)&gt; | Promise used to return the edited asset data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## getExif

```TypeScript
getExif(callback: AsyncCallback<string>): void
```

Obtains the Exif data from a JPG image and returns a JSON string. This API uses an asynchronous callback to return the result.

The Exif data obtained are provided by the [image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) module. For details about the Exif data, see [image.PropertyKey](../../apis-image-kit/arkts-apis/arkts-image-image-propertykey-e.md).

> **NOTE:** 
> 
> This API returns a JSON string consisting of Exif tags. The complete Exif data consists of **all_exif** and
> [PhotoKeys.USER_COMMENT](arkts-medialibrary-photoaccesshelper-photokeys-e.md). These two fields must be passed in via
> [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md).fetchColumns.

**Since:** 10

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the Exif data, in JSON strings. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## getExif

```TypeScript
getExif(): Promise<string>
```

Obtains the Exif data from a JPG image and returns a JSON string. This API uses a promise to return the result.

The Exif data obtained are provided by the [image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) module. For details about the Exif data, see [image.PropertyKey](../../apis-image-kit/arkts-apis/arkts-image-image-propertykey-e.md).

> **NOTE:** 
> 
> This API returns a JSON string consisting of Exif tags. The complete Exif data consists of **all_exif** and
> [PhotoKeys.USER_COMMENT](arkts-medialibrary-photoaccesshelper-photokeys-e.md). These two fields must be passed in via
> [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md).fetchColumns.

**Since:** 10

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the Exif data, in JSON strings. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

See [getExif](#getexif)

## getKeyFrameThumbnail

```TypeScript
getKeyFrameThumbnail(beginFrameTimeMs: number, type: ThumbnailType): Promise<image.PixelMap>
```

Obtains the thumbnail of the specified type for the key frame. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| beginFrameTimeMs | number | Yes | Time of the start frame, in ms. The value **0** indicates the cover frame. |
| type | [ThumbnailType](arkts-medialibrary-photoaccesshelper-thumbnailtype-e-sys.md) | Yes | Type of the thumbnail. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the PixelMap of the thumbnail obtained. The cover frame is returned by default if no thumbnail is obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## getReadOnlyFdWithCached

```TypeScript
getReadOnlyFdWithCached(): Promise<number>
```

Open the file and cache it in the gallery sandbox when streaming video from the cloud.

**Since:** 26.1.0

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the file fd. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Ensure the permission ohos.permission.READ_IMAGEVIDEO is declared in your module. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | Scene parameters validate failed, possible causes: The image and video files corresponding to the photoasset do not exist. Check if the photoasset is valid and the files exist in the gallery. |
| 23800302 | Failed to open the file. Possible causes: 1. Unable to access cloud images due to network connectivity issues; 2. File system malfunction. Please check your network connection and try again. |

## getThumbnailData

```TypeScript
getThumbnailData(type: ThumbnailType): Promise<ArrayBuffer>
```

Obtains the ArrayBuffer of a file thumbnail by specifying its type. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ThumbnailType](arkts-medialibrary-photoaccesshelper-thumbnailtype-e-sys.md) | Yes | Type of the thumbnail. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the ArrayBuffer of the thumbnail. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getThumbnailDataDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnailData(photoAccessHelper.ThumbnailType.LCD).then((buffer: ArrayBuffer) => {
    console.info('getThumbnailData successful, buffer byteLength = ${buffer.byteLength}');
  }).catch((err: BusinessError) => {
    console.error(`getThumbnailData fail with error: ${err.code}, ${err.message}`);
  });
}
```

## isEdited

```TypeScript
isEdited(callback: AsyncCallback<boolean>): void
```

Checks whether this image or video asset is edited. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result indicating whether the image or video asset is edited. **true** if edited, **false** otherwise. The default value is **false**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## isEdited

```TypeScript
isEdited(): Promise<boolean>
```

Checks whether this image or video asset is edited. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result indicating whether the image or video asset is edited. **true** if edited, **false** otherwise. The default value is **false**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

**Examples**

See [isEdited](#isedited)

## open

```TypeScript
open(mode: string, callback: AsyncCallback<number>): void
```

Opens this file asset. This API uses an asynchronous callback to return the result.

The returned FD must be closed when it is not required.

> **NOTE:** 
> 
> This API is supported since API version 10 and deprecated since API version 11. For security purposes, the API
> for obtaining the media file handle is no longer provided.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** open

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | string | Yes | Mode for opening the file, which can be **'r'** (read-only), **'w'** (write-only), or **'rw'** (read/write). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the file descriptor (FD) of the file opened. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## open

```TypeScript
open(mode: string): Promise<number>
```

Opens this file asset. This API uses a promise to return the result.

The returned FD must be closed when it is not required.

> **NOTE:** 
> 
> This API is supported since API version 10 and deprecated since API version 11. For security purposes, the API
> for obtaining the media file handle is no longer provided.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** open

**Required permissions:** ohos.permission.READ_IMAGEVIDEO or ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | string | Yes | Mode for opening the file, which can be **'r'** (read-only), **'w'** (write-only), or **'rw'** (read/write). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the FD of the file opened. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

See [open](#open)

## requestEditData

```TypeScript
requestEditData(callback: AsyncCallback<string>): void
```

Obtains the edit data of this image or video asset. This API uses an asynchronous callback to return the result.

If the asset has never been edited, an empty string is returned.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the edit data obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## requestEditData

```TypeScript
requestEditData(): Promise<string>
```

Obtains the edit data of this image or video asset. This API uses a promise to return the result.

If the asset has never been edited, an empty string is returned.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the edit data obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

See [requestEditData](#requesteditdata)

## requestPhoto

```TypeScript
requestPhoto(callback: AsyncCallback<image.PixelMap>): string
```

Obtains the quick thumbnail and quality thumbnail of this asset. This API uses an asynchronous callback to return the result.

The size of a quick thumbnail is 128 x 128, and the size of a quality thumbnail is 256 x 256. After this API is called, the callback will be invoked twice to return a quick thumbnail and a quality thumbnail in sequence.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback invoked twice to return the quick and quality thumbnails obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| string | ID of the task for obtaining thumbnails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## requestPhoto

```TypeScript
requestPhoto(options: RequestPhotoOptions, callback: AsyncCallback<image.PixelMap>): string
```

Obtains the thumbnails of an asset based on the specified options. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RequestPhotoOptions](arkts-medialibrary-photoaccesshelper-requestphotooptions-i-sys.md) | Yes | Options for obtaining the asset thumbnail. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the thumbnails obtained. The callback may be invoked more than once, depending on **options**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | ID of the task for obtaining thumbnails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

See [requestPhoto](#requestphoto)

## requestSource

```TypeScript
requestSource(callback: AsyncCallback<number>): void
```

Opens the source file and returns the FD. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the FD. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## requestSource

```TypeScript
requestSource(): Promise<number>
```

Opens the source file and returns the FD. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the FD. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

See [requestSource](#requestsource)

## revertToOriginal

```TypeScript
revertToOriginal(callback: AsyncCallback<void>): void
```

Reverts to the state of the file before being edited. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API deletes the edited data and edited image or video asset, and the deleted data cannot be restored.
> Exercise caution when using this API.

**Since:** 11

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## revertToOriginal

```TypeScript
revertToOriginal(): Promise<void>
```

Reverts to the state of the file before being edited. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API deletes the edited data and edited image or video asset, and the deleted data cannot be restored.
> Exercise caution when using this API.

**Since:** 11

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

**Examples**

See [revertToOriginal](#reverttooriginal)

## setFavorite

```TypeScript
setFavorite(favoriteState: boolean, callback: AsyncCallback<void>): void
```

Favorites or unfavorites this file asset. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setFavorite](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#setfavorite)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| favoriteState | boolean | Yes | Whether to favorite the file asset. **true** to favorite, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setFavorite

```TypeScript
setFavorite(favoriteState: boolean): Promise<void>
```

Favorites or unfavorites this file asset. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setFavorite](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#setfavorite)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| favoriteState | boolean | Yes | Whether to favorite the file asset. **true** to favorite, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setHidden

```TypeScript
setHidden(hiddenState: boolean, callback: AsyncCallback<void>): void
```

Sets this file asset to the hidden state. This API uses an asynchronous callback to return the result.

Private files are stored in the private album. After obtaining private files from the private album, users can set **hiddenState** to **false** to remove them from the private album.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setHidden](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#sethidden)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hiddenState | boolean | Yes | Whether to set a file to hidden state. **true** to hide, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setHidden

```TypeScript
setHidden(hiddenState: boolean): Promise<void>
```

Sets this file asset to the hidden state. This API uses a promise to return the result.

Private files are stored in the private album. After obtaining private files from the private album, users can set **hiddenState** to **false** to remove them from the private album.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setHidden](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#sethidden)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hiddenState | boolean | Yes | Whether to set a file to hidden state. **true** to hide, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setPending

```TypeScript
setPending(pendingState: boolean, callback: AsyncCallback<void>): void
```

Sets the pending state for this image or video asset. This API uses an asynchronous callback to return the result.

The pending state can be removed only through **setPending(false)**. You can use **photoAsset.get(photoAccessHelper.PhotoKeys.PENDING)** to check whether the asset state is pending. If the asset is in pending state, **true** is returned. Otherwise, **false** is returned.

> **NOTE:** 
> 
> **setPending** can be used only during the file creation process. Once the FD is closed, **setPending(true)**
> cannot be used to set the pending state for the file.

**Since:** 11

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pendingState | boolean | Yes | Whether to set the file to pending state. **true** to pend, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setPending

```TypeScript
setPending(pendingState: boolean): Promise<void>
```

Sets the pending state for this image or video asset. This API uses a promise to return the result.

The pending state can be removed only through **setPending(false)**. You can use **photoAsset.get(photoAccessHelper.PhotoKeys.PENDING)** to check whether the asset state is pending. If the asset is in pending state, **true** is returned. Otherwise, **false** is returned.

> **NOTE:** 
> 
> **setPending** can be used only during the file creation process. Once the FD is closed, **setPending(true)**
> cannot be used to set the pending state for the file.

**Since:** 11

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pendingState | boolean | Yes | Whether to set the file to pending state. **true** to pend, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

See [setPending](#setpending)

## setUserComment

```TypeScript
setUserComment(userComment: string, callback: AsyncCallback<void>): void
```

Sets user comment information of an image or video. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setUserComment](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setusercomment)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userComment | string | Yes | User comment information to set, which cannot exceed 420 characters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setUserComment

```TypeScript
setUserComment(userComment: string): Promise<void>
```

Sets user comment information of an image or video. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 11

**Substitutes:** [setUserComment](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setusercomment)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userComment | string | Yes | User comment information to set, which cannot exceed 420 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```
