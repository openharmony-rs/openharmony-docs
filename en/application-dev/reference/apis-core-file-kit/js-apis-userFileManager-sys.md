# @ohos.filemanagement.userFileManager (User Data Management) (System API)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45f412f2eeef2879a064ea41a4368af91265b2cb translatedAt=2026-11-10T05:27:25.056Z pushedAt=2026-11-10T07:45:55.824Z nl=1 -->

The **userFileManager** module provides user data management capabilities, including accessing and modifying user media data.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This module is a system API.
> - This module is deprecated since API version 26.0.0. You are advised to use [@ohos.file.photoAccessHelper (Album Management Module) (System API)](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md) instead.

## Modules to Import

```ts
import userFileManager from '@ohos.filemanagement.userFileManager';
```

## userFileManager.getUserFileMgr<sup>(deprecated)</sup>

getUserFileMgr(context: Context): UserFileManager

Obtains a **UserFileManager** instance. This instance can be used to access and modify user media data (such as audio and video assets, images, and documents).

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.getPhotoAccessHelper](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#photoaccesshelpergetphotoaccesshelper19) instead.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name | Type   | Mandatory| Description                      |
| ------- | ------- | ---- | -------------------------- |
| context | [Context](../apis-ability-kit/js-apis-inner-app-context.md) | Yes  | Context of the ability instance.|

**Return value**

| Type                           | Description   |
| ----------------------------- | :---- |
| [UserFileManager](#userfilemanager) | **UserFileManager** instance obtained.|

**Example**

```ts
// The userFileManager instance obtained is a global object. It is used by default in subsequent operations. If the code snippet is not added, an error will be reported indicating that mgr is not defined.
// Obtain the context from the component and ensure that the return value of this.getUiContext().getHostContext() is UIAbilityContext.
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button("example").onClick(async () => {
        let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
        let mgr = userFileManager.getUserFileMgr(context);
      }).width('100%')
    }
    .height('90%')
  }
}
```

## UserFileManager

### getPhotoAssets<sup>(deprecated)</sup>

getPhotoAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult&lt;FileAsset&gt;&gt;): void

Obtains image and video assets. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAccessHelper.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| options  | [FetchOptions](#fetchoptionsdeprecated)        | Yes   | Image and video retrieval options.              |
| callback |  AsyncCallback&lt;[FetchResult](#fetchresult)&lt;[FileAsset](#fileassetdeprecated)&gt;&gt; | Yes   | Callback used to return the image and video retrieval result set. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getPhotoAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };

  mgr.getPhotoAssets(fetchOptions, async (err, fetchResult) => {
    if (fetchResult != undefined) {
      console.info('fetchResult success');
      let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
      if (fileAsset != undefined) {
        console.info('fileAsset.displayName : ' + fileAsset.displayName);
      }
    } else {
      console.error('fetchResult fail' + err);
    }
  });
}
```

### getPhotoAssets<sup>(deprecated)</sup>

getPhotoAssets(options: FetchOptions): Promise&lt;FetchResult&lt;FileAsset&gt;&gt;

Obtains image and video assets. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAccessHelper.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getassets) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name | Type               | Mandatory| Description            |
| ------- | ------------------- | ---- | ---------------- |
| options | [FetchOptions](#fetchoptionsdeprecated)   | Yes   | Image and video retrieval options.     |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FetchResult](#fetchresult)&lt;[FileAsset](#fileassetdeprecated)&gt;&gt; | Promise object, used to return the image and video data result set. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getPhotoAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    if (fetchResult != undefined) {
      console.info('fetchResult success');
      let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
      if (fileAsset != undefined) {
        console.info('fileAsset.displayName :' + fileAsset.displayName);
      }
    }
  } catch (err) {
    console.error('getPhotoAssets failed, message = ', err);
  }
}
```
### createPhotoAsset<sup>(deprecated)</sup>

createPhotoAsset(displayName: string, albumUri: string, callback: AsyncCallback&lt;FileAsset&gt;): void

Creates an image or video asset with the specified file name and URI. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAccessHelper.createAsset](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#createasset) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| displayName  | string        | Yes  | File name of the image or video to create.             |
| albumUri  | string        | Yes  | URI of the album where the image or video is located.             |
| callback | AsyncCallback&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | callback returns the created image and video result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type displayName or albumUri is not string.         |
| 14000001   | if type displayName invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('createPhotoAssetDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: userFileManager.AlbumFetchOptions = {
    predicates: predicates
  };
  let albums: userFileManager.FetchResult<userFileManager.Album> = await mgr.getPhotoAlbums(fetchOptions);
  let album: userFileManager.Album = await albums.getFirstObject();
  let testFileName: string = 'testFile' + Date.now() + '.jpg';
  mgr.createPhotoAsset(testFileName, album.albumUri, (err, fileAsset) => {
    if (fileAsset != undefined) {
      console.info('createPhotoAsset file displayName' + fileAsset.displayName);
      console.info('createPhotoAsset successfully');
    } else {
      console.error('createPhotoAsset failed, message = ', err);
    }
  });
}
```

### createPhotoAsset<sup>(deprecated)</sup>

createPhotoAsset(displayName: string, callback: AsyncCallback&lt;FileAsset&gt;): void

Creates an image or video asset with the specified file name. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAccessHelper.createAsset](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#createasset) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| displayName  | string        | Yes  | File name of the image or video to create.             |
| callback | AsyncCallback&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | callback returns the created image and video result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type displayName is not string.         |
| 14000001   | if type displayName invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('createPhotoAssetDemo');
  let testFileName: string = 'testFile' + Date.now() + '.jpg';
  mgr.createPhotoAsset(testFileName, (err, fileAsset) => {
    if (fileAsset != undefined) {
      console.info('createPhotoAsset file displayName' + fileAsset.displayName);
      console.info('createPhotoAsset successfully');
    } else {
      console.error('createPhotoAsset failed, message = ', err);
    }
  });
}
```

### createPhotoAsset<sup>(deprecated)</sup>

createPhotoAsset(displayName: string, albumUri?: string): Promise&lt;FileAsset&gt;

Creates an image or video asset with the specified file name and album URI. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAccessHelper.createAsset](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#createasset) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| displayName  | string        | Yes  | File name of the image or video to create.             |
| albumUri  | string        | No  | URI of the album where the image or video is located.             |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FileAsset](#fileassetdeprecated)&gt; | Promise object, used to return the created image and video result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type displayName or albumUri is not string.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('createPhotoAssetDemo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let fileAsset: userFileManager.FileAsset = await mgr.createPhotoAsset(testFileName);
    console.info('createPhotoAsset file displayName' + fileAsset.displayName);
    console.info('createPhotoAsset successfully');
  } catch (err) {
    console.error('createPhotoAsset failed, message = ', err);
  }
}
```

### createPhotoAsset<sup>(deprecated)</sup>

createPhotoAsset(displayName: string, createOption: PhotoCreateOptions, callback: AsyncCallback&lt;FileAsset&gt;): void

Creates an image or video asset with the specified file name and options. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAccessHelper.createAsset](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#createasset) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| displayName  | string        | Yes  | File name of the image or video to create.             |
| createOption  | [PhotoCreateOptions](#photocreateoptionsdeprecated)        | Yes   | Defines the options for creating an image or video asset.              |
| callback |  AsyncCallback&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes   | callback returns the created image and video result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type displayName is not string.         |
| 14000001   | if type displayName invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('createPhotoAssetDemo');
  let testFileName: string = 'testFile' + Date.now() + '.jpg';
  let createOption: userFileManager.PhotoCreateOptions = {
    subType: userFileManager.PhotoSubType.DEFAULT
  }
  mgr.createPhotoAsset(testFileName, createOption, (err, fileAsset) => {
    if (fileAsset != undefined) {
      console.info('createPhotoAsset file displayName' + fileAsset.displayName);
      console.info('createPhotoAsset successfully');
    } else {
      console.error('createPhotoAsset failed, message = ', err);
    }
  });
}
```

### createPhotoAsset<sup>(deprecated)</sup>

createPhotoAsset(displayName: string, createOption: PhotoCreateOptions): Promise&lt;FileAsset&gt;

Creates an image or video asset with the specified file name and options. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAccessHelper.createAsset](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#createasset) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| displayName  | string        | Yes  | File name of the image or video to create.             |
| createOption  |  [PhotoCreateOptions](#photocreateoptionsdeprecated)       | Yes   | Defines the options for creating an image or video asset.              |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FileAsset](#fileassetdeprecated)&gt; | Promise object, used to return the created image and video result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type displayName is not string.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('createPhotoAssetDemo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let createOption: userFileManager.PhotoCreateOptions = {
      subType: userFileManager.PhotoSubType.DEFAULT
    }
    let fileAsset: userFileManager.FileAsset = await mgr.createPhotoAsset(testFileName, createOption);
    console.info('createPhotoAsset file displayName' + fileAsset.displayName);
    console.info('createPhotoAsset successfully');
  } catch (err) {
    console.error('createPhotoAsset failed, message = ', err);
  }
}
```

### createAudioAsset<sup>(deprecated)</sup>

createAudioAsset(displayName: string, callback: AsyncCallback&lt;FileAsset&gt;): void

Creates an audio asset. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. Recommended to use [picker.AudioViewPicker](js-apis-file-picker.md#audioviewpicker) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_AUDIO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| displayName  | string        | Yes  | File name of the audio asset to create.             |
| callback | AsyncCallback&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | Callback used to return the created audio asset result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type displayName is not string.         |
| 14000001   | if type displayName invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('createAudioAssetDemo');
  let testFileName: string = 'testFile' + Date.now() + '.mp3';
  mgr.createAudioAsset(testFileName, (err, fileAsset) => {
    if (fileAsset != undefined) {
      console.info('createAudioAsset file displayName' + fileAsset.displayName);
      console.info('createAudioAsset successfully');
    } else {
      console.error('createAudioAsset failed, message = ', err);
    }
  });
}
```

### createAudioAsset<sup>(deprecated)</sup>

createAudioAsset(displayName: string): Promise&lt;FileAsset&gt;

Creates an audio asset. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [picker.AudioViewPicker](js-apis-file-picker.md#audioviewpicker) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_AUDIO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| displayName  | string        | Yes  | File name of the audio asset to create.             |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FileAsset](#fileassetdeprecated)&gt; | Promise object, returns the created audio asset result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type displayName is not string.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('createAudioAssetDemo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.mp3';
    let fileAsset: userFileManager.FileAsset = await mgr.createAudioAsset(testFileName);
    console.info('createAudioAsset file displayName' + fileAsset.displayName);
    console.info('createAudioAsset successfully');
  } catch (err) {
    console.error('createAudioAsset failed, message = ', err);
  }
}
```

### createAlbum<sup>(deprecated)</sup>

createAlbum(name: string, callback: AsyncCallback&lt;Album&gt;): void

Creates an album. This API uses an asynchronous callback to return the result.

The album name must meet the following requirements:
- The album name is a string of 1 to 255 characters.
- The album name cannot contain any of the following characters:<br> . .. \ / : * ? " ' ` < > | { } [ ]
- The album name is case-insensitive.
- Duplicate album names are not allowed.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAlbumChangeRequest.createAlbumRequest](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#createalbumrequest11) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| name  | string         | Yes  | Name of the album to create.             |
| callback | AsyncCallback&lt;[Album](#albumdeprecated)&gt; | Yes | Callback used to return the created album instance. |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('createAlbumDemo');
  let albumName: string = 'newAlbumName' + new Date().getTime();
  mgr.createAlbum(albumName, (err, album) => {
    if (err) {
      console.error('createAlbumCallback failed with err: ' + err);
      return;
    }
    console.info('createAlbumCallback successfully, album: ' + album.albumName + ' album uri: ' + album.albumUri);
  });
}
```

### createAlbum<sup>(deprecated)</sup>

createAlbum(name: string): Promise&lt;Album&gt;

Creates an album. This API uses a promise to return the result.

The album name must meet the following requirements:
- The album name is a string of 1 to 255 characters.
- The album name cannot contain any of the following characters:<br> . .. \ / : * ? " ' ` < > | { } [ ]
- The album name is case-insensitive.
- Duplicate album names are not allowed.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAlbumChangeRequest.createAlbumRequest](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#createalbumrequest11) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| name  | string         | Yes  | Name of the album to create.             |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[Album](#albumdeprecated)&gt; | Promise object, returns the created album instance. |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('createAlbumDemo');
  let albumName: string  = 'newAlbumName' + new Date().getTime();
  mgr.createAlbum(albumName).then((album) => {
    console.info('createAlbumPromise successfully, album: ' + album.albumName + ' album uri: ' + album.albumUri);
  }).catch((err: BusinessError) => {
    console.error('createAlbumPromise failed with err: ' + err);
  });
}
```

### deleteAlbums<sup>(deprecated)</sup>

deleteAlbums(albums: Array&lt;Album&gt;, callback: AsyncCallback&lt;void&gt;): void

Deletes user albums. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAlbumChangeRequest.deleteAlbums](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#deletealbums11) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| albums  | Array&lt;[Album](#albumdeprecated)&gt;         | Yes   | Array of albums to be deleted.              |
| callback |  AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  // Delete the album named newAlbumName.
  console.info('deleteAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.USER, userFileManager.AlbumSubType.USER_GENERIC, fetchOptions);
  let album: userFileManager.Album = await fetchResult.getFirstObject();
  mgr.deleteAlbums([album], (err) => {
    if (err) {
      console.error('deletePhotoAlbumsCallback failed with err: ' + err);
      return;
    }
    console.info('deletePhotoAlbumsCallback successfully');
  });
  fetchResult.close();
}
```

