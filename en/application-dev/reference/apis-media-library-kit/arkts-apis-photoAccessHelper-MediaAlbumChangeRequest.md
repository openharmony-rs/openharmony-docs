# Class (MediaAlbumChangeRequest)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=f2c7727dff910038fdcf1b75fb074e51aa470331 translatedAt=2026-11-03T07:02:48.973Z pushedAt=2026-11-04T03:11:19.954Z nl=1 -->

The MediaAlbumChangeRequest class implements the [MediaChangeRequest](arkts-apis-photoAccessHelper-i.md#mediachangerequest11) interface.

MediaAlbumChangeRequest provides APIs for managing the media album change request.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this class are supported since API version 11.

## Modules to Import

```ts
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## Attributes

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

| Name          | Type   | Read-Only  | Optional | Description  |
| ------------ | ------ | ---- | ---- | ------- |
| comment<sup>23+</sup>    | string | Yes   | No  | Used to verify the [MediaChangeRequest](arkts-apis-photoAccessHelper-i.md#mediachangerequest11) type.<br>If a class (such as **MediaAlbumChangeRequest**) object can be accessed, it is an implementation class of **MediaChangeRequest**.|

## constructor<sup>11+</sup>

constructor(album: Album)

Initializes a newly created object. The constructor is used to perform operations on an album.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name  | Type                     | Mandatory| Description      |
| -------- | ------------------------- | ---- | ---------- |
| album | [Album](arkts-apis-photoAccessHelper-Album.md) | Yes  | Album to change.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The constructor was not called with the new keyword.<br>2. The album to be modified is invalid, the passed Album is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>3. System memory insufficient, please retry.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('MediaAlbumChangeRequest constructorDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions);
    let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
    let albumChangeRequest: photoAccessHelper.MediaAlbumChangeRequest = new photoAccessHelper.MediaAlbumChangeRequest(album);
  } catch (err) {
    console.error(`MediaAlbumChangeRequest constructorDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getAlbum<sup>11+</sup>

getAlbum(): Album

Obtains the album in the current album change request.

> **NOTE**
>
> For the change request for creating an album, this API returns **null** before [applyChanges](arkts-apis-photoAccessHelper-PhotoAccessHelper.md#applychanges11) is called to apply the changes.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Return value**

| Type                                   | Description             |
| --------------------------------------- | ----------------- |
| [Album](arkts-apis-photoAccessHelper-Album.md) | Album obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The album to be modified is invalid, the Album passed to the MediaAlbumChangeRequest constructor is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>2. System memory insufficient, please retry.<br>3. IPC timeout, please retry.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAlbumDemo');
  try {
    // Ensure that the user album exists in the gallery.
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let albumChangeRequest: photoAccessHelper.MediaAlbumChangeRequest = new photoAccessHelper.MediaAlbumChangeRequest(album);
    let changeRequestAlbum: photoAccessHelper.Album = albumChangeRequest.getAlbum();
    console.info('change request album uri: ' + changeRequestAlbum.albumUri);
  } catch (err) {
    console.error(`getAlbumDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setAlbumName<sup>11+</sup>

setAlbumName(name: string): void

Sets the album name.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name       | Type     | Mandatory  | Description                                |
| ---------- | ------- | ---- | ---------------------------------- |
| name | string | Yes | Name of the album to set.<br>The album name is a string of 1 to 255 characters. The following illegal English characters are not allowed:<br> . \ / : * ? " ' ` < > \| { } [ ]<br>English characters are case-insensitive.<br>Duplicate album names are not allowed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The name parameter is invalid, please check if the name meets the naming rules (non-empty, within length limit, no illegal characters).<br>2. The album to be modified is invalid, the Album passed to the MediaAlbumChangeRequest constructor is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>3. The album type does not support setAlbumName, only user source albums, highlights, smart portrait albums and group photos support this operation.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setAlbumNameDemo');
  try {
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let albumChangeRequest: photoAccessHelper.MediaAlbumChangeRequest = new photoAccessHelper.MediaAlbumChangeRequest(album);
    let newAlbumName: string = 'newAlbumName' + new Date().getTime();
    albumChangeRequest.setAlbumName(newAlbumName);
    await phAccessHelper.applyChanges(albumChangeRequest);
    console.info('setAlbumName successfully');
  } catch (err) {
    console.error(`setAlbumNameDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## addAssets<sup>11+</sup>

addAssets(assets: Array&lt;PhotoAsset&gt;): void

Add assets to the album.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name       | Type     | Mandatory  | Description                                |
| ---------- | ------- | ---- | ---------------------------------- |
| assets | Array&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt; | Yes  | Array of assets to add.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The assets array contains assets that were already added in a previous addAssets operation, please remove duplicates.<br>2. The album to be modified is invalid, the Album passed to the MediaAlbumChangeRequest constructor is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>3. The album type does not support addAssets, only user albums and highlight albums support this operation.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |
| 14000016 | Operation type not support. Possible causes:<br>Duplicate asset in addAssets, the asset was already added in a previous addAssets operation. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('addAssetsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    // Ensure that user albums and photos exist in Gallery.
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let albumChangeRequest: photoAccessHelper.MediaAlbumChangeRequest = new photoAccessHelper.MediaAlbumChangeRequest(album);
    albumChangeRequest.addAssets([asset]);
    await phAccessHelper.applyChanges(albumChangeRequest);
    console.info('addAssets successfully');
  } catch (err) {
    console.error(`addAssetsDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## removeAssets<sup>11+</sup>

removeAssets(assets: Array&lt;PhotoAsset&gt;): void

Removes assets from the album.

**System capability**: SystemCapability.FileManagement.PhotoAccessHelper.Core

**Parameters**

| Name       | Type     | Mandatory  | Description                                |
| ---------- | ------- | ---- | ---------------------------------- |
| assets | Array&lt;[PhotoAsset](arkts-apis-photoAccessHelper-PhotoAsset.md)&gt; | Yes  | Array of assets to remove.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](../apis-core-file-kit/errorcode-filemanagement.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14000011 | MediaLibrary inner fail. Possible causes:<br>1. The album to be modified is invalid, the Album passed to the MediaAlbumChangeRequest constructor is not a valid instance obtained from photoAccessHelper.getAlbums() or createAlbum().<br>2. The album type does not support removeAssets, only user albums support this operation.<br>3. The assets array contains elements that are not valid PhotoAsset objects.<br>4. System internal error, possible causes: <br>(1) Database exception; <br>(2) File system exception; <br>(3) IPC timeout. Please retry and check logs. |
| 14000016 | Operation type not support. Possible causes:<br>Duplicate asset in removeAssets, the asset was already removed in a previous removeAssets operation. |

**Example**

For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).

```ts
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('removeAssetsDemo');
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

    let albumChangeRequest: photoAccessHelper.MediaAlbumChangeRequest = new photoAccessHelper.MediaAlbumChangeRequest(album);
    albumChangeRequest.removeAssets([asset]);
    await phAccessHelper.applyChanges(albumChangeRequest);
    console.info('removeAssets successfully');
  } catch (err) {
    console.error(`removeAssetsDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```
