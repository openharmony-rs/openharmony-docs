# MediaAssetManager

```TypeScript
class MediaAssetManager
```

The MediaAssetManager class is used for manipulating the read and write operations of media assets.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cancelRequest

```TypeScript
static cancelRequest(context: Context, requestId: string): Promise<void>
```

Cancels a request for the asset, the callback of which has not been triggered yet. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| requestId | string | Yes | ID of the request to cancel. It is a valid request ID returned by **requestImage**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(context: Context) {
  try {
    let requestId: string = 'xxx-xxx'; // A valid requestId returned by APIs such as requestImage() must be used.
    await photoAccessHelper.MediaAssetManager.cancelRequest(context, requestId);
    console.info("request cancelled successfully");
  } catch (err) {
    console.error(`cancelRequest failed with error: ${err.code}, ${err.message}`);
  }
}
```

## loadMovingPhoto

```TypeScript
static loadMovingPhoto(
      context: Context,
      imageFileUri: string,
      videoFileUri: string
    ): Promise<MovingPhoto>
```

Loads a moving photo in the application sandbox. This API uses a promise to return the result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | AbilityContext or UIExtensionContext instance. |
| imageFileUri | string | Yes | URI of the image file of the moving photo in the application sandbox.<br>Example: **'file://com.example.temptest/data/storage/el2/base/haps/ImageFile.jpg'**. |
| videoFileUri | string | Yes | URI of the video file of the moving photo in the application sandbox.<br>Example: **'file://com.example.temptest/data/storage/el2/base/haps/VideoFile.mp4'**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md)&gt; | Promise used to return the [MovingPhoto](arkts-medialibrary-file-photoaccesshelper.md) instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**Examples**

```TypeScript
async function example(context: Context) {
  try {
    let imageFileUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/ImageFile.jpg'; // Image URI of the moving photo in the application sandbox.
    let videoFileUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/VideoFile.mp4'; // Video URI of the moving photo in the application sandbox.
    let movingPhoto: photoAccessHelper.MovingPhoto = await photoAccessHelper.MediaAssetManager.loadMovingPhoto(context, imageFileUri, videoFileUri);
  } catch (err) {
    console.error(`loadMovingPhoto failed with error: ${err.code}, ${err.message}`);
  }
}
```

## quickRequestImage

```TypeScript
static quickRequestImage(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      dataHandler: QuickImageDataHandler<image.Picture>
    ): Promise<string>
```

Requests an image quickly. This API uses a promise to return the result.

**Since:** 13

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | Yes | Image to request. |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | Yes | Options for requesting the image. |
| dataHandler | [QuickImageDataHandler](arkts-medialibrary-photoaccesshelper-quickimagedatahandler-i.md)&lt;[image.Picture](../../apis-image-kit/arkts-apis/arkts-image-image-picture-i.md)&gt; | Yes | Media asset handler, which invokes a callback to return the image when the requested image is ready. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest) to cancel a request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

class MediaHandler implements photoAccessHelper.QuickImageDataHandler<image.Picture> {
  onDataPrepared(data: image.Picture, imageSource: image.ImageSource, map: Map<string, string>) {
    console.info('on image data prepared');
  }
}

async function example(context: Context) {
  console.info('quickRequestImage');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.HIGH_QUALITY_MODE,
  }
  const handler = new MediaHandler();
  let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      await photoAccessHelper.MediaAssetManager.quickRequestImage(context, photoAsset, requestOptions, handler);
      console.info('quickRequestImage successfully');
  });
}
```

## requestImage

```TypeScript
static requestImage(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      dataHandler: MediaAssetDataHandler<image.ImageSource>
    ): Promise<string>
```

Requests an image. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | Yes | Image to request. |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | Yes | Options for requesting the image. |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;[image.ImageSource](../../apis-image-kit/arkts-apis/arkts-image-image-imagesource-i.md)&gt; | Yes | Media asset handler, which invokes a callback to return the image when the requested image is ready. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest) to cancel a request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