### deleteAlbums<sup>(deprecated)</sup>

deleteAlbums(albums: Array&lt;Album&gt;): Promise&lt;void&gt;

Deletes user albums. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAlbumChangeRequest.deleteAlbums](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#deletealbums11) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| albums  |  Array&lt;[Album](#albumdeprecated)&gt;          | Yes   | Array of albums to be deleted.              |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  // Delete the album named newAlbumName.
  console.info('deleteAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.USER, userFileManager.AlbumSubType.USER_GENERIC, fetchOptions);
  let album: userFileManager.Album = await fetchResult.getFirstObject();
  mgr.deleteAlbums([album]).then(() => {
    console.info('deletePhotoAlbumsPromise successfully');
      fetchResult.close();
    }).catch((err: BusinessError) => {
      console.error('deletePhotoAlbumsPromise failed with err: ' + err);
      fetchResult.close();
  });
}
```

### getAlbums<sup>(deprecated)</sup>

getAlbums(type: AlbumType, subType: AlbumSubType, options: FetchOptions, callback: AsyncCallback&lt;FetchResult&lt;Album&gt;&gt;): void

Obtains albums based on the specified options and album type. This API uses an asynchronous callback to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#gethiddenalbums11) to obtain hidden albums.

Before the operation, ensure that the albums to obtain exist.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAccessHelper.getAlbums](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getalbums) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| type  | [AlbumType](#albumtypedeprecated)         | Yes   | Album type.              |
| subType  | [AlbumSubType](#albumsubtypedeprecated)         | Yes   | Album subtype.              |
| options  | [FetchOptions](#fetchoptionsdeprecated)         | Yes   | Fetch options.              |
| callback |  AsyncCallback&lt;[FetchResult](#fetchresult)&lt;[Album](#albumdeprecated)&gt;&gt; | Yes   | Callback used to return the result set of the obtained albums. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOption.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  // Obtain the album named newAlbumName.
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  mgr.getAlbums(userFileManager.AlbumType.USER, userFileManager.AlbumSubType.USER_GENERIC, fetchOptions, async (err, fetchResult) => {
    if (err) {
      console.error('getAlbumsCallback failed with err: ' + err);
      return;
    }
    if (fetchResult == undefined) {
      console.error('getAlbumsCallback fetchResult is undefined');
      return;
    }
    let album: userFileManager.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsCallback successfully, albumName: ' + album.albumName);
    fetchResult.close();
  });
}
```

### getAlbums<sup>(deprecated)</sup>

getAlbums(type: AlbumType, subType: AlbumSubType, callback: AsyncCallback&lt;FetchResult&lt;Album&gt;&gt;): void

Obtains albums by type. This API uses an asynchronous callback to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#gethiddenalbums11) to obtain hidden albums.

Before the operation, ensure that the albums to obtain exist.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAccessHelper.getAlbums](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getalbums) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| type  | [AlbumType](#albumtypedeprecated)         | Yes   | Album type.              |
| subType  | [AlbumSubType](#albumsubtypedeprecated)         | Yes   | Album subtype.              |
| callback |  AsyncCallback&lt;[FetchResult](#fetchresult)&lt;[Album](#albumdeprecated)&gt;&gt; | Yes   | Callback used to return the result set of the obtained albums. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOption.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  // Obtain the system album VIDEO, which is preset by default.
  console.info('getAlbumsDemo');
  mgr.getAlbums(userFileManager.AlbumType.SYSTEM, userFileManager.AlbumSubType.VIDEO, async (err, fetchResult) => {
    if (err) {
      console.error('getAlbumsCallback failed with err: ' + err);
      return;
    }
    if (fetchResult == undefined) {
      console.error('getAlbumsCallback fetchResult is undefined');
      return;
    }
    let album: userFileManager.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsCallback successfully, albumUri: ' + album.albumUri);
    fetchResult.close();
  });
}
```

### getAlbums<sup>(deprecated)</sup>

getAlbums(type: AlbumType, subType: AlbumSubType, options?: FetchOptions): Promise&lt;FetchResult&lt;Album&gt;&gt;

Obtains albums based on the specified options and album type. This API uses a promise to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#gethiddenalbums11) to obtain hidden albums.

Before the operation, ensure that the albums to obtain exist.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAccessHelper.getAlbums](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getalbums) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| type  | [AlbumType](#albumtypedeprecated)         | Yes   | Album type.              |
| subType  | [AlbumSubType](#albumsubtypedeprecated)         | Yes   | Album subtype.              |
| options  | [FetchOptions](#fetchoptionsdeprecated)         | No   |  Retrieval options. If not specified, retrieval is performed based on the album type by default.              |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FetchResult](#fetchresult)&lt;[Album](#albumdeprecated)&gt;&gt; | Promise object, used to return the result set of getting albums. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOption.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  // Obtain the album named newAlbumName.
  console.info('getAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  mgr.getAlbums(userFileManager.AlbumType.USER, userFileManager.AlbumSubType.USER_GENERIC, fetchOptions).then( async (fetchResult) => {
    if (fetchResult == undefined) {
      console.error('getAlbumsPromise fetchResult is undefined');
      return;
    }
    let album: userFileManager.Album = await fetchResult.getFirstObject();
    console.info('getAlbumsPromise successfully, albumName: ' + album.albumName);
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error('getAlbumsPromise failed with err: ' + err);
  });
}
```

### getPhotoAlbums<sup>(deprecated)</sup>

getPhotoAlbums(options: AlbumFetchOptions, callback: AsyncCallback&lt;FetchResult&lt;Album&gt;&gt;): void

Obtains image and video albums. This API uses an asynchronous callback to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#gethiddenalbums11) to obtain hidden albums.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAccessHelper.getAlbums](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getalbums) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| options  | [AlbumFetchOptions](#albumfetchoptionsdeprecated)        | Yes   | Album retrieval options.              |
| callback |  AsyncCallback&lt;[FetchResult](#fetchresult)&lt;[Album](#albumdeprecated)&gt;&gt; | Yes   | Callback returns the album retrieval result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not AlbumFetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getPhotoAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: userFileManager.AlbumFetchOptions = {
    predicates: predicates
  };

  mgr.getPhotoAlbums(albumFetchOptions, (err, fetchResult) => {
    if (fetchResult != undefined) {
      console.info('albums.count = ' + fetchResult.getCount());
      fetchResult.getFirstObject((err, album) => {
        if (album != undefined) {
          console.info('first album.albumName = ' + album.albumName);
        } else {
          console.error('album is undefined, err = ', err);
        }
      });
    } else {
      console.error('getPhotoAlbums fail, message = ', err);
    }
  });
}
```

### getPhotoAlbums<sup>(deprecated)</sup>

getPhotoAlbums(options: AlbumFetchOptions): Promise&lt;FetchResult&lt;Album&gt;&gt;

Obtains albums. This API uses a promise to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#gethiddenalbums11) to obtain hidden albums.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAccessHelper.getAlbums](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getalbums) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| options  | [AlbumFetchOptions](#albumfetchoptionsdeprecated)        | Yes   | Album retrieval options.              |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FetchResult](#fetchresult)&lt;[Album](#albumdeprecated)&gt;&gt; | Promise object, returning the album retrieval result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not AlbumFetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getPhotoAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: userFileManager.AlbumFetchOptions = {
    predicates: predicates
  };
  try {
    let fetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getPhotoAlbums(albumFetchOptions);
    console.info('album.count = ' + fetchResult.getCount());
    const album: userFileManager.Album = await fetchResult.getFirstObject();
    console.info('first album.albumName = ' + album.albumName);
  } catch (err) {
    console.error('getPhotoAlbums fail, message = ' + err);
  }
}
```

### getPrivateAlbum<sup>(deprecated)</sup>

getPrivateAlbum(type: PrivateAlbumType, callback: AsyncCallback&lt;FetchResult&lt;PrivateAlbum&gt;&gt;): void

Obtains the system album. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAccessHelper.getAlbums](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getalbums) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| type  | [PrivateAlbumType](#privatealbumtypedeprecated)        | Yes   | System album type.              |
| callback |  AsyncCallback&lt;[FetchResult](#fetchresult)&lt;[PrivateAlbum](#privatealbumdeprecated)&gt;&gt; | Yes   | Callback returns the album retrieval result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type type is not PrivateAlbumType.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('getPrivateAlbumDemo');
  mgr.getPrivateAlbum(userFileManager.PrivateAlbumType.TYPE_TRASH, async (err, fetchResult) => {
    if (fetchResult != undefined) {
      let trashAlbum: userFileManager.PrivateAlbum = await fetchResult.getFirstObject();
      console.info('first album.albumName = ' + trashAlbum.albumName);
    } else {
      console.error('getPrivateAlbum failed. message = ', err);
    }
  });
}
```

### getPrivateAlbum<sup>(deprecated)</sup>

getPrivateAlbum(type: PrivateAlbumType): Promise&lt;FetchResult&lt;PrivateAlbum&gt;&gt;

Obtains the private album. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAccessHelper.getAlbums](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#getalbums) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| type  | [PrivateAlbumType](#privatealbumtypedeprecated)        | Yes   | System album type.              |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FetchResult](#fetchresult)&lt;[PrivateAlbum](#privatealbumdeprecated)&gt;&gt; | Promise object, returning the album retrieval result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type type is not PrivateAlbumType.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('getPrivateAlbumDemo');
  try {
    let fetchResult: userFileManager.FetchResult<userFileManager.PrivateAlbum> = await mgr.getPrivateAlbum(userFileManager.PrivateAlbumType.TYPE_TRASH);
    let trashAlbum: userFileManager.PrivateAlbum = await fetchResult.getFirstObject();
    console.info('first album.albumName = ' + trashAlbum.albumName);
  } catch (err) {
    console.error('getPrivateAlbum failed. message = ', err);
  }
}
```

### getAudioAssets<sup>(deprecated)</sup>

getAudioAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult&lt;FileAsset&gt;&gt;): void

Obtains audio assets. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [picker.AudioViewPicker](js-apis-file-picker.md#audioviewpicker) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_AUDIO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| options  | [FetchOptions](#fetchoptionsdeprecated)        | Yes   | Fetch options.              |
| callback |  AsyncCallback&lt;[FetchResult](#fetchresult)&lt;[FileAsset](#fileassetdeprecated)&gt;&gt; | Yes   | Callback used to return the audio retrieval result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getAudioAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };

  mgr.getAudioAssets(fetchOptions, async (err, fetchResult) => {
    if (fetchResult != undefined) {
      console.info('fetchFileResult success');
      let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
      if (fileAsset != undefined) {
        console.info('fileAsset.displayName :' + fileAsset.displayName);
      }
    } else {
      console.error('fetchFileResult fail' + err);
    }
  });
}
```

### getAudioAssets<sup>(deprecated)</sup>

getAudioAssets(options: FetchOptions): Promise&lt;FetchResult&lt;FileAsset&gt;&gt;


Obtains an audio asset. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [picker.AudioViewPicker](js-apis-file-picker.md#audioviewpicker) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Required permissions**: ohos.permission.READ_AUDIO

**Parameters**

| Name  | Type                    | Mandatory| Description                     |
| -------- | ------------------------ | ---- | ------------------------- |
| options  | [FetchOptions](#fetchoptionsdeprecated)        | Yes   | Fetch options.              |

**Return value**

| Type                       | Description          |
| --------------------------- | -------------- |
| Promise&lt;[FetchResult](#fetchresult)&lt;[FileAsset](#fileassetdeprecated)&gt;&gt; | Promise object, returning the audio retrieval result. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getAudioAssets');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getAudioAssets(fetchOptions);
    if (fetchResult != undefined) {
      console.info('fetchFileResult success');
      let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
      if (fileAsset != undefined) {
        console.info('fileAsset.displayName :' + fileAsset.displayName);
      }
    }
  } catch (err) {
    console.error('getAudioAssets failed, message = ', err);
  }
}
```

### delete<sup>(deprecated)</sup>

delete(uri: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a media file. This API uses an asynchronous callback to return the result. The deleted file is moved to the recycle bin. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAssetChangeRequest.deleteAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#deleteassets11-1) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO, ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.READ_AUDIO, and ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| uri | string | Yes  | URI of the media file.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type uri is not string.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('deleteAssetDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    const fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();


    if (asset == undefined) {
      console.error('asset not exist');
      return;
    }
    mgr.delete(asset.uri, (err) => {
      if (err == undefined) {
        console.info('delete successfully');
      } else {
        console.error('delete failed with error: ' + err);
      }
    });
  } catch (err) {
    console.error('fetch failed, message =', err);
  }
}
```

### delete<sup>(deprecated)</sup>

delete(uri: string): Promise&lt;void&gt;

Deletes media assets. The deleted assets are moved to the trash. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAssetChangeRequest.deleteAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#deleteassets11-1) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO, ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.READ_AUDIO, and ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| uri | string | Yes  | URI of the media file.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;void&gt;| Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type uri is not string.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('deleteDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    const fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    if (asset == undefined) {
      console.error('asset not exist');
      return;
    }
    await mgr.delete(asset.uri);
    console.info('delete successfully');
  } catch (err) {
    console.error('delete failed with error: ' + err);
  }
}
```

