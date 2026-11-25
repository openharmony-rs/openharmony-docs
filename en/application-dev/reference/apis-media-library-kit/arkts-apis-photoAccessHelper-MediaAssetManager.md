# Class (MediaAssetManager)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d036437fca9f1387f05ed5f1104d3980c50e5643 translatedAt=2026-11-03T07:05:45.250Z pushedAt=2026-11-04T03:11:19.961Z nl=1 -->

The MediaAssetManager class is used for manipulating the read and write operations of media assets.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this class are supported since API version 11.

## Modules to Import

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## requestImage<sup>11+</sup>

static requestImage(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler&lt;image.ImageSource&gt;): Promise&lt;string&gt;

Requests an image. This API uses a promise to return the result.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

- When this API is called in picker mode to request image resources, the **ohos.permission.READ_IMAGEVIDEO** permission is not required. For details, see [Obtaining an Image or Video by URI](../../media/medialibrary/photoAccessHelper-photoviewpicker.md#obtaining-an-image-or-video-by-uri).
- For images saved to the media library by this application, the application can access them without the **ohos.permission.READ_IMAGEVIDEO** permission.

**Parameters**

| Name           | Type                                                                                                       | Mandatory| Description                     |
|----------------|-----------------------------------------------------------------------------------------------------------| ---- | ------------------------- |
| context        | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                                                           | Yes  | Context of the ability instance.|
| asset         | [PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)                                                                                | Yes  | Image to request.|
| requestOptions | [RequestOptions](arkts-apis-photoAccessHelper-i.md#requestoptions11)                                                                        | Yes  | Options for requesting the image.|
| dataHandler    | [MediaAssetDataHandler](arkts-apis-photoAccessHelper-MediaAssetDataHandler.md)&lt;[image.ImageSource](../apis-image-kit/arkts-apis-image-ImageSource.md)&gt; | Yes  | Media asset handler, which invokes a callback to return the image when the requested image is ready.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise\<string> | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest12) to cancel a request.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Parameter types or count are invalid, please check if asset is PhotoAsset, requestOptions is RequestOptions, dataHandler is a valid MediaAssetDataHandler object.<br>2. User file service initialization failed, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please check if the context is valid and retry.<br>3. Failed to initialize the dataHandler callback, possible causes: <br>(1) Memory insufficient; <br>(2) IPC timeout. Please retry. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
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
    if (err) {
      console.error(`Failed to get assets. Code: ${err.code}, message: ${err.message}`);
      return;
    }
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

## requestImageData<sup>11+</sup>

static requestImageData(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler&lt;ArrayBuffer&gt;): Promise&lt;string&gt;

Requests image asset data based on different strategy modes. This is applicable to scenarios such as image upload and filter processing that require obtaining raw data. This API uses a promise to return the result.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

- When this API is called in picker mode to request image resources, the **ohos.permission.READ_IMAGEVIDEO** permission is not required. For details, see [Obtaining an Image or Video by URI](../../media/medialibrary/photoAccessHelper-photoviewpicker.md#obtaining-an-image-or-video-by-uri).
- For images saved to the media library by this application, the application can access them without the **ohos.permission.READ_IMAGEVIDEO** permission.

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                      | Yes  | Context of the ability instance.|
| asset | [PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)                                            | Yes  | Image to request.|
| requestOptions  | [RequestOptions](arkts-apis-photoAccessHelper-i.md#requestoptions11)                                  | Yes  | Options for requesting the image.|
| dataHandler  | [MediaAssetDataHandler](arkts-apis-photoAccessHelper-MediaAssetDataHandler.md)&lt;ArrayBuffer&gt; | Yes   | Media asset processor, which triggers the callback when the request is complete.          |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise\<string> | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest12) to cancel a request.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Parameter types or count are invalid, please check if asset is PhotoAsset, requestOptions is RequestOptions, dataHandler is a valid MediaAssetDataHandler object.<br>2. User file service initialization failed, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please check if the context is valid and retry.<br>3. Failed to initialize the dataHandler callback, possible causes: <br>(1) Memory insufficient; <br>(2) IPC timeout. Please retry. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
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
    if (err) {
      console.error(`Failed to get assets. Code: ${err.code}, message: ${err.message}`);
      return;
    }
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

## requestMovingPhoto<sup>12+</sup>

static requestMovingPhoto(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: MediaAssetDataHandler&lt;MovingPhoto&gt;): Promise&lt;string&gt;

Requests a dynamic photo object based on different strategy modes. This is applicable to viewing dynamic photos. This API uses a promise to return the result.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

- When this API is called in picker mode to request moving photos, the **ohos.permission.READ_IMAGEVIDEO** permission is not required. For details, see [Obtaining an Image or Video by URI](../../media/medialibrary/photoAccessHelper-photoviewpicker.md#obtaining-an-image-or-video-by-uri).
- For moving photos saved to the media library by this application, the application can access them without the **ohos.permission.READ_IMAGEVIDEO** permission.

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                      | Yes  | Context of the ability instance.|
| asset | [PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)                                            | Yes  | Image to request.|
| requestOptions  | [RequestOptions](arkts-apis-photoAccessHelper-i.md#requestoptions11)                                  | Yes  | Options for requesting the image.|       
| dataHandler  | [MediaAssetDataHandler](arkts-apis-photoAccessHelper-MediaAssetDataHandler.md)&lt;[MovingPhoto](arkts-apis-photoAccessHelper-MovingPhoto.md)&gt; | Yes  | Media asset handler, which invokes a callback to return the image when the requested image is ready.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise\<string> | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest12) to cancel a request.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. Possible causes:<br>1. The hardware does not support the capability.<br>2. The chip does not support the capability.<br>3. A dependent service feature is not supported. <br> Applicable version: 18+ |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Parameter parsing failed, please check the number and types of parameters.<br>2. User file service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is valid and retry.<br>3. Failed to initialize the dataHandler callback, possible causes: <br>(1) Memory insufficient; <br>(2) IPC timeout. Please retry. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
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
  if (!assetResult) {
    console.error('Failed to get assets');
    return;
  }
  let asset: photoAccessHelper.PhotoAsset = await assetResult.getFirstObject();
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.FAST_MODE,
  }
  const handler = new MovingPhotoHandler();
  try {
    let requestId: string = await photoAccessHelper.MediaAssetManager.requestMovingPhoto(context, asset, requestOptions, handler);
    console.info("moving photo requested successfully, requestId: " + requestId);
  } catch (err) {
    console.error(`Failed to request moving photo. Code: ${err.code}, message: ${err.message}`);
  }
}

```

## requestVideoFile<sup>12+</sup>

static requestVideoFile(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, fileUri: string, dataHandler: MediaAssetDataHandler&lt;boolean&gt;): Promise&lt;string&gt;

Requests video asset data to a sandbox path based on different strategy modes. This is applicable to scenarios such as uploading videos to a server or playing them in a player. This API uses a promise to return the result.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

- When this API is called in picker mode to request video resources and save them to the specified sandbox directory, the **ohos.permission.READ_IMAGEVIDEO** permission is not required. For details, see [Obtaining an Image or Video by URI](../../media/medialibrary/photoAccessHelper-photoviewpicker.md#obtaining-an-image-or-video-by-uri).
- For video resources saved to the media library by this application, the application can access them without the **ohos.permission.READ_IMAGEVIDEO** permission.

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                      | Yes  | Context of the ability instance.|
| asset | [PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)                                            | Yes  | Image to request.|
| requestOptions  | [RequestOptions](arkts-apis-photoAccessHelper-i.md#requestoptions11)                                  | Yes  | Options for requesting the video asset.|
| fileUri| string                                                              | Yes| URI of the sandbox directory, to which the requested video asset is to be saved. Example: **'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.mp4'**.|
| dataHandler  | [MediaAssetDataHandler](arkts-apis-photoAccessHelper-MediaAssetDataHandler.md)&lt;boolean&gt; | Yes  | Media asset handler. When the requested video is written to the specified directory, a callback is triggered.<br>If the video is successfully written, **true** is returned. Otherwise, **false** is returned.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise\<string> | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest12) to cancel a request.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801 | Capability not supported. Possible causes:<br>1. The hardware does not support the capability.<br>2. The chip does not support the capability.<br>3. A dependent service feature is not supported. <br> Applicable version: 15+ |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Parameter parsing failed, please check the number and types of parameters.<br>2. The dataHandler parameter must be a valid object.<br>3. User file service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is valid and retry.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
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
    if (err) {
      console.error(`Failed to get assets. Code: ${err.code}, message: ${err.message}`);
      return;
    }
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset === undefined) {
        console.error('photoAsset is undefined');
        return;
      }
      await photoAccessHelper.MediaAssetManager.requestVideoFile(context, photoAsset, requestOptions, fileUri, handler);
      console.info('requestVideoFile successfully');
  });
}
```

## cancelRequest<sup>12+</sup>

static cancelRequest(context: Context, requestId: string): Promise\<void>

Cancels a request for the asset, the callback of which has not been triggered yet. This API uses a promise to return the result.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                      | Yes  | Context of the ability instance.|
| requestId | string     | Yes   | ID of the request to cancel, which is a valid request ID returned by APIs such as requestImage. After this parameter is passed in, the corresponding request operation is canceled, the allocated resources are released, and the callback corresponding to the request will not be triggered. |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. User file service initialization failed, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please check if the context is valid and retry.<br>2. The requestId parameter is invalid, please check if it is a valid non-empty string returned by a prior request. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(context: Context) {
  try {
    let requestId: string = 'xxx-xxx'; // A valid requestId returned by APIs such as requestImage() must be used.
    await photoAccessHelper.MediaAssetManager.cancelRequest(context, requestId);
    console.info("request cancelled successfully");
  } catch (err) {
    console.error(`Failed to cancel request. Code: ${err.code}, message: ${err.message}`);
  }
}

```

## loadMovingPhoto<sup>12+</sup>

static loadMovingPhoto(context: Context, imageFileUri: string, videoFileUri: string): Promise\<MovingPhoto>

Loads a moving photo in the application sandbox. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md)   | Yes  | AbilityContext or UIExtensionContext instance.|
| imageFileUri | string     | Yes   | Image URI of the dynamic photo in the application sandbox, used to create the image component of the dynamic photo object.<br>Example: 'file://com.example.temptest/data/storage/el2/base/haps/ImageFile.jpg' |
| videoFileUri | string     | Yes   | Video URI of the dynamic photo in the application sandbox, used to create the video component of the dynamic photo object.<br>Example: 'file://com.example.temptest/data/storage/el2/base/haps/VideoFile.mp4' |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise\<MovingPhoto> | Promise used to return the [MovingPhoto](arkts-apis-photoAccessHelper-MovingPhoto.md) instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Failed to parse parameters. Please check the number and types of parameters.<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

```ts
async function example(context: Context) {
  try {
    let imageFileUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/ImageFile.jpg'; // Image URI of the moving photo in the application sandbox.
    let videoFileUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/VideoFile.mp4'; // Video URI of the moving photo in the application sandbox.
    let movingPhoto: photoAccessHelper.MovingPhoto = await photoAccessHelper.MediaAssetManager.loadMovingPhoto(context, imageFileUri, videoFileUri);
  } catch (err) {
    console.error(`Failed to load moving photo. Code: ${err.code}, message: ${err.message}`);
  }
}

```

## quickRequestImage<sup>13+</sup>

static quickRequestImage(context: Context, asset: PhotoAsset, requestOptions: RequestOptions, dataHandler: QuickImageDataHandler&lt;image.Picture&gt;): Promise&lt;string&gt;

Quickly requests image assets based on different strategy modes. This is applicable to scenarios with high loading speed requirements, such as loading thumbnails in an image list. This API uses a promise to return the result.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

- When this API is called in picker mode to request image resources, the **ohos.permission.READ_IMAGEVIDEO** permission is not required. For details, see [Obtaining an Image or Video by URI](../../media/medialibrary/photoAccessHelper-photoviewpicker.md#obtaining-an-image-or-video-by-uri).

**Parameters**

| Name           | Type                                                                                                       | Mandatory| Description                     |
|----------------|-----------------------------------------------------------------------------------------------------------| ---- | ------------------------- |
| context        | [Context](../apis-ability-kit/js-apis-inner-application-context.md)                                                           | Yes  | Context of the ability instance.|
| asset         | [PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)                                                                                | Yes  | Image to request.|
| requestOptions | [RequestOptions](arkts-apis-photoAccessHelper-i.md#requestoptions11)                                                                        | Yes  | Options for requesting the image.|
| dataHandler    | [QuickImageDataHandler](arkts-apis-photoAccessHelper-QuickImageDataHandler.md)&lt;[image.Picture](../apis-image-kit/arkts-apis-image-Picture.md)&gt; | Yes  | Media asset handler, which invokes a callback to return the image when the requested image is ready.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise\<string> | Promise used to return the request ID, which can be used in [cancelRequest](#cancelrequest12) to cancel a request.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>User file client initialization failed, possible causes: 1. Database exception; 2. IPC timeout. Please retry. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
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
    if (err) {
      console.error(`Failed to get assets. Code: ${err.code}, message: ${err.message}`);
      return;
    }
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset === undefined) {
        console.error('photoAsset is undefined');
        return;
      }
      await photoAccessHelper.MediaAssetManager.quickRequestImage(context, photoAsset, requestOptions, handler);
      console.info('quickRequestImage successfully');
  });
}
```

## requestCompositeAuxiliaryImageData

static requestCompositeAuxiliaryImageData(context: Context, asset: PhotoAsset, dataHandler: MediaAssetDataHandler&lt;ArrayBuffer&gt;): Promise&lt;string&gt;

Requests the data of the auxiliary image in a composite image.

AI enhancement additionally generates an image, which together with the original image forms a composite image. The additionally generated image in the composite image is used for display by default, and the other original image is called the auxiliary image.

**Since:** 26.0.1

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name | Type | Mandatory | Description |
|----------------|-----------------------------------------------------------------------------------------------------------| ---- | ------------------------- |
| context        | [Context](../apis-ability-kit/js-apis-inner-application-context.md#context)                                                           | Yes   | Context of the Ability instance. |
| asset         | [PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)                                                                                | Yes   | Asset to be requested. |
| dataHandler    | [MediaAssetDataHandler](arkts-apis-photoAccessHelper-MediaAssetDataHandler.md)&lt;ArrayBuffer&gt; | Yes   | Callback function. The ArrayBuffer contains the complete data of the auxiliary image in the composite image. |

**Return value**

| Type | Description |
| --------------------------------------- | ----------------- |
| Promise\<string> | Promise object that returns the request ID, which can be used to cancel the request through [cancelRequest](#cancelrequest12). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID | Error Message |
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 23800151      | Scene parameters validate failed, possible causes: 1. The asset is not a cloud-enhanced composite photo asset.        |
| 23800301      | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1. The database is corrupted.<br>2. The file system is abnormal.<br>3. The IPC request timed out.         |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

class MediaHandler implements photoAccessHelper.MediaAssetDataHandler<ArrayBuffer> {
  onDataPrepared(data: ArrayBuffer) {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    console.info('Succeeded in preparing composite auxiliary image data');
  }
}

async function example(context: Context) {
  console.info('requestCompositeAuxiliaryImageData');
  // Construct the query conditions to obtain the composite image (cloud-enhanced) photo asset in the media library.
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  // Create a data processor to receive the auxiliary image data in the composite image.
  const handler = new MediaHandler();
  let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
    if (err) {
      console.error(`Failed to get assets. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting assets');
    // Obtain the first asset in the query result.
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (photoAsset === undefined) {
      console.error('photoAsset is undefined');
      return;
    }
    try {
      // Request the auxiliary image data in the composite image. The returned requestId can be used to cancel the request through the cancelRequest API.
      let requestId: string = await photoAccessHelper.MediaAssetManager.requestCompositeAuxiliaryImageData(context, photoAsset, handler);
      console.info('Succeeded in requesting composite auxiliary image data, requestId: ' + requestId);
    } catch (err) {
      console.error(`failed to requestCompositeAuxiliaryImageData, error code is ${err.code}, message is ${err.message}`);
    }
  });
}
```