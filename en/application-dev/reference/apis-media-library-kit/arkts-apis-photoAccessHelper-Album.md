# Interface (Album)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=f2c7727dff910038fdcf1b75fb074e51aa470331 translatedAt=2026-11-03T07:01:17.921Z pushedAt=2026-11-04T03:11:19.952Z nl=1 -->

Album inherits from [AbsAlbum](arkts-apis-photoAccessHelper-AbsAlbum.md).

Album provides APIs to manage albums.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## Properties

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name          | Type   | Read-Only  | Optional | Description  |
| ------------ | ------ | ---- | ---- | ------- |
| imageCount<sup>11+</sup> | number | Yes  | Yes  | Number of images in the album.|
| videoCount<sup>11+</sup> | number | Yes  | Yes  | Number of videos in the album.|

## commitModify

commitModify(callback: AsyncCallback&lt;void&gt;): void

Updates album attributes to the database. This API uses an asynchronous callback.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback function. If the album properties are modified successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).


| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 13900020 | Invalid parameter. Possible causes:<br>1. The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>2. The album is not a user album, only user albums support this operation.<br>3. The album name exceeds the length limit or contains invalid characters.<br>4. The number of parameters is invalid.<br>5. The callback parameter must be of type AsyncCallback&lt;void&gt;. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context.<br>2. The server returned an error during commitModify, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumCommitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  if (albumList === undefined) {
    console.error('albumList is undefined');
    return;
  }
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  if (album === undefined) {
    console.error('album is undefined');
    return;
  }
  album.albumName = 'hello';
  album.commitModify((err) => {
    if (err) {
      console.error(`commitModify failed with error: ${err.code}, ${err.message}`);
    } else {
      console.info('commitModify successfully');
    }
  });
}
```

## commitModify

commitModify(): Promise&lt;void&gt;

Updates album attributes to the database. This API uses a promise.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value**

| Type                 | Description          |
| ------------------- | ------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).


| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 13900020 | Invalid parameter. Possible causes:<br>1. System out of memory, please retry.<br>2. The object is not a valid instance.<br>3. The album is not a user album, only user albums support this operation.<br>4. The album name exceeds the length limit or contains invalid characters.<br>5. The number of parameters is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The context parameter is invalid or not properly initialized, please pass a valid Context obtained from the application context.<br>2. The server returned an error during commitModify, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumCommitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  if (albumList === undefined) {
    console.error('albumList is undefined');
    return;
  }
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  if (album === undefined) {
    console.error('album is undefined');
    return;
  }
  album.albumName = 'hello';
  // Commit the album name change to the database.
  album.commitModify().then(() => {
    console.info('commitModify successfully');
  }).catch((err: BusinessError) => {
    console.error(`commitModify failed with error: ${err.code}, ${err.message}`);
  });
}
```

## addAssets<sup>(deprecated)</sup>

addAssets(assets: Array&lt;PhotoAsset&gt;, callback: AsyncCallback&lt;void&gt;): void

Adds images or videos to a user album. Before calling this API, ensure that the album object has been obtained and the resource files are ready. This API uses an asynchronous callback.