### getActivePeers<sup>(deprecated)</sup>

getActivePeers(callback: AsyncCallback&lt;Array&lt;PeerInfo&gt;&gt;): void

Obtains information about online peer devices. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. There is no substitute API.

**System capability**: SystemCapability.FileManagement.UserFileManager.DistributedCore

**Parameters**

| Name  | Type                             | Mandatory| Description        |
| -------- | --------------------------------- | ---- | ------------ |
| callback | AsyncCallback&lt;Array&lt;[PeerInfo](#peerinfodeprecated)&gt;&gt; | Yes | Return the list of online devices. |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('getActivePeersDemo');
  mgr.getActivePeers((err, devicesInfo) => {
    if (devicesInfo != undefined) {
      console.info('getActivePeers succeed.');
      for (let i = 0; i < devicesInfo.length; i++) {
        console.info('get distributed info ' + devicesInfo[i].deviceName + devicesInfo[i].networkId);
      }
    } else {
      console.error('getActivePeers failed. message = ', err);
    }
  });
}
```

### getActivePeers<sup>(deprecated)</sup>

getActivePeers(): Promise&lt;Array&lt;PeerInfo&gt;&gt;

Obtains the information about online peer devices. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. There is no substitute API.

**System capability**: SystemCapability.FileManagement.UserFileManager.DistributedCore

**Return value**

| Type                       | Description                         |
| --------------------------- | ----------------------------- |
| Promise&lt;Array&lt;[PeerInfo](#peerinfodeprecated)&gt;&gt; | Promise used to return the list of online devices. |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('getActivePeersDemo');
  try {
    let devicesInfo: Array<userFileManager.PeerInfo> = await mgr.getActivePeers();
    if (devicesInfo != undefined) {
      console.info('getActivePeers succeed.');
      for (let i = 0; i < devicesInfo.length; i++) {
        console.info('get distributed info ' + devicesInfo[i].deviceName + devicesInfo[i].networkId);
      }
    } else {
      console.error('get distributed fail');
    }
  } catch (err) {
    console.error('getActivePeers failed. message = ', err);
  }
}
```

### getAllPeers<sup>(deprecated)</sup>

getAllPeers(callback: AsyncCallback&lt;Array&lt;PeerInfo&gt;&gt;): void

Obtains information about all peer devices. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. There is no substitute API.

**System capability**: SystemCapability.FileManagement.UserFileManager.DistributedCore

**Parameters**

| Name  | Type                             | Mandatory| Description        |
| -------- | --------------------------------- | ---- | ------------ |
| callback | AsyncCallback&lt;Array&lt;[PeerInfo](#peerinfodeprecated)&gt;&gt; | Yes | Return the list of online devices. |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('getAllPeersDemo');
  mgr.getAllPeers((err, devicesInfo) => {
    if (devicesInfo != undefined) {
      console.info('getAllPeers succeed.');
      for (let i = 0; i < devicesInfo.length; i++) {
        console.info('get distributed info ' + devicesInfo[i].deviceName + devicesInfo[i].networkId);
      }
    } else {
      console.error('getAllPeers failed. message = ', err);
    }
  });
}
```

### getAllPeers<sup>(deprecated)</sup>

getAllPeers(): Promise&lt;Array&lt;PeerInfo&gt;&gt;

Obtains the information about all peer devices. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. There is no substitute API.

**System capability**: SystemCapability.FileManagement.UserFileManager.DistributedCore

**Return value**

| Type                       | Description                         |
| --------------------------- | ----------------------------- |
| Promise&lt;Array&lt;[PeerInfo](#peerinfodeprecated)&gt;&gt; | Promise used to return the list of all devices. |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('getAllPeersDemo');
  try {
    let devicesInfo: Array<userFileManager.PeerInfo> = await mgr.getAllPeers();

    if (devicesInfo != undefined) {
      console.info('getAllPeers succeed.');
      for (let i = 0; i < devicesInfo.length; i++) {
        console.info('get distributed info ' + devicesInfo[i].deviceName + devicesInfo[i].networkId);
      }
    } else {
      console.error('get distributed fail');
    }
  } catch (err) {
    console.error('getAllPeers failed. message = ', err);
  }
}
```

### getPhotoIndex<sup>(deprecated)</sup>

getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions, callback: AsyncCallback&lt;number&gt;): void

Obtains the index of an image or video in an album. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.MediaAssetChangeRequest.getPhotoIndex](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#getphotoindex) instead.

**System API**: This is a system API.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| photoUri | string | Yes  | URI of the media asset whose index is to be obtained.|
| albumUri | string | Yes  | Album URI, which can be an empty string. If it is an empty string, all the media assets in the Gallery are obtained by default.  |
| options  | [FetchOptions](#fetchoptionsdeprecated)       | Yes   |  Retrieval options. A retrieval sorting method must be set in predicates. If no sorting method is set or multiple sorting methods are set, the API call will be abnormal.      |
| callback | AsyncCallback&lt;number&gt;| Yes  | Callback used to return the index obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. | 

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('getPhotoIndexDemo');
    let predicatesForGetAsset: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOp: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicatesForGetAsset
    };
    // Obtain the album URI.
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.SYSTEM, userFileManager.AlbumSubType.FAVORITE, fetchOp);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.orderByAsc(userFileManager.ImageVideoKey.DATE_MODIFIED.toString());
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: [userFileManager.ImageVideoKey.DATE_MODIFIED.toString()],
      predicates: predicates
    };
    let photoFetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOptions);
    let expectIndex = 1;
    // Obtain the URI of the second file.
    let photoAsset: userFileManager.FileAsset = await photoFetchResult.getPositionObject(expectIndex);
    mgr.getPhotoIndex(photoAsset.uri, album.albumUri, fetchOptions, (err, index) => {
      if (err == undefined) {
        console.info(`getPhotoIndex successfully and index is : ${index}`);
      } else {
        console.error(`getPhotoIndex failed;`);
      }
    });
  } catch (error) {
    console.error(`getPhotoIndex failed; error: ${error}`);
  }
}
```

### getPhotoIndex<sup>(deprecated)</sup>

getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions): Promise&lt;number&gt;

Obtains the index of an image or video in an album. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAccessHelper.getPhotoIndex](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#getphotoindex) instead.

**System API**: This is a system API.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| photoUri | string | Yes  | URI of the media asset whose index is to be obtained.|
| albumUri | string | Yes  | Album URI, which can be an empty string. If it is an empty string, all the media assets in the Gallery are obtained by default.  |
| options  | [FetchOptions](#fetchoptionsdeprecated)       | Yes   |  Retrieval options. A retrieval sorting method must be set in predicates. If no sorting method is set or multiple sorting methods are set, the API call will be abnormal.      |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;number&gt;| Promise that returns the index obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. | 

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('getPhotoIndexDemo');
    let predicatesForGetAsset: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOp: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicatesForGetAsset
    };
    // Obtain the album URI.
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.SYSTEM, userFileManager.AlbumSubType.FAVORITE, fetchOp);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    if (album === undefined) {
      console.error('getPhotoIndexPromise albums is undefined');
      return;
    }
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.orderByAsc(userFileManager.ImageVideoKey.DATE_MODIFIED.toString());
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: [userFileManager.ImageVideoKey.DATE_MODIFIED.toString()],
      predicates: predicates
    };
    let photoFetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOptions);
    let expectIndex = 1;
    // Obtain the URI of the second file.
    let photoAsset: userFileManager.FileAsset = await photoFetchResult.getPositionObject(expectIndex);
    mgr.getPhotoIndex(photoAsset.uri, album.albumUri, fetchOptions).then((index) => {
      console.info(`getPhotoIndex successfully and index is : ${index}`);
    }).catch((err: BusinessError) => {
      console.error(`getPhotoIndex failed; error: ${err}`);
    });
  } catch (error) {
    console.error(`getPhotoIndex failed; error: ${error}`);
  }
}
```

### release<sup>(deprecated)</sup>

release(callback: AsyncCallback&lt;void&gt;): void

Releases this **UserFileManager** instance. This API uses an asynchronous callback to return the result.

Call this API when the APIs in the **UserFileManager** instance are no longer used.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAccessHelper.release](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#release) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                |
| -------- | ------------------------- | ---- | -------------------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('releaseDemo');
  mgr.release((err) => {
    if (err != undefined) {
      console.error('release failed. message = ', err);
    } else {
      console.info('release ok.');
    }
  });
}
```

### release<sup>(deprecated)</sup>

release(): Promise&lt;void&gt;

Releases this **UserFileManager** instance. This API uses a promise to return the result.

Call this API when the APIs in the **UserFileManager** instance are no longer used.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAccessHelper.release](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#release) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type               | Description                             |
| ------------------- | --------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('releaseDemo');
  try {
    await mgr.release();
    console.info('release ok.');
  } catch (err) {
    console.error('release failed. message = ', err);
  }
}
```

### on<sup>(deprecated)</sup>

on(uri: string, forSubUri: boolean, callback: Callback&lt;ChangeData&gt;) : void

Registers a listener for the specified URI. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAccessHelper.registerChange](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#registerchange) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name   | Type                                       | Mandatory| Description                                                        |
| --------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| uri       | string                                      | Yes   | URI of the FileAsset, URI of the Album, or the value of [DefaultChangeUri](#defaultchangeurideprecated). |
| forSubUri | boolean                                     | Yes  | Whether to perform fuzzy listening. <br>If **uri** is the URI of the album, the value **true** means to listen for the file change in the album; the value **false** means to listen for the album change only. If **uri** is the URI of the file asset, there is no difference whether **forSubUri** is **true** or **false**. If **uri** is **DefaultChangeUri**, the value must be **true**, otherwise, the URI cannot be found and no message can be received.|
| callback  | Callback&lt;[ChangeData](#changedatadeprecated)&gt; | Yes   | Returns the [ChangeData](#changedatadeprecated) to be listened for. Note: A uri can register multiple different callback listeners. [off](#offdeprecated) can disable all listeners of the uri, or disable the listener of a specified callback. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if parameter is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('onDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  if (fileAsset != undefined) {
    console.info('fileAsset.displayName : ' + fileAsset.displayName);
  }
  let onCallback1 = (changeData: userFileManager.ChangeData) => {
      console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
    // The image file has been changed. Go to the next step.
  }
  let onCallback2 = (changeData: userFileManager.ChangeData) => {
      console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
    // The image file has been changed. Go to the next step.
  }
  // Register onCallback1.
  mgr.on(fileAsset.uri, false, onCallback1);
  // Register onCallback2.
  mgr.on(fileAsset.uri, false, onCallback2);

  fileAsset.favorite(true, (err) => {
    if (err == undefined) {
      console.info('favorite successfully');
    } else {
      console.error('favorite failed with error:' + err);
    }
  });
}
```

### off<sup>(deprecated)</sup>

 off(uri: string, callback?: Callback&lt;ChangeData&gt;): void

Unregisters the listener for the specified URI. Multiple callbacks can be registered for a URI for listening. You can use this API to unregister the specified callbacks or all callbacks.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAccessHelper.unRegisterChange](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#unregisterchange) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                                       | Mandatory| Description                                                        |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| uri      | string                                      | Yes   | URI of the FileAsset, URI of the Album, or the value of [DefaultChangeUri](#defaultchangeurideprecated). |
| callback | Callback&lt;[ChangeData](#changedatadeprecated)&gt; | No   | Cancels the listening of the callback registered by [on](#ondeprecated). If not specified, cancels all listening of this uri. Note: After off specifies the registered callback, it will not enter this callback. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if parameter is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('offDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  if (fileAsset != undefined) {
    console.info('fileAsset.displayName : ' + fileAsset.displayName);
  }
  let onCallback1 = (changeData: userFileManager.ChangeData) => {
    console.info('onCallback1 on');
  }
  let onCallback2 = (changeData: userFileManager.ChangeData) => {
    console.info('onCallback2 on');
  }
  if (fileAsset.uri !== undefined) {
    // Register onCallback1.
    mgr.on(fileAsset.uri, false, onCallback1);
    // Register onCallback2.
    mgr.on(fileAsset.uri, false, onCallback2);
    // Unregister the listening of onCallback1.
    mgr.off(fileAsset.uri, onCallback1);  
  }
  fileAsset.favorite(true, (err) => {
    if (err == undefined) {
      console.info('favorite successfully');
    } else {
      console.error('favorite failed with error:' + err);
    }
  });
}
```

### on<sup>(deprecated)</sup>

on(type: ChangeEvent, callback: Callback&lt;void&gt;): void

Subscribes to changes of the file management library. This API uses a callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAccessHelper.on](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#onphotochange20) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | [ChangeEvent](#changeeventdeprecated)               | Yes   | Media type <br/>'deviceChange':&nbsp;Register device change. <br/>'albumChange':&nbsp;Album change.<br/>'imageChange':&nbsp;Image file change.<br/>'audioChange': &nbsp;Audio file change.<br/>'videoChange':  &nbsp;Video file change.<br/>'remoteFileChange':&nbsp;Register file change on the device. |
| callback | Callback&lt;void&gt; | Yes  | Callback that returns no value.                                                  |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('onDemo');
  let count = 0;
  mgr.on('imageChange', () => {
    count++;
    // The image file has been changed. Go to the next step.
  });
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let fileAsset: userFileManager.FileAsset = await mgr.createPhotoAsset(testFileName);
    console.info('createPhotoAsset file displayName' + fileAsset.displayName);
    console.info('createPhotoAsset successfully');
  } catch (err) {
    console.error('createPhotoAsset failed, message = ' + err);
  }
  // Sleep for 1s.
  if (count > 0) {
    console.info('onDemo success');
  } else {
    console.error('onDemo fail');
  }
  mgr.off('imageChange', () => {
    // The listening is stopped successfully.
  });
}
```

### off<sup>(deprecated)</sup>

off(type: ChangeEvent, callback?: Callback&lt;void&gt;): void

Unsubscribes from changes of the file management library. This API uses a callback to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAccessHelper.off](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAccessHelper.md#offphotochange20) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | [ChangeEvent](#changeeventdeprecated)               | Yes   | Media type <br/>'deviceChange':&nbsp;Register device change. <br/>'albumChange':&nbsp;Album change.<br/>'imageChange':&nbsp;Image file change.<br/>'audioChange': &nbsp;Audio file change.<br/>'videoChange':  &nbsp;Video file change.<br/>'remoteFileChange':&nbsp;Register file change on the device. |
| callback | Callback&lt;void&gt; | No  | Callback that returns no value.                                                  |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('offDemo');
  let count = 0;
  mgr.on('imageChange', () => {
    count++;
    // The image file has been changed. Go to the next step.
  });

  mgr.off('imageChange', () => {
    // The listening is stopped successfully.
  });

  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let fileAsset: userFileManager.FileAsset = await mgr.createPhotoAsset(testFileName);
    console.info('createPhotoAsset file displayName' + fileAsset.displayName);
    console.info('createPhotoAsset successfully');
  } catch (err) {
    console.error('createPhotoAsset failed, message = ' + err);
  }
  // Sleep for 1s.
  if (count == 0) {
    console.info('offDemo success');
  } else {
    console.error('offDemo fail');
  }
}
```

