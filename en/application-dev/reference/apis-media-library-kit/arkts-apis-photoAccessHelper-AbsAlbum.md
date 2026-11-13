# Interface (AbsAlbum)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=d036437fca9f1387f05ed5f1104d3980c50e5643 translatedAt=2026-11-03T07:00:15.601Z pushedAt=2026-11-04T03:11:19.946Z nl=1 -->

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
| albumType | [AlbumType](arkts-apis-photoAccessHelper-e.md#albumtype) | Yes   | No   | Type of the album.   |
| albumSubtype | [AlbumSubtype](arkts-apis-photoAccessHelper-e.md#albumsubtype) | Yes   | No  | Subtype of the album.   |
| albumName | string | No   | No  | Name of the album. System albums are not writable, whereas user albums can be written to.   |
| albumUri | string | Yes   | No   | URI of the album.  |
| count | number | Yes   | No   |  Number of files in the album.|
| coverUri | string | Yes   | No   | URI of the cover file of the album.|
| lpath<sup>23+</sup> | string | Yes   | Yes   | Virtual path of the album.|
| changeTime<sup>23+</sup> | number | Yes    | Yes    | Change time of the album, in seconds. |

## getAssets

getAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult&lt;PhotoAsset&gt;&gt;): void

Obtains image and video assets. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| options | [FetchOptions](arkts-apis-photoAccessHelper-i.md#fetchoptions) | Yes  | Retrieval options.|
| callback | AsyncCallback&lt;[FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt;&gt; | Yes | Callback invoked to return the result. If the files in the album are obtained successfully, err is undefined and data is the [FetchResult](arkts-apis-photoAccessHelper-FetchResult.md) object that contains the image and video data. If the operation fails, err is an error object and data is undefined. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API.  <br> Applicable versions: 12 and later  |
| 13900012     | Permission denied. <br> Applicable versions: 10-11         |
| 13900020 | Invalid parameter. Possible causes:<br>1. The predicate contains invalid statements, the key must be a valid PhotoKeys value.<br>2. The fetchColumns contain invalid column names, the column must be a valid PhotoKeys value.<br>3. The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>4. The album instance is invalid.<br>5. The album ID is invalid.<br>6. The album type or subtype is not a valid enum value.<br>7. The combination of album type and subtype is invalid. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. Database query failed, possible causes: <br>(1) Database connection exception; <br>(2) Database operation error. Please retry and check logs.<br>2. IPC call failed, the server returned an error code.<br>3. Both sandbox query and IPC query failed to retrieve data.<br>4. Failed to create the query result, possible causes: <br>(1) Memory insufficient; <br>(2) IPC timeout. Please retry.<br>5. FetchOptions parsing failed, please check if the parameter is a valid FetchOptions type.<br>6. Parameter parsing failed, please check parameter types and count. |

**Example**

Refer to the example in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper) to create phAccessHelper.

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumGetAssetsDemoCallback');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  album.getAssets(fetchOption, (err, albumFetchResult) => {
    if (!err) {
      console.info('album getAssets successfully, getCount: ' + albumFetchResult.getCount());
    } else {
      console.error(`album getAssets failed with error: ${err.code}, ${err.message}`);
    }
  });
}
```

## getAssets

getAssets(options: FetchOptions): Promise&lt;FetchResult&lt;PhotoAsset&gt;&gt;

Obtains image and video assets. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 20.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| options | [FetchOptions](arkts-apis-photoAccessHelper-i.md#fetchoptions) | Yes  | Retrieval options.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;[FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt;&gt; | Promise used to return the image and video assets obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. <br> Applicable versions: 20 and later |
| 13900012     | Permission denied. <br> Applicable versions: 10-19         |
| 13900020 | Invalid parameter. Possible causes:<br>1. The current album object is invalid, the Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>2. The album instance is invalid.<br>3. The album type is invalid, must be a valid AlbumType enum value.<br>4. The object is not a valid instance. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. FetchOptions parsing failed, please check if the parameter is a valid FetchOptions type.<br>2. Parameter parsing failed, please check parameter types and count.<br>3. Database query failed, possible causes: <br>(1) Database connection exception; <br>(2) Database operation error. Please retry and check logs.<br>4. Failed to create the query result, possible causes: <br>(1) Memory insufficient; <br>(2) IPC timeout. Please retry.<br>5. Database query returned empty result set in async execution path. |

**Example**

Refer to the example in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper) to create phAccessHelper.

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('albumGetAssetsDemoPromise');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  let album: photoAccessHelper.Album = await albumList.getFirstObject();
  album.getAssets(fetchOption).then((albumFetchResult) => {
    console.info('album getAssets successfully, getCount: ' + albumFetchResult.getCount());
  }).catch((err: BusinessError) => {
    console.error(`album getAssets failed with error: ${err.code}, ${err.message}`);
  });
}
```