> **NOTE** 
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [MediaAlbumChangeRequest.addAssets](arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md#addassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt; | Yes | Array of images or videos to be added to the album. |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback function. If an image or video is added successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).


| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 13900020 | Invalid parameter. Possible causes:<br>1. System out of memory, please retry.<br>2. The object is not a valid instance.<br>3. The album is not a user album, only user albums support this operation.<br>4. The assets parameter must be an array.<br>5. The assets array is empty.<br>6. The array element must be a valid PhotoAsset object.<br>7. The number of parameters is invalid.<br>8. The array element is not a valid object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. System memory insufficient, please retry.<br>2. The assets array contains elements with invalid file type, each element must be IMAGE or VIDEO type.<br>3. IPC call failed, please retry and check logs.<br>4. The assets array contains elements that are not valid PhotoAsset objects.<br>5. Server returned a non-permission error code.<br>6. Failed to update album count, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>7. The assets parameter must be an array.<br>8. The assets array is empty.<br>9. The array element must be a valid PhotoAsset object. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('addAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('addAssetsDemoCallback asset is undefined');
      return;
    }
    album.addAssets([asset], (err) => {
      if (!err) {
        console.info('album addAssets successfully');
      } else {
        console.error(`album addAssets failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`addAssetsDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## addAssets<sup>(deprecated)</sup>

addAssets(assets: Array&lt;PhotoAsset&gt;): Promise&lt;void&gt;

Adds images or videos to a user album. Before calling this API, ensure that the album object has been obtained and the resource files are ready. This API uses a promise.

> **NOTE** 
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [MediaAlbumChangeRequest.addAssets](arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md#addassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt; | Yes  | Array of the image and video assets to add.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
|Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).


| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 13900020 | Invalid parameter. Possible causes:<br>1. The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>2. The album instance is invalid.<br>3. The album is not a user album, only user albums support addAssets.<br>4. The assets parameter must be an array.<br>5. The assets array is empty.<br>6. The array element must be a valid PhotoAsset object.<br>7. The number of parameters is invalid, expected at least 1 parameter.<br>8. The array element is not a valid PhotoAsset object. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The assets array contains no valid photo or video resources.<br>2. IPC call returned a non-permission error code.<br>3. Batch insert failed, database operation error, please retry.<br>4. Failed to update album count, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>5. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>6. The assets parameter must be an array.<br>7. The assets array is empty.<br>8. The array element must be a valid PhotoAsset object. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('addAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('addAssetsDemoPromise asset is undefined');
      return;
    }
    // Add assets to the album.
    album.addAssets([asset]).then(() => {
      console.info('album addAssets successfully');
    }).catch((err: BusinessError) => {
      console.error(`album addAssets failed with error: ${err.code}, ${err.message}`);
    });
  } catch (err) {
    console.error(`addAssetsDemoPromise failed with error: ${err.code}, ${err.message}`);
  }
}
```

## removeAssets<sup>(deprecated)</sup>

removeAssets(assets: Array&lt;PhotoAsset&gt;, callback: AsyncCallback&lt;void&gt;): void

Removes images or videos from a user album. Before calling this API, ensure that the album object has been obtained and the resource files are ready. This API uses an asynchronous callback.

> **NOTE** 
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [MediaAlbumChangeRequest.removeAssets](arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md#removeassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt; | Yes  | Array of the image and video assets to remove.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback function. If an image or video is removed successfully, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).


| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 13900020 | Invalid parameter. Possible causes:<br>1. The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>2. The album instance is invalid.<br>3. The album is not a user album, only user albums support removeAssets.<br>4. The assets parameter must be an array.<br>5. The assets array is empty.<br>6. The array element must be a valid PhotoAsset object.<br>7. The object is not a valid instance.<br>8. The array element is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The assets array is empty or contains no valid PhotoAsset elements.<br>2. IPC call returned a non-permission error code.<br>3. The assets array contains elements that are not valid PhotoAsset objects.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>5. The assets parameter must be an array.<br>6. The assets array is empty.<br>7. The array element must be a valid PhotoAsset object. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('removeAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('removeAssetsDemoCallback asset is undefined');
      return;
    }
    album.removeAssets([asset], (err) => {
      if (!err) {
        console.info('album removeAssets successfully');
      } else {
        console.error(`album removeAssets failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`removeAssetsDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## removeAssets<sup>(deprecated)</sup>

removeAssets(assets: Array&lt;PhotoAsset&gt;): Promise&lt;void&gt;

Removes images or videos from a user album. Before calling this API, ensure that the album object has been obtained and the resource files are ready. This API uses a promise.

> **NOTE** 
>
> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [MediaAlbumChangeRequest.removeAssets](arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md#removeassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt; | Yes  | Array of the image and video assets to remove.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
|Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).


| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 13900020 | Invalid parameter. Possible causes:<br>1. The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>2. The album instance is invalid.<br>3. The album is not a user album, only user albums support removeAssets.<br>4. The assets parameter must be an array.<br>5. The assets array is empty.<br>6. The array element must be a valid PhotoAsset object.<br>7. The object is not a valid instance.<br>8. The array element is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The assets array is empty or contains no valid PhotoAsset elements.<br>2. IPC call returned a non-permission error code.<br>3. The assets array contains elements that are not valid PhotoAsset objects.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs.<br>5. The assets parameter must be an array.<br>6. The assets array is empty.<br>7. The array element must be a valid PhotoAsset object. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('removeAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    if (album === undefined) {
      console.error('removeAssetsPromise albums is undefined');
      return;
    }
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('removeAssetsPromise asset is undefined');
      return;
    }
    // Remove assets from the album.
    album.removeAssets([asset]).then(() => {
      console.info('album removeAssets successfully');
    }).catch((err: BusinessError) => {
      console.error(`album removeAssets failed with error: ${err.code}, ${err.message}`);
    });
  } catch (err) {
    console.error(`removeAssetsDemoPromise failed with error: ${err.code}, ${err.message}`);
  }
}
```