## FileAsset<sup>(deprecated)</sup>

System Album.

Provides APIs for encapsulating file asset attributes.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoAsset](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md) instead.

### Properties

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name                     | Type                    | Read-Only| Optional| Description                                                  |
| ------------------------- | ------------------------ | ---- | ---- | ------------------------------------------------------ |
| uri                       | string                   | Yes   | No   | Media file resource URI (for example, file://media/Photo/1/IMG_datetime_0001/displayName.jpg). For details, see [Media File URI](../../file-management/user-file-uri-intro.md#media-file-uri) in the introduction to user file URIs.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAsset.uri](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#properties) instead.         |
| fileType   | [FileType](#filetypedeprecated) | Yes   | No   | Media file type.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAsset.PhotoType](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md#properties) instead.                                               |
| displayName               | string                   | No   | No   | Display file name, including the suffix.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoAsset.displayName](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#properties) instead.                                 |

### get<sup>(deprecated)</sup>

get(member: string): MemberType

Obtains the value of a **FileAsset** parameter.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAsset.get](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md#get) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description   |
| -------- | ------------------------- | ---- | ----- |
| member | string | Yes   | Member parameter name, for example, **ImageVideoKey.DISPLAY_NAME**. You need to set **PhotoKeys** to be obtained in **fetchColumns** for all attributes except **uri**, **photoType**, and **displayName**. For example, **fetchColumns: ['title']**.|

**Return value**

| Type                   | Description           |
| --------------------- | ------------- |
| MemberType | Returns the member parameter.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('fileAssetGetDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: ['title'],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let title: userFileManager.ImageVideoKey = userFileManager.ImageVideoKey.TITLE;
    let fileAssetTitle: userFileManager.MemberType = fileAsset.get(title.toString());
    console.info('fileAsset Get fileAssetTitle = ', fileAssetTitle);
  } catch (err) {
    console.error('release failed. message = ', err);
  }
}
```

### set<sup>(deprecated)</sup>

set(member: string, value: string): void

Sets a **FileAsset** parameter.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAsset.set](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md#set) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description   |
| -------- | ------------------------- | ---- | ----- |
| member | string | Yes   | Member parameter name, for example, **ImageVideoKey.DISPLAY_NAME**.|
| value | string | Yes   | Value to set. Only the values of **DISPLAY_NAME** and **TITLE** can be changed.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('fileAssetSetDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let displayName: string = userFileManager.ImageVideoKey.DISPLAY_NAME.toString();
    fileAsset.set(displayName, 'newDisplayName1');
  } catch (err) {
    console.error('release failed. message = ', err);
  }
}
```

### commitModify<sup>(deprecated)</sup>

commitModify(callback: AsyncCallback&lt;void&gt;): void

Commits the modification on the file metadata to the database. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAsset.commitModify](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md#commitmodify) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description   |
| -------- | ------------------------- | ---- | ----- |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('commitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  let displayName: string = userFileManager.ImageVideoKey.DISPLAY_NAME.toString();
  let fileAssetDisplayName: userFileManager.MemberType = fileAsset.get(displayName);
  console.info('fileAsset get fileAssetDisplayName = ', fileAssetDisplayName);
  let newFileAssetDisplayName = 'new' + fileAssetDisplayName;
  console.info('fileAsset newFileAssetDisplayName = ', newFileAssetDisplayName);
  fileAsset.set(displayName, newFileAssetDisplayName);
  fileAsset.commitModify((err) => {
    if (err == undefined) {
      let commitModifyDisplayName = fileAsset.get(displayName);
      console.info('fileAsset commitModify successfully, commitModifyDisplayName = ', commitModifyDisplayName);
    } else {
      console.error('commitModify failed, message =', err);
    }
  });
}
```

### commitModify<sup>(deprecated)</sup>

commitModify(): Promise&lt;void&gt;

Commits the modification on the file metadata to the database. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAsset.commitModify](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md#commitmodify) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type                 | Description        |
| ------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('commitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  let displayName = userFileManager.ImageVideoKey.DISPLAY_NAME.toString();
  let fileAssetDisplayName: userFileManager.MemberType = fileAsset.get(displayName);
  console.info('fileAsset get fileAssetDisplayName = ', fileAssetDisplayName);
  let newFileAssetDisplayName = 'new' + fileAssetDisplayName;
  console.info('fileAsset newFileAssetDisplayName = ', newFileAssetDisplayName);
  fileAsset.set(displayName, newFileAssetDisplayName);
  try {
    await fileAsset.commitModify();
    let commitModifyDisplayName = fileAsset.get(displayName);
    console.info('fileAsset commitModify successfully, commitModifyDisplayName = ', commitModifyDisplayName);
  } catch (err) {
    console.error('commitModify failed. message = ', err);
  }
}
```

### open<sup>(deprecated)</sup>

open(mode: string, callback: AsyncCallback&lt;number&gt;): void

Opens this file asset. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> The write operations are mutually exclusive. After a write operation is complete, you must call **close** to close the file.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [fileIo.open](js-apis-file-fs.md#fileioopen-1) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO, ohos.permission.READ_AUDIO, ohos.permission.WRITE_IMAGEVIDEO, or ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name     | Type                         | Mandatory  | Description                                 |
| -------- | --------------------------- | ---- | ----------------------------------- |
| mode     | string                      | Yes   | Mode of opening the file, for example, **'r'** (read-only), **'w'** (write-only), and **'rw'** (read-write).|
| callback | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the file descriptor of the file opened.                           |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('openDemo');
   let testFileName: string = 'testFile' + Date.now() + '.jpg';
  const fileAsset: userFileManager.FileAsset = await mgr.createPhotoAsset(testFileName);
  fileAsset.open('rw', (err, fd) => {
    if (fd != undefined) {
      console.info('File fd' + fd);
      fileAsset.close(fd);
    } else {
      console.error('File err' + err);
    }
  });
}
```

### open<sup>(deprecated)</sup>

open(mode: string): Promise&lt;number&gt;

Opens this file asset. This API uses a promise to return the result.

> **NOTE**
>
> The write operations are mutually exclusive. After a write operation is complete, you must call **close** to close the file.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [fileIo.open](js-apis-file-fs.md#fileioopen) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO, ohos.permission.READ_AUDIO, ohos.permission.WRITE_IMAGEVIDEO, or ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name | Type    | Mandatory  | Description                                 |
| ---- | ------ | ---- | ----------------------------------- |
| mode | string | Yes   | File open mode, which can be **r** (read-only), **w** (write-only), or **rw** (read-write).|

**Return value**

| Type                   | Description           |
| --------------------- | ------------- |
| Promise&lt;number&gt; | Promise that returns the file descriptor of the file opened.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
async function example(mgr: userFileManager.UserFileManager) {
  console.info('openDemo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    const fileAsset: userFileManager.FileAsset = await mgr.createPhotoAsset(testFileName);
    let fd: number = await fileAsset.open('rw');
    if (fd != undefined) {
      console.info('File fd' + fd);
      fileAsset.close(fd);
    } else {
      console.error(' open File fail');
    }
  } catch (err) {
    console.error('open Demo err' + err);
  }
}
```

### close<sup>(deprecated)</sup>

close(fd: number, callback: AsyncCallback&lt;void&gt;): void

Closes a file. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [fileIo.close](js-apis-file-fs.md#fileioclose-1) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description   |
| -------- | ------------------------- | ---- | ----- |
| fd       | number                    | Yes   | File descriptor of the file to close.|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('closeDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    const fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let fd: number = await fileAsset.open('rw');
    console.info('file fd', fd);
    fileAsset.close(fd, (err) => {
      if (err == undefined) {
        console.info('asset close succeed.');
      } else {
        console.error('close failed, message = ' + err);
      }
    });
  } catch (err) {
    console.error('close failed, message = ' + err);
  }
}
```

### close<sup>(deprecated)</sup>

close(fd: number): Promise&lt;void&gt;

Closes this file. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [fileIo.close](js-apis-file-fs.md#fileioclose) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name | Type    | Mandatory  | Description   |
| ---- | ------ | ---- | ----- |
| fd   | number | Yes   | File descriptor of the file to close.|

**Return value**

| Type                 | Description        |
| ------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('closeDemo');
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let fd: number = await asset.open('rw');
    console.info('file fd', fd);
    await asset.close(fd);
    console.info('asset close succeed.');
  } catch (err) {
    console.error('close failed, message = ' + err);
  }
}
```

### getThumbnail<sup>(deprecated)</sup>

getThumbnail(callback: AsyncCallback&lt;image.PixelMap&gt;): void

Obtains the thumbnail of a file. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAsset.getThumbnail](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md#getthumbnail) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name     | Type                                 | Mandatory  | Description              |
| -------- | ----------------------------------- | ---- | ---------------- |
| callback | AsyncCallback&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | Yes   | Callback used to return the PixelMap of the thumbnail.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnail((err, pixelMap) => {
    if (err == undefined) {
      console.info('getThumbnail successful ' + pixelMap);
    } else {
      console.error('getThumbnail fail', err);
    }
  });
}
```

### getThumbnail<sup>(deprecated)</sup>

getThumbnail(size: image.Size, callback: AsyncCallback&lt;image.PixelMap&gt;): void

Obtains the file thumbnail of the given size. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAsset.getThumbnail](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md#getthumbnail) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name     | Type                                 | Mandatory  | Description              |
| -------- | ----------------------------------- | ---- | ---------------- |
| size     | [image.Size](../apis-image-kit/arkts-apis-image-i.md#size) | Yes   | Size of the thumbnail.           |
| callback | AsyncCallback&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | Yes   | Callback used to return the PixelMap of the thumbnail.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let size: image.Size = { width: 720, height: 720 };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnail(size, (err, pixelMap) => {
    if (err == undefined) {
      console.info('getThumbnail successful ' + pixelMap);
    } else {
      console.error('getThumbnail fail', err);
    }
  });
}
```

### getThumbnail<sup>(deprecated)</sup>

getThumbnail(size?: image.Size): Promise&lt;image.PixelMap&gt;