class MediaHandler implements photoAccessHelper.MediaAssetDataHandler<image.ImageSource> {
  onDataPrepared(data: image.ImageSource) {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    console.info('on image data prepared');
  }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('requestImage');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.HIGH_QUALITY_MODE,
  }
  const handler = new MediaHandler();

  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
    console.info('fetchResult success');
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (photoAsset === undefined) {
      console.error('photoAsset is undefined');
      return;
    }
    await photoAccessHelper.MediaAssetManager.requestImage(context, photoAsset, requestOptions, handler);
    console.info('requestImage successfully');
  });
}
```

## requestImageData

```TypeScript
static requestImageData(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      dataHandler: MediaAssetDataHandler<ArrayBuffer>
    ): Promise<string>
```

Requests image data. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | Yes | Image to request. |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | Yes | Options for requesting the image. |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;ArrayBuffer&gt; | Yes | Media asset handler, which invokes a callback to return the image when the requested image is ready. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest) to cancel a request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

class MediaDataHandler implements photoAccessHelper.MediaAssetDataHandler<ArrayBuffer> {
  onDataPrepared(data: ArrayBuffer) {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    console.info('on image data prepared');
  }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('requestImageData');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.HIGH_QUALITY_MODE,
  }
  const handler = new MediaDataHandler();

  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset === undefined) {
      console.error('requestImageData photoAsset is undefined');
      return;
    }
      await photoAccessHelper.MediaAssetManager.requestImageData(context, photoAsset, requestOptions, handler);
      console.info('requestImageData successfully');
  });
}
```

## requestMovingPhoto

```TypeScript
static requestMovingPhoto(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      dataHandler: MediaAssetDataHandler<MovingPhoto>
    ): Promise<string>
```

Requests a moving photo object, which can be used to request the asset data of the moving photo. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | Yes | Image to request. |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | Yes | Options for requesting the image. |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;[MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md)&gt; | Yes | Media asset handler, which invokes a callback to return the image when the requested image is ready. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest) to cancel a request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 18 and later |
| 14000011 | System inner fail |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

class MovingPhotoHandler implements photoAccessHelper.MediaAssetDataHandler<photoAccessHelper.MovingPhoto> {
  async onDataPrepared(movingPhoto: photoAccessHelper.MovingPhoto) {
    if (movingPhoto === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    console.info("moving photo acquired successfully, uri: " + movingPhoto.getUri());
  }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo(photoAccessHelper.PhotoKeys.PHOTO_SUBTYPE, photoAccessHelper.PhotoSubtype.MOVING_PHOTO);
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  // Ensure that there are moving photos in Gallery.
  let assetResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let asset: photoAccessHelper.PhotoAsset = await assetResult.getFirstObject();
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.FAST_MODE,
  }
  const handler = new MovingPhotoHandler();
  try {
    let requestId: string = await photoAccessHelper.MediaAssetManager.requestMovingPhoto(context, asset, requestOptions, handler);
    console.info("moving photo requested successfully, requestId: " + requestId);
  } catch (err) {
    console.error(`failed to request moving photo, error code is ${err.code}, message is ${err.message}`);
  }
}
```

## requestVideoFile

```TypeScript
static requestVideoFile(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      fileUri: string,
      dataHandler: MediaAssetDataHandler<boolean>
    ): Promise<string>
```

Requests a video and saves it to the specified sandbox directory. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | Yes | Image to request. |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | Yes | Options for requesting the video asset. |
| fileUri | string | Yes | URI of the sandbox directory, to which the requested video asset is to be saved. Example: **'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.mp4'**. |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;boolean&gt; | Yes | Media asset handler. When the requested video is written to the specified directory, a callback is triggered.<br>If the video is successfully written, **true** is returned. Otherwise, **false** is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest) to cancel a request. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported.<br>**Applicable version:** 15 and later |
| 14000011 | System inner fail. Possible causes:<br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**Examples**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

class MediaDataHandler implements photoAccessHelper.MediaAssetDataHandler<boolean> {
    onDataPrepared(data: boolean) {
        console.info('on video request status prepared');
    }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('requestVideoFile');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.HIGH_QUALITY_MODE,
  }
  const handler = new MediaDataHandler();
  let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.mp4';
  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      await photoAccessHelper.MediaAssetManager.requestVideoFile(context, photoAsset, requestOptions, fileUri, handler);
      console.info('requestVideoFile successfully');
  });
}
```
