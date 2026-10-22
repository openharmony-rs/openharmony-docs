# Interface (PhotoAccessHelper)

<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xuchangda; @yixiaoff-->
<!--Designer: @guxinggang; @liweilu1-->
<!--Tester: @wangbeibei; @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

The **PhotoAccessHelper** interface provides access management capabilities for image and video resources. It allows you to obtain, create, and delete media assets, manage albums, and listen for asset changes.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getAssets

getAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult&lt;PhotoAsset&gt;&gt;): void

Obtains image and video assets. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

 When this API is called in picker mode to query the image or video resource corresponding to a specified URI, the **ohos.permission.READ_IMAGEVIDEO** permission is not required. For details, see [Obtaining an Image or Video by URI](../../media/medialibrary/photoAccessHelper-photoviewpicker.md#obtaining-an-image-or-video-by-uri).

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| options  | [FetchOptions](arkts-apis-photoAccessHelper-i.md#fetchoptions)        | Yes  | Retrieval options.             |
| callback |  AsyncCallback&lt;[FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt;&gt; | Yes  | Callback used to return the image and video assets obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

In API version 13 and earlier versions, if the caller does not have the required permission, error code 13900012 is returned. Starting from API version 14, the same situation raises error code 201.

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. <br> Applicable versions: 12+ |
| 13900012     | Permission denied. <br> Applicable versions: 10 to 11        |
| 13900020 | Invalid parameter. Possible causes:<br>1. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs<br>2. The number of arguments is invalid.<br>3. The argument list is empty.<br>4. The object is not a valid instance.<br>5. PhotoAccessHelper object is not a valid instance obtained through the proper API.<br>6. The callback parameter type does not match, expected AsyncCallback.<br>7. Invalid fetchColumns: contains unknown column name. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The FetchOptions parameter is invalid, the predicates property is not a valid data predicates object.<br>2. The predicates in FetchOptions contain invalid content or operations, please check if the predicates are valid.<br>3. The fetchColumns in FetchOptions contain invalid column names, please refer to PhotoKeys for valid column names.<br>4. Database query failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please retry and check logs.<br>5. Query returned an empty result set. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };

  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
    if (err) {
      console.error(`fetchResult fail with error: ${err.code}, ${err.message}`);
      return;
    }
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset !== undefined) {
        console.info('photoAsset.displayName : ' + photoAsset.displayName);
      }
    } else {
      console.error(`fetchResult fail with error: ${err.code}, ${err.message}`);
    }
  });
}
```

## getAssets

getAssets(options: FetchOptions): Promise&lt;FetchResult&lt;PhotoAsset&gt;&gt;

Obtains image and video assets. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

 When this API is called in picker mode to query the image or video resource corresponding to a specified URI, the **ohos.permission.READ_IMAGEVIDEO** permission is not required. For details, see [Obtaining an Image or Video by URI](../../media/medialibrary/photoAccessHelper-photoviewpicker.md#obtaining-an-image-or-video-by-uri).

**Parameters**

| Name | Type               | Mandatory| Description            |
| ------- | ------------------- | ---- | ---------------- |
| options | [FetchOptions](arkts-apis-photoAccessHelper-i.md#fetchoptions)   | Yes  | Retrieval options.    |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt;&gt; | Promise used to return the image and video assets obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

In API version 13 and earlier versions, if the caller does not have the required permission, error code 13900012 is returned. Starting from API version 14, the same situation raises error code 201.

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API.<br> Applicable versions: 20+  |
| 13900012     | Permission denied. <br> Applicable versions: 10 to 19        |
| 13900020     | Invalid argument.         |
| 14000011       | System inner fail.         |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset !== undefined) {
        console.info('photoAsset.displayName :' + photoAsset.displayName);
      }
    }
  } catch (err) {
    console.error(`getAssets failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getBurstAssets<sup>12+</sup>

getBurstAssets(burstKey: string, options: FetchOptions): Promise&lt;FetchResult&lt;PhotoAsset&gt;&gt;

Obtains burst assets. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name | Type               | Mandatory| Description            |
| ------- | ------------------- | ---- | ---------------- |
| burstKey | string   | Yes  | Universally Unique Identifier (UUID) of a group of burst photos, that is, **BURST_KEY** of [PhotoKeys](arkts-apis-photoAccessHelper-e.md#photokeys). The string contains 36 bytes.|
| options | [FetchOptions](arkts-apis-photoAccessHelper-i.md#fetchoptions)   | Yes  | Retrieval options.    |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt;&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Failed to check predicates property.<br>2. Failed to get predicates property.<br>3. The object is not a valid instance.<br>4. The predicates parameter is invalid, not of predicates type.<br>5. Invalid predicate, please check the predicates in FetchOptions content or operation.<br>6. Failed to parse fetchColumns array.<br>7. Failed to create boolean result.<br>8. Sandbox query failed: internal error.<br>9. File operation failed.<br>10. Failed to parse arguments for getBurstAssets. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getBurstAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  // burstKey is a 36-bit UUID, which can be obtained from photoAccessHelper.PhotoKeys.
  let burstKey: string = "e719d696-09fa-44f8-8e9e-ec3f215aa62a";
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await 
      phAccessHelper.getBurstAssets(burstKey, fetchOptions);
    if (fetchResult !== undefined) {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset !== undefined) {
        console.info('photoAsset.displayName :' + photoAsset.displayName);
      }
    }
  } catch (err) {
    console.error(`getBurstAssets failed, error: ${err.code}, ${err.message}`);
  }
}
```

## createAsset

createAsset(photoType: PhotoType, extension: string, options: CreateOptions, callback: AsyncCallback&lt;string&gt;): void

Creates an image or video asset with the specified file type, file name extension, and options. This API uses an asynchronous callback to return the result.

If you do not have the **ohos.permission.WRITE_IMAGEVIDEO** permission, you can create a media asset by using a security component or an authorization pop-up. For details, see [Saving Media Assets](../../media/medialibrary/photoAccessHelper-savebutton.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| photoType  | [PhotoType](arkts-apis-photoAccessHelper-e.md#phototype)        | Yes  | Type of the file to create, which can be **IMAGE** or **VIDEO**.             |
| extension  | string        | Yes  | File name extension, for example, **'jpg'**.             |
| options  | [CreateOptions](arkts-apis-photoAccessHelper-i.md#createoptions)        | Yes  | Options used for creation. Currently, only **title** is supported, for example, **{title: 'testPhoto'}**.<br>**NOTE**<br>If a **subtype** option is passed, the configuration does not take effect. Only DEFAULT images can be saved.<br>The file name must not contain any invalid characters, which are:.. \ / : * ? " ' ` < > \| { } [ ] |
| callback |  AsyncCallback&lt;string&gt; | Yes  | Callback used to return the URI of the created image or video asset.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

In API version 13 and earlier versions, if the caller does not have the required permission, error code 13900012 is returned. Starting from API version 14, the same situation raises error code 201.

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. <br> Applicable versions: 11+   |
| 13900012     | Permission denied. <br> Applicable version: 10        |
| 13900020 | Invalid parameter. Possible causes:<br>1. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>2. The number of arguments is invalid.<br>3. The argument list is empty.<br>4. The object is not a valid instance.<br>5. PhotoAccessHelper object is not a valid instance obtained through the proper API.<br>6. The callback parameter type does not match, expected AsyncCallback.<br>7. Failed to get the photoType parameter, please check the parameter type.<br>8. The photoType parameter is not a valid number type.<br>9. Invalid file type, must be IMAGE or VIDEO.<br>10. Failed to parse the extension parameter, please check if it is a valid string.<br>11. Failed to get the options parameter type, please check if it is an object.<br>12. Failed to parse CreateOptions, please check the options parameter.<br>13. Server returned an invalid argument error.<br>14. Failed to get the photoType parameter. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The photoType parameter is not a valid PhotoType enum value, must be IMAGE or VIDEO.<br>2. The extension parameter is not a valid string, please check if it is a valid file extension.<br>3. The options parameter is invalid, please check if it is a valid CreateOptions object.<br>4. Failed to create the asset, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
  let extension:string = 'jpg';
  let options: photoAccessHelper.CreateOptions = {
    title: 'testPhoto'
  }
  phAccessHelper.createAsset(photoType, extension, options, (err, uri) => {
    if (uri !== undefined) {
      console.info('createAsset uri' + uri);
      console.info('createAsset successfully');
    } else {
      console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
    }
  });
}
```

## createAsset

createAsset(photoType: PhotoType, extension: string, callback: AsyncCallback&lt;string&gt;): void

Creates an image or video asset with the specified file type and file name extension. This API uses an asynchronous callback to return the result.

If you do not have the **ohos.permission.WRITE_IMAGEVIDEO** permission, you can create a media asset by using a security component or an authorization pop-up. For details, see [Saving Media Assets](../../media/medialibrary/photoAccessHelper-savebutton.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| photoType  | [PhotoType](arkts-apis-photoAccessHelper-e.md#phototype)        | Yes  | Type of the file to create, which can be **IMAGE** or **VIDEO**.             |
| extension  | string        | Yes  | File name extension, for example, **'jpg'**.             |
| callback |  AsyncCallback&lt;string&gt; | Yes  | Callback used to return the URI of the created image or video asset.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

In API version 13 and earlier versions, if the caller does not have the required permission, error code 13900012 is returned. Starting from API version 14, the same situation raises error code 201.

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. <br> Applicable versions: 11+  |
| 13900012     | Permission denied. <br> Applicable version: 10        |
| 13900020 | Invalid parameter. Possible causes:<br>1. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs<br>2. The number of arguments is invalid.<br>3. The argument list is empty.<br>4. The object is not a valid instance.<br>5. PhotoAccessHelper object is not a valid instance obtained through the proper API.<br>6. The callback parameter type does not match, expected AsyncCallback.<br>7. Failed to get the photoType parameter, please check the parameter type.<br>8. The photoType parameter is not a valid number type.<br>9. Invalid file type, must be IMAGE or VIDEO.<br>10. Failed to parse the extension parameter, please check if it is a valid string.<br>11. Failed to get parameter type, please check the parameter.<br>12. Failed to get the photoType parameter.<br>13. Server returned an invalid argument error. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The photoType parameter is not a valid PhotoType enum value, must be IMAGE or VIDEO.<br>2. The extension parameter is not a valid string, please check if it is a valid file extension.<br>3. Failed to create the asset, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
  let extension: string = 'jpg';
  phAccessHelper.createAsset(photoType, extension, (err, uri) => {
    if (uri !== undefined) {
      console.info('createAsset uri' + uri);
      console.info('createAsset successfully');
    } else {
      console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
    }
  });
}
```