Obtains the file thumbnail of the given size. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAsset.getThumbnail](../apis-media-library-kit/arkts-apis-photoAccessHelper-PhotoAsset.md#getthumbnail) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO or ohos.permission.READ_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name | Type            | Mandatory  | Description   |
| ---- | -------------- | ---- | ----- |
| size | [image.Size](../apis-image-kit/arkts-apis-image-i.md#size) | No   | Size of the thumbnail.|

**Return value**

| Type                           | Description                   |
| ----------------------------- | --------------------- |
| Promise&lt;[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | Promise that returns the PixelMap of the thumbnail.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getThumbnailDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let size: image.Size = { width: 720, height: 720 };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnail(size).then((pixelMap) => {
    console.info('getThumbnail successful ' + pixelMap);
  }).catch((err: BusinessError) => {
    console.error('getThumbnail fail' + err);
  });
}
```

### favorite<sup>(deprecated)</sup>

favorite(isFavorite: boolean, callback: AsyncCallback&lt;void&gt;): void

Favorites or unfavorites a file. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAssetChangeRequest.setFavorite](../apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#setfavorite) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name       | Type                       | Mandatory  | Description                                |
| ---------- | ------------------------- | ---- | ---------------------------------- |
| isFavorite | boolean                   | Yes   | Whether to favorite or unfavorite the file. The value **true** means to favorite the file; the value **false** means the opposite.|
| callback   | AsyncCallback&lt;void&gt; | Yes   | Callback that returns no value.                             |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('favoriteDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  asset.favorite(true, (err) => {
    if (err == undefined) {
      console.info('favorite successfully');
    } else {
      console.error('favorite failed with error:' + err);
    }
  });
}
```

### favorite<sup>(deprecated)</sup>

favorite(isFavorite: boolean): Promise&lt;void&gt;

Favorites or unfavorites this file asset. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAssetChangeRequest.setFavorite](../apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#setfavorite) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name       | Type     | Mandatory  | Description                                |
| ---------- | ------- | ---- | ---------------------------------- |
| isFavorite | boolean | Yes   | Whether to favorite or unfavorite the file. The value **true** means to favorite the file; the value **false** means the opposite.|

**Return value**

| Type                 | Description        |
| ------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('favoriteDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  asset.favorite(true).then(() => {
    console.info('favorite successfully');
  }).catch((err: BusinessError) => {
    console.error('favorite failed with error:' + err);
  });
}
```

### setHidden<sup>(deprecated)</sup>

setHidden(hiddenState: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets a file to hidden state. This API uses an asynchronous callback to return the result.

The private files set to hidden state are located in the private album (in hidden state) and are not open to third-party applications. After obtaining private files from the private album, users can set **hiddenState** to **false** to remove them from the private album.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.MediaAssetChangeRequest.setHidden](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#sethidden11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name       | Type                       | Mandatory  | Description                                |
| ---------- | ------------------------- | ---- | ---------------------------------- |
| hiddenState | boolean                   | Yes   | Whether to hide the file. The value **true** means to hide the file; the value **false** means the opposite.|
| callback   | AsyncCallback&lt;void&gt; | Yes   | Callback that returns no value.                             |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202   | Called by non-system application.                |
| 13900020   | if parameter is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('setHiddenDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  asset.setHidden(true, (err) => {
    if (err == undefined) {
      console.info('setHidden successfully');
    } else {
      console.error('setHidden failed with error:' + err);
    }
  });
}
```

### setHidden<sup>(deprecated)</sup>

setHidden(hiddenState: boolean): Promise&lt;void&gt;

Sets this file asset to the hidden state. This API uses a promise to return the result.

The private files set to hidden state are located in the private album (in hidden state) and are not open to third-party applications. After obtaining private files from the private album, users can set **hiddenState** to **false** to remove them from the private album.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.MediaAssetChangeRequest.setHidden](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#sethidden11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name       | Type     | Mandatory  | Description                                |
| ---------- | ------- | ---- | ---------------------------------- |
| hiddenState | boolean | Yes   | Whether to hide the file. The value **true** means to hide the file; the value **false** means the opposite.|

**Return value**

| Type                 | Description        |
| ------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202   | Called by non-system application.                |
| 13900020   | if parameter is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  // Restore a file from a hidden album. Before the operation, ensure that the file exists in the hidden album.
  console.info('setHiddenDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.SYSTEM, userFileManager.AlbumSubType.HIDDEN);
  const album: userFileManager.Album = await albumList.getFirstObject();
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOption);
  const asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  asset.setHidden(false).then(() => {
    console.info('setHidden successfully');
  }).catch((err: BusinessError) => {
    console.error('setHidden failed with error:' + err);
  });
}
```

### getExif<sup>(deprecated)</sup>

getExif(): Promise&lt;string&gt;

Obtains the EXIF data from a JPG image and returns a JSON string. This API uses a promise to return the result.

> **NOTE**
>
> This API returns a JSON string composed of EXIF tags. The complete EXIF information consists of all_exif and [ImageVideoKey](#imagevideokeydeprecated).USER_COMMENT, and both fields need to be passed in fetchColumns.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAsset.getExif](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#getexif) instead.

**System API**: This is a system API.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;string&gt; | Promise that returns the EXIF data, in JSON strings.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202   | Called by non-system application.               |

**Supported EXIF tags**

For details about the EXIF tags, see [image.PropertyKey](../apis-image-kit/arkts-apis-image-e.md#propertykey7).

| Key Value                                   | Description             |
| --------------------------------------- | ----------------- |
| BitsPerSample | Number of bits per sample.|
| Orientation | Image orientation.|
| ImageLength | Image length.|
| ImageWidth | Image width.|
| GPSLatitude | GPS latitude of the image.|
| GPSLongitude | GPS longitude of the image.|
| GPSLatitudeRef | Latitude reference, for example, N or S. |
| GPSLongitudeRef | Longitude reference, for example, W or E. |
| DateTimeOriginal | Shooting time.|
| ExposureTime | Exposure time.|
| SceneType | Scene type.|
| ISOSpeedRatings | ISO sensitivity or speed.|
| FNumber | f-number.|
| DateTime | Modification time.|
| GPSTimeStamp | GPS timestamp.|
| GPSDateStamp | GPS date stamp.|
| ImageDescription | Image description.|
| Make | Manufacturer.|
| MakeNote | Manufacturer.|
| Model | Model.|
| PhotoMode | Photo mode.|
| SensitivityType | Sensitivity type.|
| StandardOutputSensitivity | Standard output sensitivity.|
| RecommendedExposureIndex | Recommended exposure index.|
| ApertureValue | Aperture value.|
| MeteringMode | Metering mode.|
| LightSource | Light source.|
| Flash | Flash status.|
| FocalLength | Focal length.|
| UserComment | User comments.|
| PixelXDimension | Pixel X dimension.|
| PixelYDimension | Pixel Y dimension.|
| WhiteBalance | White balance.|
| FocalLengthIn35mmFilm | Focal length in 35 mm film.|
| ExposureBiasValue | Exposure compensation.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('getExifDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.isNotNull('all_exif')
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: ['all_exif', userFileManager.ImageVideoKey.USER_COMMENT.toString()],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    console.info('getExifDemo fileAsset displayName: ' + JSON.stringify(fileAsset.displayName));
    let exifMessage: string = await fileAsset.getExif();
    let userCommentKey: string = 'UserComment';
    let userComment: string = JSON.stringify(JSON.parse(exifMessage), [userCommentKey]);
    console.info('getExifDemo userComment: ' + JSON.stringify(userComment));
    fetchResult.close();
  } catch (err) {
    console.error('getExifDemoCallback failed with error: ' + err);
  }
}
```

### getExif<sup>(deprecated)</sup>

getExif(callback: AsyncCallback&lt;string&gt;): void

Obtains the EXIF data from a JPG image and returns a JSON string. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API returns a JSON string composed of EXIF tags. The complete EXIF information consists of all_exif and [ImageVideoKey](#imagevideokeydeprecated).USER_COMMENT, and both fields need to be passed in fetchColumns.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.PhotoAsset.getExif](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#getexif) instead.

**System API**: This is a system API.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback that returns the EXIF data, in JSON strings.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202   | Called by non-system application.               |

**Supported EXIF tags**

For details about the EXIF tags, see [image.PropertyKey](../apis-image-kit/arkts-apis-image-e.md#propertykey7).

| Key Value                                   | Description             |
| --------------------------------------- | ----------------- |
| BitsPerSample | Number of bits per sample.|
| Orientation | Image orientation.|
| ImageLength | Image length.|
| ImageWidth | Image width.|
| GPSLatitude | GPS latitude of the image.|
| GPSLongitude | GPS longitude of the image.|
| GPSLatitudeRef | Latitude reference, for example, N or S. |
| GPSLongitudeRef | Longitude reference, for example, W or E. |
| DateTimeOriginal | Shooting time.|
| ExposureTime | Exposure time.|
| SceneType | Scene type.|
| ISOSpeedRatings | ISO sensitivity or speed.|
| FNumber | f-number.|
| DateTime | Modification time.|
| GPSTimeStamp | GPS timestamp.|
| GPSDateStamp | GPS date stamp.|
| ImageDescription | Image description.|
| Make | Manufacturer.|
| MakeNote | Manufacturer.|
| Model | Model.|
| PhotoMode | Photo mode.|
| SensitivityType | Sensitivity type.|
| StandardOutputSensitivity | Standard output sensitivity.|
| RecommendedExposureIndex | Recommended exposure index.|
| ApertureValue | Aperture value.|
| MeteringMode | Metering mode.|
| LightSource | Light source.|
| Flash | Flash status.|
| FocalLength | Focal length.|
| UserComment | User comments.|
| PixelXDimension | Pixel X dimension.|
| PixelYDimension | Pixel Y dimension.|
| WhiteBalance | White balance.|
| FocalLengthIn35mmFilm | Focal length in 35 mm film.|
| ExposureBiasValue | Exposure compensation.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('getExifDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.isNotNull('all_exif')
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: ['all_exif', userFileManager.ImageVideoKey.USER_COMMENT.toString()],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    if (fileAsset === undefined) {
      console.error('getExif fileAsset is undefined');
      fetchResult.close();
      return;
    }
    console.info('getExifDemo fileAsset displayName: ' + JSON.stringify(fileAsset.displayName));
    let userCommentKey: string = 'UserComment';
    fileAsset.getExif((err, exifMessage) => {
      if (exifMessage != undefined) {
        let userComment: string = JSON.stringify(JSON.parse(exifMessage), [userCommentKey]);
        console.info('getExifDemo userComment: ' + JSON.stringify(userComment));
      } else {
        console.error('getExif failed, message = ', err);
      }
    });
    fetchResult.close();
  } catch (err) {
    console.error('getExifDemoCallback failed with error: ' + err);
  }
}
```

### setUserComment<sup>(deprecated)</sup>

setUserComment(userComment: string): Promise&lt;void&gt;

Sets user comment information of an image or video. This API uses a promise to return the result.

> **NOTE**
>
> This API can only be used to set user comment information of an image or video.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.MediaAssetChangeRequest.setUserComment](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#setusercomment11) instead.

**System API**: This is a system API.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| userComment | string | Yes  | User comment information to set, which cannot exceed 140 characters.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
|Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202   | Called by non-system application.                |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. | 

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('setUserCommentDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let userComment: string = 'test_set_user_comment';
    await fileAsset.setUserComment(userComment);
  } catch (err) {
    console.error('setUserCommentDemoCallback failed with error: ' + err);
  }
}
```

### setUserComment<sup>(deprecated)</sup>

setUserComment(userComment: string, callback: AsyncCallback&lt;void&gt;): void

Sets user comment information of an image or video. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API can only be used to set user comment information of an image or video.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.MediaAssetChangeRequest.setUserComment](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#setusercomment11) instead.

**System API**: This is a system API.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| userComment | string | Yes  | User comment information to set, which cannot exceed 140 characters.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202   | Called by non-system application.                |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. | 

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('setUserCommentDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOptions);
    let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    let userComment: string = 'test_set_user_comment';
    fileAsset.setUserComment(userComment, (err) => {
      if (err === undefined) {
        console.info('setUserComment successfully');
      } else {
        console.error('setUserComment failed with error: ' + err);
      }
    });
  } catch (err) {
    console.error('setUserCommentDemoCallback failed with error: ' + err);
  }
}
```

## FetchResult

Provides APIs to manage the file retrieval result.

### getCount<sup>(deprecated)</sup>

getCount(): number

Obtains the total number of files in the result set.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.FetchResult.getCount](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getcount) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type    | Description      |
| ------ | -------- |
| number | Returns the total number of files obtained.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getCountDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const fetchCount: number = fetchResult.getCount();
  console.info('fetchCount = ', fetchCount);
}
```

### isAfterLast<sup>(deprecated)</sup>

isAfterLast(): boolean

Checks whether the cursor is in the last row of the result set.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.FetchResult.isAfterLast](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#isafterlast) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type     | Description                                |
| ------- | ---------------------------------- |
| boolean | Returns **true** if the cursor is in the last row of the result set; returns **false** otherwise.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  const fetchCount: number = fetchResult.getCount();
  console.info('count:' + fetchCount);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getLastObject();
  if (fetchResult.isAfterLast()) {
    console.info('fileAsset isAfterLast displayName = ', fileAsset.displayName);
  } else {
    console.info('fileAsset  not isAfterLast ');
  }
}
```

### close<sup>(deprecated)</sup>

close(): void

Releases and invalidates the **FetchFileResult** instance. After this instance is released, the APIs in this instance cannot be invoked.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.FetchResult.close](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#close) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('fetchResultCloseDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    fetchResult.close();
    console.info('close succeed.');
  } catch (err) {
    console.error('close fail. message = ' + err);
  }
}
```

### getFirstObject<sup>(deprecated)</sup>

getFirstObject(callback: AsyncCallback&lt;T&gt;): void

Obtains the first file asset in the result set. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.FetchResult.getFirstObject](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getfirstobject) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                                         | Mandatory| Description                                       |
| -------- | --------------------------------------------- | ---- | ------------------------------------------- |
| callback | AsyncCallback&lt;T&gt; | Yes  | Callback used to return the first file asset obtained.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getFirstObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  fetchResult.getFirstObject((err, fileAsset) => {
    if (fileAsset != undefined) {
      console.info('fileAsset displayName: ', fileAsset.displayName);
    } else {
      console.error('fileAsset failed with err:' + err);
    }
  });
}
```

### getFirstObject<sup>(deprecated)</sup>

getFirstObject(): Promise&lt;T&gt;

Obtains the first file asset in the result set. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.FetchResult.getFirstObject](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getfirstobject) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type                                   | Description                      |
| --------------------------------------- | -------------------------- |
| Promise&lt;T&gt; | Promise that returns the first object in the result set.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getFirstObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  console.info('fileAsset displayName: ', fileAsset.displayName);
}
```

