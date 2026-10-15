# Interface (AbsAlbum)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

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
| changeTime<sup>23+</sup> | number | Yes   | Yes   | Time when the album is changed, in seconds.|

## getAssets

getAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult&lt;PhotoAsset&gt;&gt;): void

Obtains image and video assets. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| options | [FetchOptions](arkts-apis-photoAccessHelper-i.md#fetchoptions) | Yes  | Retrieval options.|
| callback | AsyncCallback&lt;[FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt;&gt; | Yes  | Callback function. If files from the album are obtained successfully, **err** is **undefined**, and **data** is the result set of the obtained image and video data ([FetchResult](arkts-apis-photoAccessHelper-FetchResult.md)). Otherwise, **err** is an error object, and **data** is **undefined**.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. | 
| 201     | Permission denied. <br> Applicable versions: 12+       |
| 13900012     | Permission denied. <br> Applicable versions: 10 to 11        |
| 13900020     | Invalid argument.         |
| 14000011       | System inner fail.         |

**Example**

Create **phAccessHelper** by referring to the [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper) example.

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
| 201     | Permission denied. <br> Applicable versions: 20+       |
| 13900012     | Permission denied. <br> Applicable versions: 10 to 19        |
| 13900020     | Invalid argument.         |
| 14000011       | System inner fail.         |

**Example**

Create **phAccessHelper** by referring to the [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper) example.

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