## createAsset

createAsset(photoType: PhotoType, extension: string, options?: CreateOptions): Promise&lt;string&gt;

Creates an image or video asset with the specified file type, file name extension, and options. This API uses a promise to return the result.

If you do not have the **ohos.permission.WRITE_IMAGEVIDEO** permission, you can create a media asset by using a security component or an authorization pop-up. For details, see [Saving Media Assets](../../media/medialibrary/photoAccessHelper-savebutton.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| photoType  | [PhotoType](arkts-apis-photoAccessHelper-e.md#phototype)        | Yes  | Type of the file to create, which can be **IMAGE** or **VIDEO**.             |
| extension  | string        | Yes  | File name extension, for example, **'jpg'**.             |
| options  | [CreateOptions](arkts-apis-photoAccessHelper-i.md#createoptions)        | No  | Options used for creation. Currently, only **title** is supported, for example, **{title: 'testPhoto'}**.<br>**NOTE**<br>If a **subtype** option is passed, the configuration does not take effect. Only DEFAULT images can be saved.<br>The file name must not contain any invalid characters, which are:.. \ / : * ? " ' ` < > \| { } [ ] |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;string&gt; | Promise used to return the URI of the created image or video asset.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

In API version 13 and earlier versions, if the caller does not have the required permission, error code 13900012 is returned. Starting from API version 14, the same situation raises error code 201.

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. <br> Applicable versions: 11+ |
| 13900012     | Permission denied. <br> Applicable version: 10        |
| 13900020 | Invalid parameter. Possible causes:<br>1. System internal error. Possible: (1) File system exception; (2) IPC timeout. Please retry and check logs<br>2. The number of arguments is invalid.<br>3. The argument list is empty.<br>4. The object is not a valid instance.<br>5. PhotoAccessHelper object is not a valid instance obtained through the proper API.<br>6. The callback parameter type does not match, expected AsyncCallback.<br>7. Failed to get the photoType parameter, please check the parameter type.<br>8. The photoType parameter is not a valid number type.<br>9. Invalid file type, must be IMAGE or VIDEO.<br>10. Failed to parse the extension parameter, please check if it is a valid string.<br>11. Failed to get the options parameter type, please check if it is an object.<br>12. Failed to parse CreateOptions, please check the options parameter.<br>13. Server returned an invalid argument error.<br>14. Failed to get the photoType parameter. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The photoType parameter is not a valid PhotoType enum value, must be IMAGE or VIDEO.<br>2. The extension parameter is not a valid string, please check if it is a valid file extension.<br>3. The options parameter is invalid, please check if it is a valid CreateOptions object.<br>4. Failed to create the asset, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let options: photoAccessHelper.CreateOptions = {
      title: 'testPhoto'
    }
    let uri: string = await phAccessHelper.createAsset(photoType, extension, options);
    console.info('createAsset uri' + uri);
    console.info('createAsset successfully');
  } catch (err) {
    console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## createPhotoAsset<sup>23+</sup>

createPhotoAsset(photoType: PhotoType, extension: string, title?: string): Promise\<string\>

Creates an image or video resource with the specified file type, extension, and title. This API uses a promise to return the result.

If you do not have the **ohos.permission.WRITE_IMAGEVIDEO** permission, you can create a media asset by using a security component or an authorization pop-up. For details, see [Saving Media Assets](../../media/medialibrary/photoAccessHelper-savebutton.md).

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 23.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| photoType  | [PhotoType](arkts-apis-photoAccessHelper-e.md#phototype)        | Yes  | Type of the file to be created. For example, **IMAGE** or **VIDEO**.             |
| extension  | string        | Yes  | File name extension. For example, **jpg**, **png**, or **mp4**.|
| title | string | No  | Title of the image or video resource.    |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;string&gt; | Promise used to return the URL of the created image or video.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | The scenario parameter verification fails.Possible causes: 1. The extension format is unsupported. 2. Title contains unsupported character, such as . .. \ / : * ? " ' ` < > \| { } [ ]. 3. The title is an empty string 4. The total length of title and extension is more than 255. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>Server returned an invalid argument error. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createPhotoAssetDemo');
  try {
    let photoType: photoAccessHelper.PhotoType = photoAccessHelper.PhotoType.IMAGE;
    let extension: string = 'jpg';
    let title: string = 'testPhoto';
    let uri: string = await phAccessHelper.createPhotoAsset(photoType, extension, title);
    console.info('createPhotoAsset uri' + uri);
    console.info('createPhotoAsset successfully');
  } catch (err) {
    console.error(`createPhotoAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getAlbums

getAlbums(type: AlbumType, subtype: AlbumSubtype, options: FetchOptions, callback: AsyncCallback&lt;FetchResult&lt;Album&gt;&gt;): void

Obtains albums based on the specified options and album type. This API uses an asynchronous callback to return the result.

Before the operation, ensure that the albums to obtain exist.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| type  | [AlbumType](arkts-apis-photoAccessHelper-e.md#albumtype)         | Yes  | Type of the album.             |
| subtype  | [AlbumSubtype](arkts-apis-photoAccessHelper-e.md#albumsubtype)         | Yes  | Subtype of the album.             |
| options  | [FetchOptions](arkts-apis-photoAccessHelper-i.md#fetchoptions)         | Yes  |  Retrieval options.             |
| callback |  AsyncCallback&lt;[FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)&lt;[Album](arkts-apis-photoAccessHelper-Album.md)&gt;&gt; | Yes  | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

In API version 13 and earlier versions, if the caller does not have the required permission, error code 13900012 is returned. Starting from API version 14, the same situation raises error code 201.

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. <br> Applicable versions: 12+|
| 13900012     | Permission denied. <br> Applicable versions: 10 to 11        |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters is invalid, expected 0 to 4 parameters.<br>2. The callback parameter must be of type AsyncCallback.<br>3. The type parameter must be a number.<br>4. The type must be a valid AlbumType (USER, SYSTEM, SMART, or SOURCE).<br>5. The subtype parameter must be a number.<br>6. The subtype must be a valid AlbumSubtype.<br>7. The fetchColumns contain invalid column names. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The type parameter is not a valid number, must be a valid AlbumType enum value.<br>2. The subtype parameter is not a valid number, must be a valid AlbumSubtype enum value.<br>3. The FetchOptions parameter is invalid, the predicates contain invalid content or the fetchColumns contain unknown column names.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>5. The query result is empty, the IPC or database query returned no albums (not caused by permission or system app errors). |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // Obtain the album named newAlbumName.
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions, async (err, fetchResult) => {
    if (err) {
      console.error(`getAlbumsCallback failed with err: ${err.code}, ${err.message}`);
      return;
    }
    if (fetchResult === undefined) {
      console.error('getAlbumsCallback fetchResult is undefined');
      return;
    }
    let album = await fetchResult.getFirstObject();
    console.info('getAlbumsCallback successfully, albumName: ' + album.albumName);
    fetchResult.close();
  });
}
```

## getAlbums

getAlbums(type: AlbumType, subtype: AlbumSubtype, callback: AsyncCallback&lt;FetchResult&lt;Album&gt;&gt;): void

Obtains albums by type. This API uses an asynchronous callback to return the result.

Before the operation, ensure that the albums to obtain exist.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| type  | [AlbumType](arkts-apis-photoAccessHelper-e.md#albumtype)         | Yes  | Type of the album.             |
| subtype  | [AlbumSubtype](arkts-apis-photoAccessHelper-e.md#albumsubtype)         | Yes  | Subtype of the album.             |
| callback |  AsyncCallback&lt;[FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)&lt;[Album](arkts-apis-photoAccessHelper-Album.md)&gt;&gt; | Yes  | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  <br> Applicable versions: 12+ |
| 13900012     | Permission denied. <br> Applicable versions: 10 to 11        |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters is invalid, expected 0 to 4 parameters.<br>2. The callback parameter must be of type AsyncCallback.<br>3. The type parameter must be a number.<br>4. The type must be a valid AlbumType (USER, SYSTEM, SMART, or SOURCE).<br>5. The subtype parameter must be a number.<br>6. The subtype must be a valid AlbumSubtype. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The type parameter is not a valid number, must be a valid AlbumType enum value.<br>2. The subtype parameter is not a valid number, must be a valid AlbumSubtype enum value.<br>3. The query result is empty, the IPC or database query returned no albums (not caused by permission or system app errors).<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // Obtain the system album VIDEO, which is preset by default.
  console.info('getAlbumsDemo');
  phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.VIDEO, async (err, fetchResult) => {
    if (err) {
      console.error(`getAlbumsCallback failed with err: ${err.code}, ${err.message}`);
      return;
    }
    if (fetchResult === undefined) {
      console.error('getAlbumsCallback fetchResult is undefined');
      return;
    }
    let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsCallback successfully, albumUri: ' + album.albumUri);
    fetchResult.close();
  });
}
```

## getAlbums

getAlbums(type: AlbumType, subtype: AlbumSubtype, options?: FetchOptions): Promise&lt;FetchResult&lt;Album&gt;&gt;

Obtains albums based on the specified options and album type. This API uses a promise to return the result.

Before the operation, ensure that the albums to obtain exist.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| type  | [AlbumType](arkts-apis-photoAccessHelper-e.md#albumtype)         | Yes  | Type of the album.             |
| subtype  | [AlbumSubtype](arkts-apis-photoAccessHelper-e.md#albumsubtype)         | Yes  | Subtype of the album.             |
| options  | [FetchOptions](arkts-apis-photoAccessHelper-i.md#fetchoptions)         | No  |  Retrieval options. If this parameter is not specified, the albums are obtained based on the album type by default.             |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)&lt;[Album](arkts-apis-photoAccessHelper-Album.md)&gt;&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

If error code 13900012 is returned, follow the instructions provided in [Before You Start](../../media/medialibrary/photoAccessHelper-preparation.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. <br> Applicable versions: 12+|
| 13900012     | Permission denied. <br> Applicable versions: 10 to 11        |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters is invalid, expected 0 to 4 parameters.<br>2. The callback parameter must be of type AsyncCallback.<br>3. The type parameter must be a number.<br>4. The type must be a valid AlbumType (USER, SYSTEM, SMART, or SOURCE).<br>5. The subtype parameter must be a number.<br>6. The subtype must be a valid AlbumSubtype.<br>7. The fetchColumns contain invalid column names. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The type parameter is not a valid number, must be a valid AlbumType enum value.<br>2. The subtype parameter is not a valid number, must be a valid AlbumSubtype enum value.<br>3. The FetchOptions parameter is invalid, the predicates contain invalid content or the fetchColumns contain unknown column names.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>5. The query result is empty, the IPC or database query returned no albums (not caused by permission or system app errors). |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // Obtain the album named newAlbumName.
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getAlbumsPromise fetchResult is undefined');
      return;
    }
    let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsPromise successfully, albumName: ' + album.albumName);
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getAlbumsPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## registerChange

registerChange(uri: string, forChildUris: boolean, callback: Callback&lt;ChangeData&gt;) : void

Registers listening for the specified URI. This API uses a callback to return the result.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name   | Type                                       | Mandatory| Description                                                        |
| --------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| uri       | string                                      | Yes  | URI of the photo asset, URI of the album, or [DefaultChangeUri](arkts-apis-photoAccessHelper-e.md#defaultchangeuri).|
| forChildUris | boolean                                     | Yes  | Whether to perform fuzzy listening.<br> If **uri** is the URI of an album, the value **true** means to listen for the changes of the files in the album; the value **false** means to listen for the changes of the album only.<br>If **uri** is the URI of a photoAsset, there is no difference between **true** and false for **forChildUris**.<br>If **uri** is **DefaultChangeUri**, **forChildUris** must be set to **true**. If **forChildUris** is false, the URI cannot be found and no message can be received.|
| callback  | Callback&lt;[ChangeData](arkts-apis-photoAccessHelper-i.md#changedata)&gt; | Yes  | Callback used to return [ChangeData](arkts-apis-photoAccessHelper-i.md#changedata). **NOTE**: Multiple callback listeners can be registered for a URI. You can use [unRegisterChange](#unregisterchange) to unregister all listeners for the URI or a specified callback listener.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

If error code 13900012 is returned, follow the instructions provided in [Before You Start](../../media/medialibrary/photoAccessHelper-preparation.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900012     | Permission denied.         |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters is invalid, expected 3 parameters.<br>2. The uri parameter must be a string.<br>3. The forChildUris parameter must be a boolean.<br>4. The callback parameter must be a function.<br>5. The uri string extraction failed.<br>6. The forChildUris boolean value extraction failed.<br>7. The callback is already registered for this uri, duplicate registration is not allowed.<br>8. The object is not a valid instance. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('registerChangeDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  if (photoAsset !== undefined) {
    console.info('photoAsset.displayName : ' + photoAsset.displayName);
    } else {
      console.error('photoAsset is undefined');
      return;
    }
  let onCallback1 = (changeData: photoAccessHelper.ChangeData) => {
      console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
    // file had changed, do something.
  }
  let onCallback2 = (changeData: photoAccessHelper.ChangeData) => {
      console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
    // file had changed, do something.
  }
  // Register onCallback1.
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback1);
  // Register onCallback2.
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback2);

  await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [photoAsset]);
}
```

## unRegisterChange

unRegisterChange(uri: string, callback?: Callback&lt;ChangeData&gt;): void

Unregisters a listener for the specified URI. Multiple listeners can be registered for a URI. If multiple listeners are registered, you can unregister a specific listener by specifying **callback**. Alternatively, you can unregister all of them without specifying **callback**.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                                       | Mandatory| Description                                                        |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| uri      | string                                      | Yes  | URI of the photo asset, URI of the album, or [DefaultChangeUri](arkts-apis-photoAccessHelper-e.md#defaultchangeuri).|
| callback | Callback&lt;[ChangeData](arkts-apis-photoAccessHelper-i.md#changedata)&gt; | No  | Callback to unregister. If this parameter is not specified, all the callbacks for listening for the URI will be canceled. **NOTE**: The specified callback unregistered will not be invoked when the data changes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

If error code 13900012 is returned, follow the instructions provided in [Before You Start](../../media/medialibrary/photoAccessHelper-preparation.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900012     | Permission denied.         |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters is invalid, expected 1 or 2 parameters.<br>2. The uri parameter must be a string.<br>3. The uri string extraction failed.<br>4. The callback parameter must be a function.<br>5. The object is not a valid instance. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('offDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  if (photoAsset !== undefined) {
    console.info('photoAsset.displayName : ' + photoAsset.displayName);
    } else {
      console.error('photoAsset is undefined');
      return;
    }
  let onCallback1 = (changeData: photoAccessHelper.ChangeData) => {
    console.info('onCallback1 on');
  }
  let onCallback2 = (changeData: photoAccessHelper.ChangeData) => {
    console.info('onCallback2 on');
  }
  // Register onCallback1.
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback1);
  // Register onCallback2.
  phAccessHelper.registerChange(photoAsset.uri, false, onCallback2);
  // Unregister the listening of onCallback1.
  phAccessHelper.unRegisterChange(photoAsset.uri, onCallback1);
  await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [photoAsset]);
}
```

## applyChanges<sup>11+</sup>

applyChanges(mediaChangeRequest: MediaChangeRequest): Promise&lt;void&gt;

Applies media changes. This API uses a promise to return the result.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

If you do not have the **ohos.permission.WRITE_IMAGEVIDEO** permission, you can create a media asset by using a security component or an authorization pop-up. For details, see [Saving Media Assets](../../media/medialibrary/photoAccessHelper-savebutton.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| mediaChangeRequest  | [MediaChangeRequest](arkts-apis-photoAccessHelper-i.md#mediachangerequest11)  | Yes |  Request for asset changes or album changes.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;void&gt;| Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The mediaChangeRequest parameter is not a valid MediaChangeRequest object.<br>2. Server returned an error during applyChanges, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>3. The resource change operation for the current request type is not supported. |

**Example**

This API depends on the [MediaChangeRequest](arkts-apis-photoAccessHelper-i.md#mediachangerequest11) object. For details about the sample code, see the examples of [MediaAssetChangeRequest](arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md) and [MediaAlbumChangeRequest](arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md).

## release

release(callback: AsyncCallback&lt;void&gt;): void

Releases the **PhotoAccessHelper** instance. This API uses an asynchronous callback to return the result.

Call this API when the APIs of the PhotoAccessHelper instance are no longer used.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                |
| -------- | ------------------------- | ---- | -------------------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters exceeds the maximum limit.<br>2. The current object is invalid.<br>3. The PhotoAccessHelper object is not a valid object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. PhotoAccessHelper has been released, no need to release again.<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('releaseDemo');
  phAccessHelper.release((err) => {
    if (err !== undefined) {
      console.error(`release failed. error: ${err.code}, ${err.message}`);
    } else {
      console.info('release ok.');
    }
  });
}
```

## release

release(): Promise&lt;void&gt;

Releases the **PhotoAccessHelper** instance. This API uses a promise to return the result.

Call this API when the APIs of the PhotoAccessHelper instance are no longer used.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value**

| Type               | Description                             |
| ------------------- | --------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900020 | Invalid parameter. Possible causes:<br>1. The number of parameters exceeds the maximum limit.<br>2. The current object is invalid.<br>3. The PhotoAccessHelper object is not a valid object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. PhotoAccessHelper has been released, no need to release again.<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('releaseDemo');
  try {
    await phAccessHelper.release();
    console.info('release ok.');
  } catch (err) {
    console.error(`release failed. error: ${err.code}, ${err.message}`);
  }
}
```

## showAssetsCreationDialog<sup>12+</sup>

showAssetsCreationDialog(srcFileUris: Array&lt;string&gt;, photoCreationConfigs: Array&lt;PhotoCreationConfig&gt;): Promise&lt;Array&lt;string&gt;&gt;

Displays a dialog box for the user to confirm whether to save the images or videos. If the user agrees to save the images or videos, this API returns a list of URIs that have been created and granted save permissions (this list is permanent), and the application can use these URIs to write the images or videos. If the user declines to save the images or videos, this API returns an empty list.

The dialog box must display the application name, but this cannot be directly obtained. Therefore, before calling this API, ensure that the **label** and **icon** items are configured in the **abilities** tag in the [module.json5 configuration file](../../../application-dev/quick-start/module-configuration-file.md). Note that the icon is not affected by the **icon** item in the **abilities** tag and cannot be modified.

> **NOTE**
>
> - If the passed URI is a sandbox path, images or videos can be saved but cannot be previewed.
> - The difference between **showAssetsCreationDialog** and **showAssetsCreationDialogEx** is that **showAssetsCreationDialog** uses **PhotoCreationConfig** for configuration, while **showAssetsCreationDialogEx** uses **CreationSetting**.
> - The difference between **showAssetsCreationDialog** and **showSingleAssetCreationDialogEx** is that **showAssetsCreationDialog** allows you to save images in batches (up to 100 images), while **showSingleAssetCreationDialogEx** allows you to save only a single asset. Use this API for batch saving. If you need to control the image display mode when saving a single asset, use **showSingleAssetCreationDialogEx**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| srcFileUris | Array&lt;string&gt; | Yes| [URIs](../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be saved to the media library.<br>**NOTE**<br>- A maximum of 100 images can be saved at a time.<br>- Only image and video URIs are supported.<br>- URIs cannot be manually constructed. You must call APIs to obtain them. For details, see [Obtaining a Media File URI](../../file-management/user-file-uri-intro.md#obtaining-a-media-file-uri). |
| photoCreationConfigs | Array&lt;[PhotoCreationConfig](arkts-apis-photoAccessHelper-i.md#photocreationconfig12)&gt; | Yes| Configuration for saving the images or videos, including the file names. The value must be consistent with that of **srcFileUris**.<br>**NOTE**<br>If a **subtype** option is passed, the configuration does not take effect. Only DEFAULT images can be saved.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return a URI list. The URIs are granted with the permission for the application to write data. If the URIs fail to be generated, a batch creation error code will be returned.<br>The return values are as follows:<br>- **-3006**: Invalid characters, which are not allowed.<br>-**-2004**: The image type does not match the file name extension.<br>-**-203**: Invalid file operation.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 |  Internal system error. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Internal error in dialog, please retry.<br>2. Dialog result missing required parameters, system internal error.<br>3. Callback processing failed, system internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('ShowAssetsCreationDialogDemo.');

  try {
    // Obtain the sandbox URIs of the images or videos to be saved to the media library.
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // The URI here is an example only.
    ];
    let photoCreationConfigs: Array<photoAccessHelper.PhotoCreationConfig> = [
      {
        title: 'test2', // Optional.
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE,
        subtype: photoAccessHelper.PhotoSubtype.DEFAULT, // This parameter is optional.
      }
    ];
    let desFileUris: Array<string> = await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
    console.info('showAssetsCreationDialog success, data is ' + desFileUris);
  } catch (err) {
    console.error(`showAssetsCreationDialog failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## showAssetsCreationDialogEx<sup>23+</sup>

showAssetsCreationDialogEx(srcFileUris: Array&lt;string&gt;, creationSettings: Array&lt;CreationSetting&gt;): Promise&lt;Array&lt;string&gt;&gt;

Displays a dialog box for the user to confirm whether to save the images or videos. This API uses a promise to return the result.

> **NOTE**
>
> - The difference between **showAssetsCreationDialogEx** and **showAssetsCreationDialog** is that **showAssetsCreationDialogEx** uses **CreationSetting** for configuration, while **showAssetsCreationDialog** uses **PhotoCreationConfig** for configuration.
> - If the user agrees, the list of created URIs with the save permission granted is returned. The list is permanently valid and supports image or video writing. If the user rejects, an empty list is returned.
> - The app name needs to be displayed in the dialog box. You need to configure the **label** and **icon** items in the **abilities** tag of the [module.json5 configuration file](../../../application-dev/quick-start/module-configuration-file.md).
> - If the passed URI is a sandbox path, images or videos can be saved but cannot be previewed.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name          | Type                                                                                | Mandatory| Description                     |
| ---------------- |-------------------------------------------------------------------------------------| ---- | ------------------------- |
| srcFileUris      | Array&lt;string&gt;                                                                 | Yes| [URIs](../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be saved to the media library.<br>**NOTE**<br>- A maximum of 100 images can be saved at a time.<br>- Only image and video URIs are supported.<br>- URIs cannot be manually constructed. You must call APIs to obtain them. For details, see [Obtaining a Media File URI](../../file-management/user-file-uri-intro.md#obtaining-a-media-file-uri). |
| creationSettings | Array&lt;[CreationSetting](arkts-apis-photoAccessHelper-i.md#creationsetting23)&gt; | Yes| Configuration for saving images or videos to the media library, including the file name. The URI in this parameter must correspond to that in the **srcFileUris** parameter.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return a URI list. The application can use the returned URI to write data.|

**Error codes**

For details about the error codes, see [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ----------------------- |
| 23800301 |Internal system error. It is recommended to retry and check the logs. Possible causes: 1. Database corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts 
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) { 
  console.info('ShowAssetsCreationDialogExDemo.'); 

  try {
    // Obtain the sandbox URIs of the images or videos to be saved to the media library.
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // The URI here is an example only.
    ];
    let creationConfigs: Array<photoAccessHelper.CreationSetting> = [
      {
        title: 'test2', // Optional.
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE
      }
    ];
    let desFileUris: Array<string> = await phAccessHelper.showAssetsCreationDialogEx(srcFileUris, creationConfigs);
    console.info('showAssetsCreationDialogEx success, data is ' + desFileUris);
  } catch (err) {
    console.error(`showAssetsCreationDialogEx failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## showSingleAssetCreationDialogEx<sup>23+</sup>

showSingleAssetCreationDialogEx(srcFileUri: string, creationSetting: CreationSetting, isImageFullyDisplayed: boolean): Promise&lt;string&gt;

Displays a dialog box for the user to confirm whether to save an image or video. This API uses a promise to return the result.

> **NOTE**
>
> - The difference between **showAssetsCreationDialog** and **showAssetsCreationDialog** is that **showSingleAssetCreationDialogEx** can only save a single asset, while **showAssetsCreationDialog** can save images in batches (up to 100 images). If you need to save a single asset and control the image display mode, use **showSingleAssetCreationDialogEx**.
> - If the user agrees to save the images or videos, this API returns a URI that has been created and granted with the save permission (this URI is permanent), and the application can use this URI to write the image or video. If the user declines to save the image or video, this API returns an empty string.
> - The dialog box must display the application name, but this cannot be directly obtained. Therefore, before calling this API, ensure that the **label** and **icon** items are configured in the **abilities** tag in the [module.json5 configuration file](../../../application-dev/quick-start/module-configuration-file.md). Note that the icon is not affected by the **icon** item in the **abilities** tag and cannot be modified.
> - If the passed URI is a sandbox path, images or videos can be saved but cannot be previewed.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| srcFileUri | string | Yes| [URIs](../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be saved to the media library.<br>**NOTE**<br>- Only one image can be saved at a time.<br>- Only image and video URIs are supported.<br>- URIs cannot be manually constructed. You must call APIs to obtain them. For details, see [Obtaining a Media File URI](../../file-management/user-file-uri-intro.md#obtaining-a-media-file-uri). |
| creationSetting | [CreationSetting](arkts-apis-photoAccessHelper-i.md#creationsetting23) | Yes| Configuration for saving the image or video, including the file name. The value must be consistent with that of **srcFileUri **.|
| isImageFullyDisplayed | boolean | Yes| Whether the image is displayed completely. The value **true** indicates that the image is displayed completely, and **false** indicates the opposite. |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;string&gt; | Promise used to return the URIs of media library files. In normal cases, available media library URIs are returned. The app is granted with permissions for the URIs and is allowed to write data. If the URIs fail to be generated, a batch creation error code will be returned.<br>The return values are as follows:<br>- **-3006**: Invalid characters, which are not allowed.<br>-**-2004**: The image type does not match the file name extension.<br>-**-203**: Invalid file operation.|

**Error codes**

For details about the error codes, see [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Internal error in dialog, please retry.<br>2. Dialog result missing required parameters, system internal error.<br>3. Dialog operation failed, please retry.<br>4. Callback processing failed, system internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Internal error in dialog, please retry.<br>2. Dialog result missing required parameters, system internal error.<br>3. Callback processing failed, system internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('ShowSingleAssetCreationDialogExDemo.');

  try {
    // Obtain the sandbox URIs of the images or videos to be saved to the media library.
    let srcFileUri: string = 'file://fileUriDemo1'; // The URI here is an example only.
    let photoCreationConfig: photoAccessHelper.CreationSetting = {
      title: 'test2', // Optional.
      fileNameExtension: 'jpg',
      photoType: photoAccessHelper.PhotoType.IMAGE
    }
    let isImageFullyDisplayed: boolean = true
    let desFileUri: string = await phAccessHelper.showSingleAssetCreationDialogEx(srcFileUri, photoCreationConfig, isImageFullyDisplayed);
    console.info('showSingleAssetCreationDialogEx success, data is ' + desFileUri);
  } catch (err) {
    console.error(`showSingleAssetCreationDialogEx failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## createAssetWithShortTermPermission<sup>12+</sup>

createAssetWithShortTermPermission(photoCreationConfig: PhotoCreationConfig): Promise&lt;string&gt;

When an app calls this API for the first time, a confirmation dialog box is displayed. After the user agrees to save the asset, the URI of the created asset that has the save permission is returned. The app can use the URI to write the image or video.

Within 5 minutes after the user agrees to save the asset, if the same application calls this API again, the authorized URI can be automatically returned without the need to display the confirmation dialog box. Exiting the app will terminate the authorization, and the user need to re-trigger the dialog box for authorization confirmation when the app is re-launched.

> **NOTE**
>
> The difference between **createAssetWithShortTermPermission** and **createAssetWithShortTermPermissionEx** is that **createAssetWithShortTermPermission** uses **PhotoCreationConfig** for configuration, while **createAssetWithShortTermPermissionEx** uses **CreationSetting**.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.SHORT_TERM_WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| photoCreationConfig | [PhotoCreationConfig](arkts-apis-photoAccessHelper-i.md#photocreationconfig12) | Yes| Configuration for saving a media asset (image or video) to the media library, including the file name.<br>**NOTE**<br>If a **subtype** option is passed, the configuration does not take effect. Only DEFAULT images can be saved.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;string&gt; | Promise used to return the URIs of media library files. The URIs are granted with the permission for the application to write data. If the URIs fail to be generated, a batch creation error code will be returned.<br>The error code **-3006** means that there are invalid characters; **-2004** means that the image type does not match the file name extension; **-203** means that the file operation is abnormal.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 |  Internal system error |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { fileIo } from '@kit.CoreFileKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
    console.info('createAssetWithShortTermPermissionDemo.');
    
    try {
        let photoCreationConfig: photoAccessHelper.PhotoCreationConfig = {
            title: '123456', 
            fileNameExtension: 'jpg',
            photoType: photoAccessHelper.PhotoType.IMAGE,
            subtype: photoAccessHelper.PhotoSubtype.DEFAULT, 
        };

        let resultUri: string = await phAccessHelper.createAssetWithShortTermPermission(photoCreationConfig);
        let resultFile: fileIo.File = fileIo.openSync(resultUri, fileIo.OpenMode.READ_WRITE);
        // Use the actual URI and file size.
        let srcFile:  fileIo.File = fileIo.openSync("file://test.jpg", fileIo.OpenMode.READ_ONLY);
        let bufSize: number = 2000000;
        let readSize: number = 0;
        let buf = new ArrayBuffer(bufSize);
        let readLen = fileIo.readSync(srcFile.fd, buf, {
            offset: readSize,
            length: bufSize
        });
        if (readLen > 0) {
            readSize += readLen;
            fileIo.writeSync(resultFile.fd, buf, { length: readLen });
        }
        fileIo.closeSync(srcFile);
        fileIo.closeSync(resultFile);
    } catch (err) {
        console.error(`createAssetWithShortTermPermission failed. Code: ${err.code}, message: ${err.message}`);
    }
    
}
```

## createAssetWithShortTermPermissionEx<sup>23+</sup>

createAssetWithShortTermPermissionEx(creationSetting: CreationSetting): Promise&lt;string&gt;

Displays the dialog box for the first time for the user to confirm whether to save the asset. This API uses a promise to return the result.

> **NOTE**
>
> - The difference between **createAssetWithShortTermPermissionEx** and **createAssetWithShortTermPermission** is that **createAssetWithShortTermPermissionEx** uses **CreationSetting** for configuration, while **createAssetWithShortTermPermission** uses **PhotoCreationConfig**.
> - After the user agrees to save the asset, the API returns the URI of the created asset that has the save permission. The app can use the URI to write the image or video.
> - Within 5 minutes after the user agrees to save the asset, if the same app calls this API again, the system directly returns the authorized URI for the app to save the image or video without displaying a confirmation dialog box. Exiting the app will terminate the authorization, and the user need to re-trigger the dialog box for authorization confirmation when the app is re-launched.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.SHORT_TERM_WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| creationSetting | [CreationSetting](arkts-apis-photoAccessHelper-i.md#creationsetting23) | Yes| Configuration for saving a media asset (image or video) to the media library, including the file name.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;string&gt; | Promise used to return the URIs of media library files. The application can use the returned URI to write data.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 14000011 |  Internal system error |

## requestPhotoUrisReadPermission<sup>14+</sup>

requestPhotoUrisReadPermission(srcFileUris: Array&lt;string&gt;): Promise&lt;Array&lt;string&gt;&gt;

<!--RP1--><!--RP1End-->Grants the read permission for unauthorized URIs, returning a list of URIs that have been created and granted the permission.

> **NOTE**
>
> The difference between **requestPhotoUrisReadPermission** and **requestPhotoUrisReadPermissionEx** is that **requestPhotoUrisReadPermission** returns only the list of URIs granted the permission, while **requestPhotoUrisReadPermissionEx** returns a **RequestReadPermissionResult** object that contains both the list of URIs granted the permission and the list of invalid URIs, helping you identify invalid URIs. Since API version 23, you are advised to use **requestPhotoUrisReadPermissionEx** to obtain a more complete authorization result.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| srcFileUris | Array&lt;string&gt; | Yes| [URIs](../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be granted with the permission.<br>**NOTE**<br>Only image and video URIs are supported, and the maximum number of URIs is 100.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the URIs granted with the permission.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Internal error in dialog, please retry.<br>2. Dialog result missing required parameters, system internal error.<br>3. Dialog operation failed, please retry.<br>4. Callback processing failed, system internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('requestPhotoUrisReadPermissionDemo.');

  try {
    // Obtain the URIs of the images or videos to be granted with the permission.
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // The URI here is an example only.
    ];
    let desFileUris: Array<string> = await phAccessHelper.requestPhotoUrisReadPermission(srcFileUris);
    console.info('requestPhotoUrisReadPermission success, data is ' + desFileUris);
  } catch (err) {
    console.error(`requestPhotoUrisReadPermission failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## requestPhotoUrisReadPermissionEx<sup>23+</sup>

requestPhotoUrisReadPermissionEx(srcFileUris: Array&lt;string&gt;): Promise&lt;RequestReadPermissionResult&gt;

Grants the read permission for unauthorized URIs. This API uses a promise to return the result.

It contains the list of URIs that have been created and granted the save permission and the list of invalid URIs.

**Atomic service API**: This API can be used in atomic services since API version 23.
  
​**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                                                                  | Mandatory| Description                     |
| -------- |----------------------------------------------------------------------| ---- | ------------------------- |
| srcFileUris | Array&lt;string&gt; | Yes| [URIs](../../file-management/user-file-uri-intro.md#media-file-uri) of the images or videos to be granted with the permission.<br>**NOTE**<br>Only image and video URIs are supported, and the maximum number of URIs is 100.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;RequestReadPermissionResult&gt; | Promise used to return the list of URIs granted with the permission and the list of invalid URIs.|

**Error codes**

For details about the error codes, see [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 23800301 |  Internal system error. It is recommended to retry and check the logs.<br>Possible causes: 1. Database corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
console.info('requestPhotoUrisReadPermissionExDemo.');

  try {
    // Obtain the URIs of the images or videos to be granted with the permission.
    let srcFileUris: Array<string> = [
      'file://fileUriDemo1' // The URI here is an example only.
    ];
    let requestReadPermissionResult: photoAccessHelper.RequestReadPermissionResult = await phAccessHelper.requestPhotoUrisReadPermissionEx(srcFileUris);
    console.info('requestPhotoUrisReadPermissionEx success, data is ' + requestReadPermissionResult);
  } catch (err) {
    console.error(`requestPhotoUrisReadPermissionEx failed. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getSupportedPhotoFormats<sup>18+</sup> 

getSupportedPhotoFormats(photoType: PhotoType): Promise&lt;Array&lt;string&gt;&gt;

Obtains the list of image or video file name extensions supported by the media library.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| photoType | [PhotoType](arkts-apis-photoAccessHelper-e.md#phototype) | Yes  | Type of the file.|

**Return value**

| Type                                    | Description             |
|------------------------------------------|-------------------------|
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return an array of the supported image or video file name extensions.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. invalid photoType.<br>2. Failed to create string.<br>3. Failed to set element. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, photoTypeNumber: number){
  console.info('getSupportedPhotoFormatsDemo.');

  try {
    let outputText: string;
    if (photoTypeNumber !== photoAccessHelper.PhotoType.IMAGE && photoTypeNumber !== photoAccessHelper.PhotoType.VIDEO) {
      outputText = 'Does not support querying formats other than images or videos';
      return;
    }
    outputText = 'The supported types are:\n';
    let imageFormat  = await phAccessHelper.getSupportedPhotoFormats(photoAccessHelper.PhotoType.IMAGE);
    let result = "";
    for (let i = 0; i < imageFormat.length; i++) {
      result += imageFormat[i];
      if (i !== imageFormat.length - 1) {
        result += ', ';
      }
    }
    outputText += result;
    console.info('getSupportedPhotoFormats success, data is ' + outputText);
  } catch (error) {
    console.error('getSupportedPhotoFormats failed, errCode is', error);
  }
}
```

## on('photoChange')<sup>20+</sup> 

on(type: 'photoChange', callback: Callback&lt;PhotoAssetChangeInfos&gt;): void

Registers a listener for the **'photoChange'** event to monitor media asset changes. This API uses a callback to return the result, and it accepts multiple callbacks.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| type | string | Yes  | Event type. The value is fixed at **'photoChange'**. After the registration is complete, any change to the media assets is returned through the callback.|
| callback  | Callback&lt;[PhotoAssetChangeInfos](arkts-apis-photoAccessHelper-i.md#photoassetchangeinfos20)&gt; | Yes  | Callback used to return the media asset information after change, which is [PhotoAssetChangeInfos](arkts-apis-photoAccessHelper-i.md#photoassetchangeinfos20).<br>**NOTE**<br>You can register multiple listeners using this API, and you can call [off('photoChange')](#offphotochange20) to unregister all listeners or a specific one.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | Invalid parameter. Possible causes:<br>1. Scenario parameter verification failed.<br>2. Invalid parameter. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Data service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is properly initialized and retry<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

// Register photoChange to listen for media asset changes. You can register multiple callbacks.
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onPhotoChangeDemo.');

  try {
    // Register onCallback1.
    phAccessHelper.on('photoChange', onCallback1);
    // Register onCallback2.
    phAccessHelper.on('photoChange', onCallback2);
  } catch (error) {
    console.error('onPhotoChangeDemo failed, errCode is', error);
  }
}
```

## off('photoChange')<sup>20+</sup> 

off(type: 'photoChange', callback?: Callback&lt;PhotoAssetChangeInfos&gt;): void

Unregisters the listener for the **'photoChange'** event to stop monitoring media asset changes. If multiple listeners are registered, you can unregister a specific listener by specifying **callback**. Alternatively, you can unregister all of them without specifying **callback**.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| type | string | Yes  | Event type. The value is fixed at **'photoChange'**. After the unregistration is complete, any change to the media assets is no longer returned through the callback.|
| callback | Callback&lt;[PhotoAssetChangeInfos](arkts-apis-photoAccessHelper-i.md#photoassetchangeinfos20)&gt; | No  | Exact callback you previously registered with [on('photoChange')](#onphotochange20). If this parameter is left unspecified, all listeners for the **'photoChange'** event are unregistered.<br>**NOTE**<br>Once a specific callback is unregistered, it will not be invoked when a media asset changes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | The scenario parameter verification fails.<br>Possible causes: 1. The type is not fixed at 'photoChange'; 2. The same callback is unregistered repeatedly. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Data service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is properly initialized and retry<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

// After registering the photoChange listener, cancel the specified listener to demonstrate how to cancel the listener.
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('offPhotoChangeDemo.');

  try {
    // Register onCallback1.
    phAccessHelper.on('photoChange', onCallback1);
    // Register onCallback2.
    phAccessHelper.on('photoChange', onCallback2);

    // Unregister the listening of onCallback1.
    phAccessHelper.off('photoChange', onCallback1);
  } catch (error) {
    console.error('offPhotoChangeDemo failed, errCode is', error);
  }
}
```

## on('photoAlbumChange')<sup>20+</sup> 

on(type: 'photoAlbumChange', callback: Callback&lt;AlbumChangeInfos&gt;): void

Registers a listener for the **'photoAlbumChange'** event to monitor album changes. This API uses a callback to return the result, and it accepts multiple callbacks.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| type | string | Yes  | Event type. The value is fixed at **'photoAlbumChange'**. After the registration is complete, any change to the albums is returned through the callback.|
| callback  | Callback&lt;[AlbumChangeInfos](arkts-apis-photoAccessHelper-i.md#albumchangeinfos20)&gt; | Yes  | Callback used to return the album information after change, which is [AlbumChangeInfos](arkts-apis-photoAccessHelper-i.md#albumchangeinfos20).<br>**NOTE**<br>You can register multiple listeners using this API, and you can call [off('photoAlbumChange')](#offphotoalbumchange20) to unregister all listeners or a specific one.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | Invalid parameter. Possible causes:<br>1. Scenario parameter verification failed.<br>2. Invalid parameter. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Data service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is properly initialized and retry<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

// Register photoAlbumChange to listen for album changes. You can register multiple callbacks.
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onPhotoAlbumChangeDemo.');

  try {
    // Register onCallback1.
    phAccessHelper.on('photoAlbumChange', onCallback1);
    // Register onCallback2.
    phAccessHelper.on('photoAlbumChange', onCallback2);
  } catch (error) {
    console.error('onPhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## off('photoAlbumChange')<sup>20+</sup> 

off(type: 'photoAlbumChange', callback?: Callback&lt;AlbumChangeInfos&gt;): void

Unregisters a listener for the **'photoAlbumChange'** event to stop monitoring album changes. If multiple listeners are registered, you can unregister a specific listener by specifying **callback**. Alternatively, you can unregister all of them without specifying **callback**.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| type | string | Yes  | Event type. The value is fixed at **'photoAlbumChange'**. After the unregistration is complete, any change to the albums is no longer returned through the callback.|
| callback | Callback&lt;[AlbumChangeInfos](arkts-apis-photoAccessHelper-i.md#albumchangeinfos20)&gt; | No  | Exact callback you previously registered with [on('photoAlbumChange')](#onphotoalbumchange20). If this parameter is left unspecified, all listeners for the **'photoAlbumChange'** event are unregistered.<br>**NOTE**<br>Once a specific callback is unregistered, it will not be invoked when an album changes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | The scenario parameter verification fails.<br>Possible causes: 1. The type is not fixed at 'photoAlbumChange'; 2. The same callback is unregistered repeatedly. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Data service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is properly initialized and retry<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

// After registering the photoAlbumChange listener, cancel the specified listener to demonstrate how to cancel the listener.
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onPhotoAlbumChangeDemo.');

  try {
    // Register onCallback1.
    phAccessHelper.on('photoAlbumChange', onCallback1);
    // Register onCallback2.
    phAccessHelper.on('photoAlbumChange', onCallback2);

    // Unregister the listening of onCallback1.
    phAccessHelper.off('photoAlbumChange', onCallback1);
  } catch (error) {
    console.error('onPhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## getPhotoPickerComponentDefaultAlbumName<sup>20+</sup>

getPhotoPickerComponentDefaultAlbumName(): Promise&lt;string&gt;

Obtains the name of the album that the photo picker component shows by default. The album name is returned in the language specified by the system language setting. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;string&gt;| Promise used to return the name of the default album.|

**Error codes**

For details about the error codes, see [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 23800301   | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. The IPC request timed out. 2. system running error.         |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import {photoAccessHelper} from '@kit.MediaLibraryKit';

async function example(context: Context) {
  console.info('getPhotoPickerComponentDefaultAlbumNameDemo');
  let phAccessHelper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  phAccessHelper.getPhotoPickerComponentDefaultAlbumName().then((defaultAlbumName) => {
    console.info('getPhotoPickerComponentDefaultAlbumName success, defaultAlbumName is ' + defaultAlbumName);
  }).catch((err: BusinessError) => {
    console.error(`getPhotoPickerComponentDefaultAlbumName failed with error: ${err.code}, ${err.message}`);
  });
}
```

## createDeleteRequest<sup>(deprecated)</sup>

createDeleteRequest(uriList: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Creates a dialog box for deleting media files. This API uses an asynchronous callback to return the result. The deleted media files are moved to the trash.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [MediaAssetChangeRequest.deleteAssets](arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#deleteassets11-1) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| uriList | Array&lt;string&gt; | Yes  | URIs of the media files to delete. A maximum of 300 media files can be deleted.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

If error code 13900012 is returned, follow the instructions provided in [Before You Start](../../media/medialibrary/photoAccessHelper-preparation.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900012 | Permission denied. Possible causes:<br>1. Not have ohos.permission.WRITE_IMAGEVIDEO.<br>2. User deny. |
| 13900020 | Invalid parameter. Possible causes:<br>1. The context parameter is invalid, failed to convert to AbilityContext.<br>2. Failed to create the dialog, system internal error, please retry. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The delete operation failed, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>2. The uriList parameter contains invalid URIs, please check if each URI is a valid file URI obtained from a valid query result.<br>3. The UI extension component reported an error, please retry. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createDeleteRequestDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> | undefined = undefined;
  try {
    fetchResult = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('asset not exist');
      return;
    }
    phAccessHelper.createDeleteRequest([asset.uri], (err) => {
      if (err) {
        console.error(`createDeleteRequest failed with error: ${err.code}, ${err.message}`);
      } else {
        console.info('createDeleteRequest successfully');
      }
    });
  } catch (err) {
    console.error(`fetch failed, error: ${err.code}, ${err.message}`);
  } finally {
    // Release resources after use.
    fetchResult?.close();
  }
}
```

## createDeleteRequest<sup>(deprecated)</sup>

createDeleteRequest(uriList: Array&lt;string&gt;): Promise&lt;void&gt;

Creates a dialog box for deleting media files. This API uses a promise to return the result. The deleted media files are moved to the trash.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [MediaAssetChangeRequest.deleteAssets](arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#deleteassets11-1) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| uriList | Array&lt;string&gt; | Yes  | URIs of the media files to delete. A maximum of 300 media files can be deleted.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;void&gt;|  Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

If error code 13900012 is returned, follow the instructions provided in [Before You Start](../../media/medialibrary/photoAccessHelper-preparation.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 13900012 | Permission denied. Possible causes:<br>1. Not have ohos.permission.WRITE_IMAGEVIDEO.<br>2. User deny. |
| 13900020 | Invalid parameter. Possible causes:<br>1. The context parameter is invalid, failed to convert to AbilityContext.<br>2. Failed to create the dialog, system internal error, please retry. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The delete operation failed, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>2. The uriList parameter contains invalid URIs, please check if each URI is a valid file URI obtained from a valid query result.<br>3. The UI extension component reported an error, please retry. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createDeleteRequestDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> | undefined = undefined;
  try {
    fetchResult = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('asset not exist');
      return;
    }
    await phAccessHelper.createDeleteRequest([asset.uri]);
    console.info('createDeleteRequest successfully');
  } catch (err) {
    console.error(`createDeleteRequest failed with error: ${err.code}, ${err.message}`);
  } finally {
    // Release resources after use.
    fetchResult?.close();
  }
}
```

## getRecentPhotoInfo<sup>20+</sup>

getRecentPhotoInfo(options?: RecentPhotoOptions): Promise\<RecentPhotoInfo>

Obtains the information about the recent image or video when the application uses the **RecentPhotoComponent** to view recent images or videos. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type   | Mandatory| Description                      |
| ------- | ------- | ---- | -------------------------- |
| options | [RecentPhotoOptions](arkts-apis-photoAccessHelper-class.md#recentphotooptions20) | No  | Options for retrieving the recent image or video. If this parameter is not specified, the latest image is retrieved according to the creation time.<br>If this parameter is specified, it must match the **options** configuration in the **RecentPhotoComponent**. Otherwise, there may be discrepancies where the API finds a recent image or video but the component does not.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise\<[RecentPhotoInfo](arkts-apis-photoAccessHelper-class.md#recentphotoinfo20)>| Promise used to return the information about the recent image or video.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { photoAccessHelper, PhotoSource, RecentPhotoOptions} from '@kit.MediaLibraryKit';

async function example(context: Context) {
  console.info('getRecentPhotoInfoDemo');
  let phAccessHelper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  let recentPhotoOptions: RecentPhotoOptions = {
    period: 60 * 60,
    MIMEType: photoAccessHelper.PhotoViewMIMETypes.IMAGE_VIDEO_TYPE,
    photoSource: PhotoSource.ALL
  }

  phAccessHelper.getRecentPhotoInfo(recentPhotoOptions).then((recentPhotoInfo) => {
    console.info('getRecentPhotoInfo success, recentPhotoInfo is ' + JSON.stringify(recentPhotoInfo));
  }).catch((err: BusinessError) => {
    console.error(`getRecentPhotoInfo failed with error: ${err.code}, ${err.message}`);
  });
}
```

## getAlbumIdByLpath<sup>22+</sup>

getAlbumIdByLpath(lpath: string): Promise&lt;number&gt;

Obtains the album ID in the media library based on the album's virtual path. This API uses a promise to return the result.

This API supports the following albums: camera application album (**/DCIM/Camera**), screenshot application album (**/Pictures/Screenshots**), and screen recording application album (**/Pictures/Screenrecords**).

​**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type   | Mandatory| Description                      |
| ------- | ------- | ---- | -------------------------- |
| lpath | string | Yes| Virtual path of the album. The value can contain a maximum of 255 characters.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;number&gt; | Promise used to return the album ID.|

**Error codes**

For details about the error codes, see [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 23800151 | Invalid parameter. Possible causes:<br>1. The number of parameters is not 1.<br>2. The value is not a string or the string fails to be read.<br>3. The lpath is an empty string or its length exceeds the maximum limit <br>(255).<br>4. The lpath is not in the allowed list of MEDIA_DIRS (excluding /DCIM/Camera, /Pictures/Screenshots, and /Pictures/Screenrecords).<br>5. The IPC call returns a server error code. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. System internal error, failed to create boolean value, please retry.<br>2. The IPC call returns a server error code.<br>3. Failed to initialize error Field / Failed to initialize data Field. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAlbumIdByLpath');

  try {
      let albumId: number = await phAccessHelper.getAlbumIdByLpath('/DCIM/Camera');
      console.info('requestFile:: albumId: ', albumId);

      console.info('getAlbumIdByLpath completed.');
      console.info(`albumId : ${albumId}`);
    } catch (err) {
      console.error(`getAlbumIdByLpath failed: ${err.code}, ${err.message}`);
    }
}
```

## onSinglePhotoChange<sup>23+</sup> 

onSinglePhotoChange(asset: PhotoAsset, callback: Callback&lt;PhotoAssetChangeInfos&gt;): void

Registers a listener for changes of a single common asset. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| asset | PhotoAsset | Yes| Asset to be listened for. After the registration is complete, any change to the media assets is returned through the callback.|
| callback  | Callback&lt;[PhotoAssetChangeInfos](arkts-apis-photoAccessHelper-i.md#photoassetchangeinfos20)&gt; | Yes| Callback used to return the media asset information after change, which is [PhotoAssetChangeInfos](arkts-apis-photoAccessHelper-i.md#photoassetchangeinfos20).<br>**NOTE**<br>This API can be used to register multiple different callbacks.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | Invalid parameter. Possible causes:<br>1. One or two parameters are required.<br>2. Invalid parameter.<br>3. The first parameter is not an object or the second parameter is not a function.<br>4. The object is not a valid instance to get asset object.<br>5. The PhotoAsset is not a valid PhotoAsset object.<br>6. Check whether it is a hidden or recycled album.<br>7. Check whether it is not a MEDIA_TYPE_IMAGE or MEDIA_TYPE_VIDEO.<br>8. Ordinary assets invalid.<br>9. Registration has reached the limit.<br>10. Failed to create a reference for the callback.<br>11. The listener for this resource has been registered with the same callback.<br>12. Failed to get photo asset from parameter.<br>13. Failed to get file asset instance.<br>14. Failed to get fileId from photo asset. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Data service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is properly initialized and retry<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}

// After obtaining albums and assets, register a listener for changes to a single asset to demonstrate how to use onSinglePhotoChange.
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // Register onCallback1.
    phAccessHelper.onSinglePhotoChange(asset, onCallback1);
    // Register onCallback2.
    phAccessHelper.onSinglePhotoChange(asset, onCallback2);
  } catch (error) {
    console.error('onSinglePhotoChangeDemo failed, errCode is', error);
  }
}
```

## offSinglePhotoChange<sup>23+</sup> 

offSinglePhotoChange(asset?: PhotoAsset, callback?: Callback&lt;PhotoAssetChangeInfos&gt;): void

Unregisters the listener for a single asset. Note the following:

1. If no parameter is specified, all listeners for the single assets are unregistered.

2. If **asset** is specified but **callback** is not specified, all callback listeners of the **asset** are unregistered.

3. If both **asset** and **callback** are specified, only the specified callback listener is unregistered.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| asset | PhotoAsset | No| Asset for which the listener is canceled. After the unregistration is complete, any change to the **asset** is no longer returned through the **callback**. If this parameter is not specified, all listeners for a single asset are unregistered.|
| callback  | Callback&lt;[PhotoAssetChangeInfos](arkts-apis-photoAccessHelper-i.md#photoassetchangeinfos20)&gt; | No| Callback used for the unregistration. If this parameter is not specified, all callbacks of the **asset** parameter are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | Invalid parameter. Possible causes:<br>1. The object is not a valid instance.<br>2. The parameter type is invalid.<br>3. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Data service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is properly initialized and retry<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback3 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback3 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}

// After obtaining albums and assets, register a listener for changes to a single asset and demonstrate how to cancel the listener in different ways.
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // Register onCallback1.
    phAccessHelper.onSinglePhotoChange(asset, onCallback1);
    // Register onCallback2.
    phAccessHelper.onSinglePhotoChange(asset, onCallback2);
    // Register onCallback3.
    phAccessHelper.onSinglePhotoChange(asset, onCallback3);

    // Unregister onCallback1.
    phAccessHelper.offSinglePhotoChange(asset, onCallback1);
    // Unregister all callbacks of the asset.
    phAccessHelper.offSinglePhotoChange(asset);
    // Unregister all listeners of the singlePhotoAssetChange type.
    phAccessHelper.offSinglePhotoChange();
  } catch (error) {
    console.error('offSinglePhotoChangeDemo failed, errCode is', error);
  }
}
```

## onSinglePhotoAlbumChange<sup>23+</sup> 

onSinglePhotoAlbumChange(album: Album, callback: Callback&lt;AlbumChangeInfos&gt;): void

Registers a listener for changes of a single common asset. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| album | Album | Yes| Album to be listened for. After the registration is complete, any change to the albums is returned through the callback.|
| callback  | Callback&lt;[AlbumChangeInfos](arkts-apis-photoAccessHelper-i.md#albumchangeinfos20)&gt; | Yes| Callback used to return the album information after change, which is [PhotoAssetChangeInfos](arkts-apis-photoAccessHelper-i.md#photoassetchangeinfos20).<br>**NOTE**<br>This API can be used to register multiple different callbacks.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | Invalid parameter. Possible causes:<br>1. One or two parameters are required.<br>2. Invalid parameter.<br>3. Album object is not a valid object.<br>4. The PhotoAsset is not a valid PhotoAsset object.<br>5. Check whether it is a hidden or recycled album.<br>6. Ordinary album invalid.<br>7. Failed to get URI from photo album.<br>8. Registration has reached the limit (>= 50).<br>9. Failed to create a reference for the callback.<br>10. The listener for this resource has been registered with the same callback. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Data service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is properly initialized and retry<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}

// After obtaining albums, register a listener for changes to a single album to demonstrate how to use onSinglePhotoAlbumChange.
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoAlbumChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // Register onCallback1.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback1);
    // Register onCallback2.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback2);
  } catch (error) {
    console.error('onSinglePhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## offSinglePhotoAlbumChange<sup>23+</sup> 

offSinglePhotoAlbumChange(album?: Album, callback?: Callback&lt;AlbumChangeInfos&gt;): void

Unregisters a listener for a single album. Note the following:

1. If no parameter is specified, all listeners for the single albums are unregistered.

2. If **album** is specified but **callback** is not specified, all callback listeners of the album are unregistered.

3. If both **album** and **callback** are specified, only the specified callback listener is unregistered.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| album | Album | No| Album for which the listener is unregistered. After the unregistration is complete, any change to the album is no longer returned through the callback.|
| callback  | Callback&lt;[AlbumChangeInfos](arkts-apis-photoAccessHelper-i.md#albumchangeinfos20)&gt; | No| Callback used for the unregistration. If this parameter is not specified, all callbacks of the **album** parameter are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | Invalid parameter. Possible causes:<br>1. One or two parameters are required.<br>2. Invalid parameter.<br>3. The first parameter is not an object or the second parameter is not a function.<br>4. Object is not a valid object.<br>5. Album object is not a valid object.<br>6. Ordinary album invalid.<br>7. Failed to create callback reference.<br>8. No observer has ever been registered.<br>9. Observer list is empty. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Data service initialization failed, possible causes: <br>(1) Database exception; <br>(2) IPC timeout. Please check if the context is properly initialized and retry<br>2. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}
let onCallback3 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback3 success, changeData: ' + JSON.stringify(changeData));
  // Operations performed when the callback is triggered.
}

// After obtaining albums, register a listener for changes to a single album and demonstrate how to cancel the listener in different ways.
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onSinglePhotoChangeDemo.');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();

    if (albumFetchResult.isAfterLast()) {
      console.error('lack of album to be moved into');
      return;
    }
    // Register onCallback1.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback1);
    // Register onCallback2.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback2);
    // Register onCallback3.
    phAccessHelper.onSinglePhotoAlbumChange(album, onCallback3);

    // Unregister onCallback1.
    phAccessHelper.offSinglePhotoAlbumChange(album, onCallback1);
    // Unregister all callbacks of the album.
    phAccessHelper.offSinglePhotoAlbumChange(album);
    // Unregister all listeners of the singlePhotoAlbumChange type.
    phAccessHelper.offSinglePhotoAlbumChange();
  } catch (error) {
    console.error('offSinglePhotoAlbumChangeDemo failed, errCode is', error);
  }
}
```

## setAssetCompatibleCapability<sup>24+</sup>

setAssetCompatibleCapability(capability: AssetCompatibleCapability): Promise\<void>

Sets the asset compatibility capability. The system performs compatibility processing on special assets (such as high-resolution assets). If you want to obtain the original assets, you need to register the compatibility capability with the system.

​**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type   | Mandatory| Description                      |
| ------- | ------- | ---- | -------------------------- |
| capability | [AssetCompatibleCapability](arkts-apis-photoAccessHelper-i.md#assetcompatiblecapability24) | Yes  | Asset compatibility capability.|


**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 23800151 | Invalid parameter. Possible causes:<br>1. The number of parameters is invalid, expected 1 or 2 parameters.<br>2. The bundleName parameter must be a non-empty string.<br>3. The config parameter must be an object.<br>4. The supportedHighResolution attribute must be a boolean.<br>5. The supportedMimeType attribute must be an array of strings.<br>6. The supportedMimeType array contains unsupported MIME types, only image/jpeg and image/png are supported.<br>7. The supportedMimeTypes array size exceeds the limit (max 2 after deduplication).<br>8. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |
| 23800301 | MediaLibrary inner fail. Possible causes:<br>1. Parameter is not an array type.<br>2. Failed to get array length.<br>3. Server returned an invalid argument error. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let capability : photoAccessHelper.AssetCompatibleCapability = {
        supportedHighResolution : true,
    };
    await phAccessHelper.setAssetCompatibleCapability(capability);
  } catch (error) {
    console.error('failed to setAssetCompatibleCapability err', error);
  }
}
```

## checkPhotoUrisReadPermission

checkPhotoUrisReadPermission(uris: string[]): Promise&lt;Map&lt;string, MediaAssetPermissionState&gt;&gt;

Checks whether the application has the read permission on the asset corresponding to the specified URI and whether the asset exists. This API uses a promise to return the result.

**Since**: 26.0.0

​**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name | Type   | Mandatory| Description                      |
| ------- | ------- | ---- | -------------------------- |
| uris | string[] | Yes  | Array of URIs to be checked. A maximum of 500 URIs can be checked at a time.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;Map&lt;string, [MediaAssetPermissionState](arkts-apis-photoAccessHelper-e.md#mediaassetpermissionstate)&gt;&gt; | Promise used to return the key-value pair set of URIs and **MediaAssetPermissionState**.|

**Error codes**

For details about the error codes, see [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 23800151 | Scenario-specific parameters are incorrect. Possible causes are as follows: 1. The length of the input parameter queue is greater than 500. 2. The input parameter is null or undefined.|
| 23800301 | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. Database corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('checkPhotoUrisReadPermissionDemo');

  try {
    let uris: string[] = [
      'file://fileUriDemo1', // The URI here is an example only.
      'file://fileUriDemo2'
    ];
    let permissionMap: Map<string, photoAccessHelper.MediaAssetPermissionState> =
      await phAccessHelper.checkPhotoUrisReadPermission(uris);
  } catch (err) {
    const error = err as BusinessError;
    console.error(`checkPhotoUrisReadPermission failed, error: ${error.code}, ${error.message}`);
  }
}
```
## onMediaLibraryAvailability

onMediaLibraryAvailability(callback: Callback&lt;MediaLibraryAvailability&gt;): void

Registers the media library availability status and returns the current availability status and unavailability cause of the media library. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| callback  | Callback&lt;[MediaLibraryAvailability](arkts-apis-photoAccessHelper-i.md#medialibraryavailability)&gt; | Yes  | Callback used to return the availability information of the media library.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800151 | Scenario-specific parameters are incorrect. Possible causes are as follows: 1. The input parameter is null or undefined. |
| 23800301 | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. Database corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
class MediaLibraryExample {
  private helper: photoAccessHelper.PhotoAccessHelper;
  private handleMediaLibraryChange?: (changeData: photoAccessHelper.MediaLibraryAvailability) => void;

  constructor(context: common.Context) {
    this.helper = photoAccessHelper.getPhotoAccessHelper(context);
  }

  onMediaLibraryAvailability = async () => {
    try {
      // Define the callback function for media library availability changes.
      this.handleMediaLibraryChange = (
        changeData: photoAccessHelper.MediaLibraryAvailability
      ) => {
        // Obtain the availability of the media library and the reason why it is unavailable.
        const availabilityStatus = changeData.availabilityStatus;
        const unavailabilityReason = changeData.unavailabilityReason;
        console.info(`Media library status changed: status=${availabilityStatus}, reason=${unavailabilityReason}`);
      };
      // Register a listener for media library availability.
      this.helper.onMediaLibraryAvailability(this.handleMediaLibraryChange);
      console.info('Media library listener registered successfully.');
    } catch (err) {
      console.error(`onMediaLibraryAvailability failed::${(err as BusinessError).code}, ${(err as BusinessError).message} !`);
    }
  };
}
```

## offMediaLibraryAvailability

offMediaLibraryAvailability(callback?: Callback&lt;MediaLibraryAvailability&gt;): void

Unregisters the media library availability status.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                  | Mandatory| Description     |
|-----------|-------------------------|-----------|-----------------|
| callback | Callback&lt;[MediaLibraryAvailability](arkts-apis-photoAccessHelper-i.md#medialibraryavailability)&gt; | No  | Callback used to return the callback listener specified by [onMediaLibraryAvailability](#onmedialibraryavailability). If this parameter is left empty, all listeners for media library availability changes are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Media Library Error Codes](errorcode-medialibrary.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 23800301 | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. Database corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
class MediaLibraryExample {
  private helper: photoAccessHelper.PhotoAccessHelper;
  private handleMediaLibraryChange?: (changeData: photoAccessHelper.MediaLibraryAvailability) => void;

  constructor(context: common.Context) {
    this.helper = photoAccessHelper.getPhotoAccessHelper(context);
  }

  offMediaLibraryAvailability = async () => {
    try {
      // Register a listener for the media library availability and then unregister it to demonstrate how to cancel the listener.
      this.helper.onMediaLibraryAvailability(this.handleMediaLibraryChange);
      this.helper.offMediaLibraryAvailability(this.handleMediaLibraryChange);
      console.info('Media library listener unregistered successfully.');
    } catch (err) {
      console.error(`offMediaLibraryAvailability failed::${(err as BusinessError).code}, ${(err as BusinessError).message} !`);
    }
  };
}
```