### getNextObject<sup>(deprecated)</sup>

getNextObject(callback: AsyncCallback&lt;T&gt;): void

Obtains the next file asset in the result set. This API uses an asynchronous callback to return the result.

Before calling this method, use [isAfterLast()](#isafterlastdeprecated) to check whether the current position is the last row.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.FetchResult.getNextObject](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getnextobject) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name   | Type                                         | Mandatory| Description                                     |
| --------- | --------------------------------------------- | ---- | ----------------------------------------- |
| callback | AsyncCallback&lt;T&gt; | Yes  | Callback used to return the next file asset.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getNextObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  await fetchResult.getFirstObject();
  if (!fetchResult.isAfterLast()) {
    fetchResult.getNextObject((err, fileAsset) => {
      if (fileAsset != undefined) {
        console.info('fileAsset displayName: ', fileAsset.displayName);
      } else {
        console.error('fileAsset failed with err: ' + err);
      }
    });
  }
}
```

### getNextObject<sup>(deprecated)</sup>

getNextObject(): Promise&lt;T&gt;

Obtains the next file asset in the result set. This API uses a promise to return the result.

Before calling this method, use [isAfterLast()](#isafterlastdeprecated) to check whether the current position is the last row.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.FetchResult.getNextObject](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getnextobject) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;T&gt; | Promise that returns the next object in the result set.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getNextObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  await fetchResult.getFirstObject();
  if (!fetchResult.isAfterLast()) {
    let fileAsset: userFileManager.FileAsset = await fetchResult.getNextObject();
    console.info('fileAsset displayName: ', fileAsset.displayName);
  }
}
```

### getLastObject<sup>(deprecated)</sup>

getLastObject(callback: AsyncCallback&lt;T&gt;): void

Obtains the last file asset in the result set. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.FetchResult.getLastObject](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getlastobject) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                                         | Mandatory| Description                       |
| -------- | --------------------------------------------- | ---- | --------------------------- |
| callback | AsyncCallback&lt;T&gt; | Yes  | Callback used to return the last file asset obtained.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getLastObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  fetchResult.getLastObject((err, fileAsset) => {
    if (fileAsset != undefined) {
      console.info('fileAsset displayName: ', fileAsset.displayName);
    } else {
      console.error('fileAsset failed with err: ' + err);
    }
  });
}
```

### getLastObject<sup>(deprecated)</sup>

getLastObject(): Promise&lt;T&gt;

Obtains the last file asset in the result set. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.FetchResult.getLastObject](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getlastobject) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;T&gt; | Promise that returns the last object in the result set.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getLastObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getLastObject();
  console.info('fileAsset displayName: ', fileAsset.displayName);
}
```

### getPositionObject<sup>(deprecated)</sup>

getPositionObject(index: number, callback: AsyncCallback&lt;T&gt;): void

Obtains a file asset with the specified index in the result set. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.FetchResult.getObjectByPosition](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getobjectbyposition) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name      | Type                                      | Mandatory  | Description                |
| -------- | ---------------------------------------- | ---- | ------------------ |
| index    | number                                   | Yes   | Index of the file asset to obtain. The value starts from **0**.    |
| callback | AsyncCallback&lt;T&gt; | Yes   | Callback used to return the file asset obtained.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type index is not number.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getPositionObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  fetchResult.getPositionObject(0, (err, fileAsset) => {
    if (fileAsset != undefined) {
      console.info('fileAsset displayName: ', fileAsset.displayName);
    } else {
      console.error('fileAsset failed with err: ' + err);
    }
  });
}
```

### getPositionObject<sup>(deprecated)</sup>

getPositionObject(index: number): Promise&lt;T&gt;

Obtains a file asset with the specified index in the result set. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.FetchResult.getObjectByPosition](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getobjectbyposition) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name   | Type    | Mandatory  | Description            |
| ----- | ------ | ---- | -------------- |
| index | number | Yes   | Index of the file asset to obtain. The value starts from **0**.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;T&gt; | Promise that returns the file asset obtained.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type index is not number.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getPositionObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  if (fetchResult.getCount() > 0) {
    let fileAsset: userFileManager.FileAsset = await fetchResult.getPositionObject(0);
    console.info('fileAsset displayName: ', fileAsset.displayName);
  } else {
    console.info('No file assets found');
  } 
}
```

### getAllObject<sup>(deprecated)</sup>

getAllObject(callback: AsyncCallback&lt;Array&lt;T&gt;&gt;): void

Obtains all the file assets in the result set. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.FetchResult.getAllObjects](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getallobjects) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                                         | Mandatory| Description                                       |
| -------- | --------------------------------------------- | ---- | ------------------------------------------- |
| callback | AsyncCallback&lt;Array&lt;T&gt;&gt; | Yes  | Callback used to return an array of all file assets in the result set.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getAllObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  fetchResult.getAllObject((err, fileAssetList) => {
    if (fileAssetList != undefined) {
      console.info('fileAssetList length: ', fileAssetList.length);
    } else {
      console.error('fileAssetList failed with err:' + err);
    }
  });
}
```

### getAllObject<sup>(deprecated)</sup>

getAllObject(): Promise&lt;Array&lt;T&gt;&gt;

Obtains all the file assets in the result set. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.FetchResult.getAllObjects](../apis-media-library-kit/arkts-apis-photoAccessHelper-FetchResult.md#getallobjects) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type                                   | Description                      |
| --------------------------------------- | -------------------------- |
| Promise&lt;Array&lt;T&gt;&gt; | Promise that returns an array of all file assets in the result set.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('getAllObjectDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
  let fileAssetList: Array<userFileManager.FileAsset> = await fetchResult.getAllObject();
  console.info('fileAssetList length: ', fileAssetList.length);
}
```

## Album<sup>(deprecated)</sup>

System Album.

Provides APIs to manage albums.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.Album](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#album) instead.

### Properties

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name          | Type   | Read-Only  | Optional | Description  |
| ------------ | ------ | ---- | ---- | ------- |
| albumType | [AlbumType](#albumtypedeprecated) | Yes    | No    | Album type.<br/> **Note:** This API is supported since API version 10, and deprecated since API version 26.0.0, recommended to use [photoAccessHelper.AbsAlbum.albumType](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead.    |
| albumSubType | [AlbumSubType](#albumsubtypedeprecated) | Yes    | No   | Album subtype.<br/> **Note:** This API is supported since API version 10, and deprecated since API version 26.0.0, recommended to use [photoAccessHelper.AbsAlbum.albumSubType](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead.    |
| albumName | string | No    | No   | Album name.<br/>**Note:**<br/>User albums are writable, while preset albums are not writable.<br/>This API is supported since API version 9, and deprecated since API version 26.0.0, recommended to use [photoAccessHelper.AbsAlbum.albumName](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead.    |
| albumUri | string | Yes    | No    | Album URI.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0, recommended to use [photoAccessHelper.AbsAlbum.albumUri](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead.   |
| dateModified  | number | Yes    | No    |  Modification time of the album.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0, recommended to use [photoAccessHelper.Album.dateModified](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#properties-1) instead. |
| count | number | Yes    | No    |  Number of files in the album.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0, recommended to use [photoAccessHelper.AbsAlbum.count](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead. |
| coverUri | string | No    | No     | Cover file URI.<br>**Note:**<br/>User albums are writable, while preset albums are not writable.<br/>This API is supported since API version 9, and deprecated since API version 26.0.0, recommended to use [photoAccessHelper.AbsAlbum.coverUri](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead. |

### getPhotoAssets<sup>(deprecated)</sup>

getPhotoAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult&lt;FileAsset&gt;&gt;): void

Obtains image and video assets. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.AbsAlbum.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#getassets) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| options | [FetchOptions](#fetchoptionsdeprecated) | Yes | Fetch options. |
| callback | AsyncCallback&lt;[FetchResult](#fetchresult)&lt;[FileAsset](#fileassetdeprecated)&gt;&gt; | Yes | callback returns the image and video data result set. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('albumGetFileAssetsDemoCallback');

  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: userFileManager.AlbumFetchOptions = {
    predicates: predicates
  };
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: userFileManager.FetchResult<userFileManager.Album> = await mgr.getPhotoAlbums(albumFetchOptions);
  let album: userFileManager.Album = await albumList.getFirstObject();
  album.getPhotoAssets(fetchOption, (err, albumFetchResult) => {
    if (albumFetchResult != undefined) {
      console.info('album getPhotoAssets successfully, getCount: ' + albumFetchResult.getCount());
    } else {
      console.error('album getPhotoAssets failed with error: ' + err);
    }
  });
}
```

### getPhotoAssets<sup>(deprecated)</sup>

getPhotoAssets(options: FetchOptions): Promise&lt;FetchResult&lt;FileAsset&gt;&gt;

Obtains image and video assets. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.AbsAlbum.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#getassets) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| options | [FetchOptions](#fetchoptionsdeprecated) | Yes | Fetch options. |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;[FetchResult](#fetchresult)&lt;[FileAsset](#fileassetdeprecated)&gt;&gt; | Promise object, used to return the image and video data result set. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('albumGetFileAssetsDemoPromise');

  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: userFileManager.AlbumFetchOptions = {
    predicates: predicates
  };
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  const albumList: userFileManager.FetchResult<userFileManager.Album> = await mgr.getPhotoAlbums(albumFetchOptions);
  const album: userFileManager.Album = await albumList.getFirstObject();
  album.getPhotoAssets(fetchOption).then((albumFetchResult) => {
    console.info('album getFileAssets successfully, getCount: ' + albumFetchResult.getCount());
  }).catch((err: BusinessError) => {
    console.error('album getFileAssets failed with error: ' + err);
  });
}
```

### commitModify<sup>(deprecated)</sup>

commitModify(callback: AsyncCallback&lt;void&gt;): void

Commits the modification on the album attributes to the database. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.Album.commitModify](../apis-media-library-kit/arkts-apis-photoAccessHelper-Album.md#commitmodify) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('albumCommitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: userFileManager.AlbumFetchOptions = {
    predicates: predicates
  };
  const albumList: userFileManager.FetchResult<userFileManager.Album> = await mgr.getPhotoAlbums(albumFetchOptions);
  const album: userFileManager.Album = await albumList.getFirstObject();
  album.albumName = 'hello';
  album.commitModify((err) => {
    if (err != undefined) {
      console.error('commitModify failed with error: ' + err);
    } else {
      console.info('commitModify successfully');
    }
  });
}
```

### commitModify<sup>(deprecated)</sup>

commitModify(): Promise&lt;void&gt;

Commits the modification on the album attributes to the database. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.Album.commitModify](../apis-media-library-kit/arkts-apis-photoAccessHelper-Album.md#commitmodify) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Return value**

| Type                 | Description          |
| ------------------- | ------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('albumCommitModifyDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: userFileManager.AlbumFetchOptions = {
    predicates: predicates
  };
  try {
    let albumList: userFileManager.FetchResult<userFileManager.Album> = await mgr.getPhotoAlbums(albumFetchOptions);
    let album: userFileManager.Album = await albumList.getFirstObject();
    album.albumName = 'hello';
    album.commitModify().then(() => {
      console.info('commitModify successfully');
    }).catch((err: BusinessError) => {
      console.error('commitModify failed with error: ' + err);
    });
  } catch (err) {
    console.error('getPhotoAlbums failed. message = ', err);
  }
}
```

### addPhotoAssets<sup>(deprecated)</sup>

addPhotoAssets(assets: Array&lt;FileAsset&gt;, callback: AsyncCallback&lt;void&gt;): void

Adds image and video assets to an album. Before the operation, ensure that the image and video assets to add and the album exist. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.MediaAlbumChangeRequest.addAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md#addassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | Image or video array to be added to the album. |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if PhotoAssets is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('addPhotoAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.USER, userFileManager.AlbumSubType.USER_GENERIC);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    album.addPhotoAssets([asset], (err) => {
      if (err === undefined) {
        console.info('album addPhotoAssets successfully');
      } else {
        console.error('album addPhotoAssets failed with error: ' + err);
      }
    });
  } catch (err) {
    console.error('addPhotoAssetsDemoCallback failed with error: ' + err);
  }
}
```

### addPhotoAssets<sup>(deprecated)</sup>

addPhotoAssets(assets: Array&lt;FileAsset&gt;): Promise&lt;void&gt;

Adds image and video assets to an album. Before the operation, ensure that the image and video assets to add and the album exist. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.MediaAlbumChangeRequest.addAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md#addassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | Image or video array to be added to the album. |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
|Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if PhotoAssets is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('addPhotoAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.USER, userFileManager.AlbumSubType.USER_GENERIC);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await mgr.getPhotoAssets(fetchOption);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    album.addPhotoAssets([asset]).then(() => {
      console.info('album addPhotoAssets successfully');
    }).catch((err: BusinessError) => {
      console.error('album addPhotoAssets failed with error: ' + err);
    });
  } catch (err) {
    console.error('addPhotoAssetsDemoPromise failed with error: ' + err);
  }
}
```

### removePhotoAssets<sup>(deprecated)</sup>

removePhotoAssets(assets: Array&lt;FileAsset&gt;, callback: AsyncCallback&lt;void&gt;): void

Removes image and video assets from an album. The album and file resources must exist. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAlbumChangeRequest.removeAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md#removeassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | Array of images or videos to be removed from the album. |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if PhotoAssets is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('removePhotoAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.USER, userFileManager.AlbumSubType.USER_GENERIC);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOption);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    album.removePhotoAssets([asset], (err) => {
      if (err === undefined) {
        console.info('album removePhotoAssets successfully');
      } else {
        console.error('album removePhotoAssets failed with error: ' + err);
      }
    });
  } catch (err) {
    console.error('removePhotoAssetsDemoCallback failed with error: ' + err);
  }
}
```

### removePhotoAssets<sup>(deprecated)</sup>

removePhotoAssets(assets: Array&lt;FileAsset&gt;): Promise&lt;void&gt;

Removes image and video assets from an album. The album and file resources must exist. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAlbumChangeRequest.removeAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAlbumChangeRequest.md#removeassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | Array of images or videos to be removed from the album. |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
|Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if PhotoAssets is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('removePhotoAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.USER, userFileManager.AlbumSubType.USER_GENERIC);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOption);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    album.removePhotoAssets([asset]).then(() => {
      console.info('album removePhotoAssets successfully');
    }).catch((err: BusinessError) => {
      console.error('album removePhotoAssets failed with error: ' + err);
    });
  } catch (err) {
    console.error('removePhotoAssetsDemoPromise failed with error: ' + err);
  }
}
```

### recoverPhotoAssets<sup>(deprecated)</sup>

recoverPhotoAssets(assets: Array&lt;FileAsset&gt;, callback: AsyncCallback&lt;void&gt;): void

Recovers image or video assets from the recycle bin. Before the operation, ensure that the image or video assets exist in the recycle bin. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAlbumChangeRequest.recoverAssets](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#recoverassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | Array of images or videos to be restored in the recycle bin. |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if PhotoAssets is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('recoverPhotoAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.SYSTEM, userFileManager.AlbumSubType.TRASH);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOption);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    album.recoverPhotoAssets([asset], (err) => {
      if (err === undefined) {
        console.info('album recoverPhotoAssets successfully');
      } else {
        console.error('album recoverPhotoAssets failed with error: ' + err);
      }
    });
  } catch (err) {
    console.error('recoverPhotoAssetsDemoCallback failed with error: ' + err);
  }
}
```

### recoverPhotoAssets<sup>(deprecated)</sup>

recoverPhotoAssets(assets: Array&lt;FileAsset&gt;): Promise&lt;void&gt;

Recovers image or video assets from the recycle bin. Before the operation, ensure that the image or video assets exist in the recycle bin. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAlbumChangeRequest.recoverAssets](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#recoverassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | Array of images or videos to be restored in the recycle bin. |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
|Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if PhotoAssets is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('recoverPhotoAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.SYSTEM, userFileManager.AlbumSubType.TRASH);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOption);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    album.recoverPhotoAssets([asset]).then(() => {
      console.info('album recoverPhotoAssets successfully');
    }).catch((err: BusinessError) => {
      console.error('album recoverPhotoAssets failed with error: ' + err);
    });
  } catch (err) {
    console.error('recoverPhotoAssetsDemoPromise failed with error: ' + err);
  }
}
```

### deletePhotoAssets<sup>(deprecated)</sup>

deletePhotoAssets(assets: Array&lt;FileAsset&gt;, callback: AsyncCallback&lt;void&gt;): void

Deletes image or video assets from the recycle bin. Before the operation, ensure that the image or video assets exist in the recycle bin. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This operation is irreversible. The assets deleted cannot be restored. Exercise caution when performing this operation.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.MediaAlbumChangeRequest.deleteAssets](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#deleteassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | Array of images or videos to be permanently deleted from the recycle bin. |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if PhotoAssets is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('deletePhotoAssetsDemoCallback');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.SYSTEM, userFileManager.AlbumSubType.TRASH);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOption);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    album.deletePhotoAssets([asset], (err) => {
      if (err === undefined) {
        console.info('album deletePhotoAssets successfully');
      } else {
        console.error('album deletePhotoAssets failed with error: ' + err);
      }
    });
  } catch (err) {
    console.error('deletePhotoAssetsDemoCallback failed with error: ' + err);
  }
}
```

### deletePhotoAssets<sup>(deprecated)</sup>

deletePhotoAssets(assets: Array&lt;FileAsset&gt;): Promise&lt;void&gt;

Deletes image or video assets from the recycle bin. Before the operation, ensure that the image or video assets exist in the recycle bin. This API uses a promise to return the result.

> **NOTE**
>
> This operation is irreversible. The assets deleted cannot be restored. Exercise caution when performing this operation.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.MediaAlbumChangeRequest.deleteAssets](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#deleteassets11) instead.

**Required permissions**: ohos.permission.WRITE_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| assets | Array&lt;[FileAsset](#fileassetdeprecated)&gt; | Yes | Array of images or videos to be permanently deleted from the recycle bin. |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
|Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if PhotoAssets is invalid.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  try {
    console.info('deletePhotoAssetsDemoPromise');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: userFileManager.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let albumFetchResult: userFileManager.FetchResult<userFileManager.Album> = await mgr.getAlbums(userFileManager.AlbumType.SYSTEM, userFileManager.AlbumSubType.TRASH);
    let album: userFileManager.Album = await albumFetchResult.getFirstObject();
    let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await album.getPhotoAssets(fetchOption);
    let asset: userFileManager.FileAsset = await fetchResult.getFirstObject();
    album.deletePhotoAssets([asset]).then(() => {
      console.info('album deletePhotoAssets successfully');
    }).catch((err: BusinessError) => {
      console.error('album deletePhotoAssets failed with error: ' + err);
    });
  } catch (err) {
    console.error('deletePhotoAssetsDemoPromise failed with error: ' + err);
  }
}
```

## PrivateAlbum<sup>(deprecated)</sup>

Provides APIs for managing the system albums.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.Album](#albumdeprecated) instead.

### Properties

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name          | Type   | Read-Only  | Optional  | Description     |
| ------------ | ------ | ---- | ---- | ------- |
| albumName | string | No    | No    | Album name.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.AbsAlbum.albumName](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead.    |
| albumUri | string | Yes    | No    | Album URI.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0, recommended to use [photoAccessHelper.AbsAlbum.albumUri](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead.   |
| dateModified | number | Yes    | No    | Modification date.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.Album.dateModified](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#properties-1) instead.    |
| count | number | Yes    | No    | Number of files in the album.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0, recommended to use [photoAccessHelper.AbsAlbum.count](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead. |
| coverUri | string | No    | No    | Cover file URI.<br/> **Note:** This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.AbsAlbum.coverUri](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#properties) instead. |

### getPhotoAssets<sup>(deprecated)</sup>

getPhotoAssets(options: FetchOptions, callback: AsyncCallback&lt;FetchResult&lt;FileAsset&gt;&gt;): void

Obtains image and video assets from a system album. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.AbsAlbum.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#getassets) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| options | [FetchOptions](#fetchoptionsdeprecated) | Yes | Fetch options. |
| callback | AsyncCallback&lt;[FetchResult](#fetchresult)&lt;[FileAsset](#fileassetdeprecated)&gt;&gt; | Yes | callback returns the image and video data result set. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('privateAlbumGetFileAssetsDemoCallback');
  let albumList: userFileManager.FetchResult<userFileManager.PrivateAlbum> = await mgr.getPrivateAlbum(userFileManager.PrivateAlbumType.TYPE_TRASH);
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  const trashAlbum: userFileManager.PrivateAlbum = await albumList.getFirstObject();
  if (trashAlbum === undefined) {
    console.error('trashAlbum is undefined');
    return;
  }
  trashAlbum.getPhotoAssets(fetchOption, (err, fetchResult) => {
    if (fetchResult != undefined) {
      let count = fetchResult.getCount();
      console.info('fetchResult.count = ', count);
    } else {
      console.error('getFileAssets failed, message = ', err);
    }
  });
}

```

### getPhotoAssets<sup>(deprecated)</sup>

getPhotoAssets(options: FetchOptions): Promise&lt;FetchResult&lt;FileAsset&gt;&gt;

Obtains image and video assets from a system album. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.AbsAlbum.getAssets](../apis-media-library-kit/arkts-apis-photoAccessHelper-AbsAlbum.md#getassets) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| options | [FetchOptions](#fetchoptionsdeprecated) | Yes | Fetch options. |

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise:[FetchResult](#fetchresult)&lt;[FileAsset](#fileassetdeprecated)&gt;| Promise object, used to return the image and video data result set. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 13900020   | if type options is not FetchOptions.         |

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('privateAlbumGetFileAssetsDemoPromise');
  let albumList: userFileManager.FetchResult<userFileManager.PrivateAlbum> = await mgr.getPrivateAlbum(userFileManager.PrivateAlbumType.TYPE_TRASH);
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  const trashAlbum: userFileManager.PrivateAlbum = await albumList.getFirstObject();
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await trashAlbum.getPhotoAssets(fetchOption);
  let count = fetchResult.getCount();
  console.info('fetchResult.count = ', count);
}
```

### delete<sup>(deprecated)</sup>

delete(uri: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a file from the system album. Only the files in the trash can be deleted. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.MediaAssetChangeRequest.deleteAssetsWithUri](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#deleteassetswithuri19) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO, ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.READ_AUDIO, and ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| uri | string | Yes  | File URI.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('privateAlbumDeleteCallback');
  let albumList: userFileManager.FetchResult<userFileManager.PrivateAlbum> = await mgr.getPrivateAlbum(userFileManager.PrivateAlbumType.TYPE_TRASH);
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let trashAlbum: userFileManager.PrivateAlbum = await albumList.getFirstObject();
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await trashAlbum.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  let deleteFileUri = fileAsset.uri;
  trashAlbum.delete(deleteFileUri, (err) => {
    if (err != undefined) {
      console.error('trashAlbum.delete failed, message = ', err);
    } else {
      console.info('trashAlbum.delete successfully');
    }
  });
}
```

### delete<sup>(deprecated)</sup>

delete(uri: string): Promise&lt;void&gt;

Deletes a file from the system album. Only the files in the trash can be deleted. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.MediaAssetChangeRequest.deleteAssetsWithUri](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#deleteassetswithuri19) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO, ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.READ_AUDIO, and ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| uri | string | Yes  | File URI.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;void&gt;| Promise that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('privateAlbumDeleteDemoPromise');
  let albumList: userFileManager.FetchResult<userFileManager.PrivateAlbum> = await mgr.getPrivateAlbum(userFileManager.PrivateAlbumType.TYPE_TRASH);
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let trashAlbum: userFileManager.PrivateAlbum = await albumList.getFirstObject();
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await trashAlbum.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  let deleteFileUri = fileAsset.uri;
  trashAlbum.delete(deleteFileUri).then(() => {
    console.info('trashAlbum.delete successfully');
  }).catch((err: BusinessError) => {
    console.error('trashAlbum.delete failed, message = ', err);
  });
}
```

### recover<sup>(deprecated)</sup>

recover(uri: string, callback: AsyncCallback&lt;void&gt;): void

Recovers a file in the system album. Only the files in the trash can be recovered. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAssetChangeRequest.recoverAssetsWithUri](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#recoverassetswithuri19) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO, ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.READ_AUDIO, and ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| uri | string | Yes  | File URI.|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('privateAlbumRecoverDemoCallback');
  let albumList: userFileManager.FetchResult<userFileManager.PrivateAlbum> = await mgr.getPrivateAlbum(userFileManager.PrivateAlbumType.TYPE_TRASH);
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let trashAlbum: userFileManager.PrivateAlbum = await albumList.getFirstObject();
  if (trashAlbum === undefined) {
    console.error('privateAlbumRecoverDemoCallback trashAlbum is undefined');
    return;
  }
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await trashAlbum.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  if (fileAsset === undefined) {
    console.error('privateAlbumRecoverDemoCallback fileAsset is undefined');
    return;
  }
  let recoverFileUri: string = fileAsset.uri;
  trashAlbum.recover(recoverFileUri, (err) => {
    if (err != undefined) {
      console.error('trashAlbum.recover failed, message = ', err);
    } else {
      console.info('trashAlbum.recover successfully');
    }
  });
}
```

### recover<sup>(deprecated)</sup>

recover(uri: string): Promise&lt;void&gt;

Recovers a file in the system album. Only the files in the trash can be recovered. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MediaAssetChangeRequest.recoverAssetsWithUri](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#recoverassetswithuri19) instead.

**Required permissions**: ohos.permission.READ_IMAGEVIDEO, ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.READ_AUDIO, and ohos.permission.WRITE_AUDIO

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| uri | string | Yes  | File URI.|

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| Promise&lt;void&gt;| Promise that returns no value.|

**Example**

For details about how to create mgr, see [userFileManager.getUserFileMgr](#userfilemanagergetuserfilemgrdeprecated).

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(mgr: userFileManager.UserFileManager) {
  console.info('privateAlbumRecoverDemoPromise');
  let albumList: userFileManager.FetchResult<userFileManager.PrivateAlbum> = await mgr.getPrivateAlbum(userFileManager.PrivateAlbumType.TYPE_TRASH);
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: userFileManager.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let trashAlbum: userFileManager.PrivateAlbum = await albumList.getFirstObject();
  let fetchResult: userFileManager.FetchResult<userFileManager.FileAsset> = await trashAlbum.getPhotoAssets(fetchOption);
  let fileAsset: userFileManager.FileAsset = await fetchResult.getFirstObject();
  let recoverFileUri: string = fileAsset.uri;
  trashAlbum.recover(recoverFileUri).then(() => {
    console.info('trashAlbum.recover successfully');
  }).catch((err: BusinessError) => {
    console.error('trashAlbum.recover failed, message = ', err);
  });
}
```

## MemberType<sup>(deprecated)</sup>

type MemberType = number | string | boolean

Represents the type of a file asset member.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.MemberType](../apis-media-library-kit/arkts-apis-photoAccessHelper-t.md#membertype) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Type | Description                     |
| ----- |  ---- |
| number | The member is a number.|
| string | The member is a string.|
| boolean | The member is a Boolean value.|

## ChangeEvent<sup>(deprecated)</sup>

type ChangeEvent = 'deviceChange' | 'albumChange' | 'imageChange' | 'audioChange' | 'videoChange' | 'remoteFileChange'

Enumerates the type of changes to observe.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.ChangeData](../apis-media-library-kit/arkts-apis-photoAccessHelper-i.md#changedata) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Type | Description                     |
| ----- |  ---- |
| 'deviceChange' | Device. The value is fixed at **'deviceChange'**.|
| 'albumChange' | Album. The value is fixed at **'albumChange'**.|
| 'imageChange' | Image. The value is fixed at **'imageChange'**.|
| 'audioChange' | Audio. The value is fixed at **'audioChange'**.|
| 'videoChange' | Video. The value is fixed at **'videoChange'**.|
| 'remoteFileChange' | Remote file. The value is fixed at **'remoteFileChange'**.|

## PeerInfo<sup>(deprecated)</sup>

Defines information about a registered device.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. There is no substitute API.

**System capability**: SystemCapability.FileManagement.UserFileManager.DistributedCore

| Name      | Type                      | Read-Only| Optional| Description            |
| ---------- | -------------------------- | ---- | ---- | ---------------- |
| deviceName | string                     | Yes  | No  | Name of the registered device.  |
| networkId  | string                     | Yes  | No  | Network ID of the registered device.|
| isOnline   | boolean                    | Yes  | No  | Whether the registered device is online. The value **true** means the registered device is online; the value **false** means the opposite.        |

## FileType<sup>(deprecated)</sup>

Enumerates media file types.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoType](../apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#phototype) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name |  Value|  Description|
| ----- |  ---- |  ---- |
| IMAGE |  1 |  Image.|
| VIDEO |  2 |  Video.|
| AUDIO |  3 |  Audio.|

## PhotoSubType<sup>(deprecated)</sup>

Enumerates the types of different [FileAsset](#fileassetdeprecated).

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoSubType](../apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#photosubtype12) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name |  Value|  Description|
| ----- |  ---- |  ---- |
| DEFAULT |  0 |  Default (photo) type.|
| SCREENSHOT |  1 |  Screenshots and screen recording files.|
| CAMERA |  2 |  Photos and videos taken by a camera.|

## PositionType<sup>(deprecated)</sup>

Enumerates the file location.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PositionType](../apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#positiontype16) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name |  Value|  Description|
| ----- |  ---- |  ---- |
| LOCAL |  1 |  Stored only on a local device.|
| CLOUD |  2 |  Stored only on the cloud.|
| BOTH |  3 |  Stored both on a local device and the cloud.|

## AlbumType<sup>(deprecated)</sup>

Enumerates the album types.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.AlbumType](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#albumtype) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name |  Value|  Description|
| ----- |  ---- |  ---- |
| USER |  0 |  User album.|
| SYSTEM |  1024 |  System album.|

## AlbumSubType<sup>(deprecated)</sup>

Enumerates the album subtypes.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.AlbumSubType](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#albumsubtype) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name |  Value|  Description|
| ----- |  ---- |  ---- |
| USER_GENERIC |  1 |  User album.|
| FAVORITE |  1025 |  Favorites.|
| VIDEO |  1026 |  Video album.|
| HIDDEN |  1027 |  Hidden album.|
| TRASH |  1028 |  Trash.|
| SCREENSHOT |  1029 |  Album for screenshots and screen recording files.|
| CAMERA |  1030 |  Album for photos and videos taken by the camera.|
| ANY |  2147483647 |  Any album.|

## PrivateAlbumType<sup>(deprecated)</sup>

Enumerates the system album types.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.AlbumSubtype](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#albumsubtype) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name   |  Value|   Description  |
| -----   |  ----  |   ----  |
| TYPE_FAVORITE |  0 |  Favorites.|
| TYPE_TRASH |  1 |  Trash.|

## AudioKey<sup>(deprecated)</sup>

Defines the key information about an audio file.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [picker.AudioViewPicker](js-apis-file-picker.md#audioviewpicker) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name         |   Value             | Description                                                      |
| ------------- | ------------------- | ---------------------------------------------------------- |
| URI           | uri                 | URI of the file.                                                  |
| DISPLAY_NAME  | display_name        | File name displayed.                                                  |
| DATE_ADDED    | date_added          | Date when the file was added. The value is the number of seconds elapsed since the Epoch time (00:00:00 UTC on January 1, 1970).            |
| DATE_MODIFIED | date_modified       | Date when the file content (not the file name) was last modified. The value is the number of seconds elapsed since the Epoch time (00:00:00 UTC on January 1, 1970).|
| TITLE         | title               | Title of the file.                                                  |
| ARTIST        | artist              | Author of the file.                                                  |
| AUDIOALBUM    | audio_album         | Audio album.                                                  |
| DURATION      | duration            | Duration, in ms.                                   |
| FAVORITE      | favorite            | Whether the file is added to favorites.                                                  |

## ImageVideoKey<sup>(deprecated)</sup>

Defines the key information about an image or video file.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.PhotoKeys](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#photokeys) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name         | Value             | Description                                                      |
| ------------- | ------------------- | ---------------------------------------------------------- |
| URI           | uri                 | URI of the file.                                                  |
| FILE_TYPE     | file_type           | Type of the file.                                             |
| DISPLAY_NAME  | display_name        | File name displayed.                                                  |
| DATE_ADDED    | date_added          | Date when the file was added. The value is the number of seconds elapsed since the Epoch time (00:00:00 UTC on January 1, 1970).            |
| DATE_MODIFIED | date_modified       | Date when the file content (not the file name) was last modified. The value is the number of seconds elapsed since the Epoch time (00:00:00 UTC on January 1, 1970).|
| TITLE         | title               | Title of the file.                                                  |
| DURATION      | duration            | Duration, in ms.                                   |
| WIDTH         | width               | Image width, in pixels.                                   |
| HEIGHT        | height              | Image height, in pixels.                                     |
| DATE_TAKEN    | date_taken          | Date when the file (photo) was taken. The value is the number of seconds elapsed since the Epoch time (00:00:00 UTC on January 1, 1970).               |
| ORIENTATION   | orientation         | Orientation of the image file.                                            |
| FAVORITE      | favorite            | Whether the file is added to favorites.                                                   |
| POSITION  | position            | File position type.                               |
| DATE_TRASHED  | date_trashed  | Deletion date (the number of seconds from the deletion time to January 1, 1970).                 |
| HIDDEN  | hidden            | Hidden status of the file.                               |
| CAMERA_SHOT_KEY    | camera_shot_key           | Marker field for photos or videos taken by the lock screen camera (open only to the system camera, and its key value is defined by the system camera).    |
| USER_COMMENT  | user_comment            | User comment information.                               |

## AlbumKey<sup>(deprecated)</sup>

Defines the key album information.

> **NOTE**
>
> This API is supported since API version 9, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.AlbumKeys](../apis-media-library-kit/js-apis-photoAccessHelper-sys.md#albumkeys) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name         | Value             | Description                                                      |
| ------------- | ------------------- | ---------------------------------------------------------- |
| URI           | uri                 | URI of the album.                                                  |
| FILE_TYPE     | file_type           | Type of the file.                                             |
| ALBUM_NAME    | album_name          | Name of the album.                                                  |
| DATE_ADDED    | date_added          | Date when the file was added. The value is the number of seconds elapsed since the Epoch time (00:00:00 UTC on January 1, 1970).            |
| DATE_MODIFIED | date_modified       | Date when the file content (not the file name) was last modified. The value is the number of seconds elapsed since the Epoch time (00:00:00 UTC on January 1, 1970).|

## PhotoCreateOptions<sup>(deprecated)</sup>

Defines the options for creating an image or video asset.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.PhotoCreateOptions](../apis-media-library-kit/arkts-apis-photoAccessHelper-i.md#createoptions) instead.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name                  | Type               | Read-Only| Optional| Description                                             |
| ---------------------- | ------------------- | ---- |---- | ------------------------------------------------ |
| subType           | [PhotoSubType](#photosubtypedeprecated) | No   | Yes   | Subtype of the image or video. |
| cameraShotKey           | string | No  | Yes  | Key for the Ultra Snapshot feature, which allows the camera to take photos or record videos with the screen off. (This parameter is available only for the system camera, and the key value is defined by the system camera.)|

## FetchOptions<sup>(deprecated)</sup>

Defines the options for fetching file attributes.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.FetchOptions](../apis-media-library-kit/arkts-apis-photoAccessHelper-i.md#fetchoptions) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name                  | Type               | Read-Only| Optional| Description                                             |
| ---------------------- | ------------------- | ---- |---- | ------------------------------------------------ |
| fetchColumns           | Array&lt;string&gt; | No   | No   | Retrieval condition, specifying the column names for query. If this parameter is empty, uri, name, and fileType are queried by default (the specific field names are subject to the definition of the retrieval object), and an error is reported when using the [get](#getdeprecated) API to obtain other properties of the current object. Example:<br />fetchColumns: ['uri', 'title']. |
| predicates           | [dataSharePredicates.DataSharePredicates](../apis-arkdata/js-apis-data-dataSharePredicates-sys.md) | No  | No  | Predicates that specify the fetch criteria.|

## AlbumFetchOptions<sup>(deprecated)</sup>

Defines the options for fetching an album.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 26.0.0. You are advised to use [photoAccessHelper.FetchOptions](../apis-media-library-kit/arkts-apis-photoAccessHelper-i.md#fetchoptions) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name                  | Type               | Read-Only| Optional| Description                                             |
| ---------------------- | ------------------- | ---- |---- | ------------------------------------------------ |
| predicates           | [dataSharePredicates.DataSharePredicates](../apis-arkdata/js-apis-data-dataSharePredicates-sys.md) | No  | No  | Predicates that specify the fetch criteria.|

## ChangeData<sup>(deprecated)</sup>

Defines the return value of the listener callback.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.ChangeData](../apis-media-library-kit/arkts-apis-photoAccessHelper-i.md#changedata) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name   | Type                       | Read-Only| Optional| Description                                                        |
| ------- | --------------------------- | ---- | ---- | ------------------------------------------------------------ |
| type    | [NotifyType](#notifytypedeprecated) | No   | No   | Notification type of ChangeData.                                       |
| uris    | Array&lt;string&gt;         | No   | No   | All URIs of the same [NotifyType](#notifytypedeprecated), which can be FileAsset or Album. |
| subUris | Array&lt;string&gt;         | No  | No  | URIs of the changed files in the album. The value may be undefined. Check whether the value is undefined before using it.|

## NotifyType<sup>(deprecated)</sup>

Enumerates the notification event types.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 26.0.0. It is recommended to use [photoAccessHelper.NotifyType](../apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#notifytype) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name                     | Value  | Description                            |
| ------------------------- | ---- | -------------------------------- |
| NOTIFY_ADD                | 0    | A file asset or album is added.    |
| NOTIFY_UPDATE             | 1    | A file asset or album is updated.    |
| NOTIFY_REMOVE             | 2    | A file asset or album is removed.    |
| NOTIFY_ALBUM_ADD_ASSET    | 3    | A file asset is added to the album.|
| NOTIFY_ALBUM_REMOVE_ASSET | 4    | A file asset is removed from the album.|

## DefaultChangeUri<sup>(deprecated)</sup>

Enumerates the **DefaultChangeUri** subtypes.

> **NOTE**
>
> This API is supported since API version 10, and deprecated since API version 26.0.0. Recommended to use [photoAccessHelper.DefaultChangeUri](../apis-media-library-kit/arkts-apis-photoAccessHelper-e.md#defaultchangeuri) instead.

**System capability**: SystemCapability.FileManagement.UserFileManager.Core

| Name             | Value                     | Description                                                        |
| ----------------- | ----------------------- | ------------------------------------------------------------ |
| DEFAULT_PHOTO_URI | file://media/Photo      | Default **PhotoAsset** URI. The **PhotoAsset** change notifications are received based on this parameter and **forSubUri{true}**.|
| DEFAULT_ALBUM_URI | file://media/PhotoAlbum | Default album URI. Album change notifications are received based on this parameter and **forSubUri{true}**. |
| DEFAULT_AUDIO_URI | file://media/Audio      | Default **AudioAsset** URI. The **AudioAsset** change notifications are received based on this parameter and **forSubUri{true}**.|

