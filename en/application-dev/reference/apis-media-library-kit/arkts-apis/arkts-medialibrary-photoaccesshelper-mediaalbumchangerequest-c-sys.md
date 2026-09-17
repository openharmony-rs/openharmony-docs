# MediaAlbumChangeRequest

Provides APIs for managing the media album change request.

**Inheritance/Implementation:** MediaAlbumChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## createAlbumRequest

```TypeScript
static createAlbumRequest(context: Context, name: string): MediaAlbumChangeRequest
```

Creates a MediaAlbumChangeRequest instance.

The album name must meet the following requirements:

- The total length of the album name must be between 1 and 255 characters.  
- It must not contain any invalid characters, which are:

. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

- The characters are case insensitive.  
- Duplicate album names are not allowed.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| name | string | Yes | Name of the album. |

**Return value:**

| Type | Description |
| --- | --- |
| [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md) | MediaAlbumChangeRequest instance created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## deleteAlbums

```TypeScript
static deleteAlbums(context: Context, albums: Array<Album>): Promise<void>
```

Deletes user albums. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| albums | Array&lt;[Album](arkts-medialibrary-photoaccesshelper-album-i.md)&gt; | Yes | Albums to delete. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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

## deleteAlbumsWithUri

```TypeScript
static deleteAlbumsWithUri(context: Context, albumUris: Array<string>): Promise<void>
```

Deletes user albums by URI. This API uses a promise to return the result.

**Since:** 19

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| albumUris | Array&lt;string&gt; | Yes | Array of URIs of the albums to be deleted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| 13900020 | Invalid argument |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out; |

**Examples**

```TypeScript
async function example(context: Context, albumUri: string) {
  console.info('deleteAlbumsWithUriDemo');
  try {
    await photoAccessHelper.MediaAlbumChangeRequest.deleteAlbumsWithUri(context, [albumUri]);
    console.info('deleteAlbums successfully');
  } catch (err) {
    console.error(`deleteAlbumsWithUriDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## deleteAssets

```TypeScript
deleteAssets(assets: Array<PhotoAsset>): void
```

Permanently deletes assets from the trash.

> **NOTE:** 
> 
> This operation is irreversible. The assets deleted cannot be restored. Exercise caution when performing this
> operation.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Assets to be permanently deleted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## deleteAssetsWithUri

```TypeScript
deleteAssetsWithUri(assetUris: Array<string>): void
```

Permanently deletes assets from the trash.

> **NOTE:** 
> 
> This operation is irreversible. The assets deleted cannot be restored. Exercise caution when performing this
> operation.

**Since:** 19

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetUris | Array&lt;string&gt; | Yes | Array of URIs of the assets to be permanently deleted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| 13900020 | Invalid argument |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## dismiss

```TypeScript
dismiss(): void
```

Removes this group photo album.

**Since:** 13

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## dismissAssets

```TypeScript
dismissAssets(assets: Array<PhotoAsset>): void
```

Removes assets from this portrait album or group photo album.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Assets to remove. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## mergeAlbum

```TypeScript
mergeAlbum(target: Album): void
```

Merges two portrait albums.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Yes | Album generated after the merge. The album must be renamed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## moveAssets

```TypeScript
moveAssets(assets: Array<PhotoAsset>, targetAlbum: Album): void
```

Moves assets to another album.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Assets to move. |
| targetAlbum | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Yes | Album to which the assets are to be moved. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## moveAssetsWithUri

```TypeScript
moveAssetsWithUri(assetUris: Array<string>, targetAlbum: Album): void
```

Moves assets in an album to another album.

**Since:** 19

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetUris | Array&lt;string&gt; | Yes | Array of URIs of the assets to move. |
| targetAlbum | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Yes | Album to which the assets are to be moved. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| 13900020 | Invalid argument |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## operateAttribute

```TypeScript
operateAttribute(operation: AlbumOperation): void
```

Operates album attribute.

**Since:** 26.0.0

**Required permissions:** 
- API versions 26 to 0: ohos.permission.ACCESS_MEDIALIB_THUMB_DB
- API version 26 and later: ohos.permission.ACCESS_MEDIALIB_THUMB_DB or ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| operation | [AlbumOperation](arkts-medialibrary-photoaccesshelper-albumoperation-i-sys.md) | Yes | operation to execute for the album. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The attr of operation is invalid; <br>2. The type of operation is invalid; <br>3. The values of operation is incorrect; |
| [23800201](../errorcode-medialibrary.md#23800201-unsupported-operation-type) | Unsupported operation type. It is recommended to check the logs. Possible causes:<br>1. Unsupported AlbumAttribute for the album. <br>2. Unsupported AlbumOperationType for the AlbumAttribute. <br>3. Other operation limit. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error.It is recommended to retry and check the logs.<br>Possible causes:1. Database corrupted.2. The file system is abnormal.3. The IPC request timed out. |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## placeBefore

```TypeScript
placeBefore(album: Album): void
```

Places this album before an album.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| album | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Yes | Target album. To place this album to the end, set **album** to null. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## recoverAssets

```TypeScript
recoverAssets(assets: Array<PhotoAsset>): void
```

Restores the assets corresponding to the specified PhotoAsset object array from the trash.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | Yes | Assets to recover. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## recoverAssetsWithUri

```TypeScript
recoverAssetsWithUri(assetUris: Array<string>): void
```

Restores the assets corresponding to the specified URI string array from the trash.

**Since:** 19

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetUris | Array&lt;string&gt; | Yes | Array of URIs of the assets to recover. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| 13900020 | Invalid argument |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| 14000016 | Operation Not Support |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## resetCoverUri

```TypeScript
resetCoverUri(): void
```

Resets the cover.

**Since:** 20

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error.It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](./arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setCoverUri

```TypeScript
setCoverUri(coverUri: string): void
```

Sets the album cover.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| coverUri | string | Yes | URI of the file to be set as the album cover. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setDisplayLevel

```TypeScript
setDisplayLevel(displayLevel: number): void
```

Sets the display level of the portrait album.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayLevel | number | Yes | Display level to set. The options are as follows:<br>**0**: unfavorite the portrait album. <br>**1**: set the portrait album as the first to display. <br>**2**: do not display the portrait album as the first one. <br>**3**: favorite the portrait album. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setIsMe

```TypeScript
setIsMe(): void
```

Sets the relationship between people in the portrait album to **Me**.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

**Examples**

```TypeScript
For details about how to create a phAccessHelper instance, see the example provided in [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper).
```

## setUploadStatus

```TypeScript
static setUploadStatus(context: Context, albums: Album[], allowUpload: boolean): Promise<void>
```

Sets whether the albums can be synced to cloud storage or family storage. This API uses a promise to return the result.

**Since:** 22

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| albums | [Album](arkts-medialibrary-photoaccesshelper-album-i.md)[] | Yes | Array of albums whose sync status is to be set. You can set the sync status for user albums and source albums. The array can contain a maximum of 500 elements. |
| allowUpload | boolean | Yes | Whether the albums can be synced to cloud storage or family storage. **true** if they can be synced, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The context is empty; <br>2. Album array size is bigger than 500. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1.Database corrupted; <br>2.The file system is abnormal; <br>3.The IPC request timed out; |

**Examples**

```TypeScript
async function example(context: Context, album: photoAccessHelper.Album) {
  console.info('setUploadStatusDemo');
  try {
    let allowUpload = true;
    await photoAccessHelper.MediaAlbumChangeRequest.setUploadStatus(context, [album], allowUpload);
    console.info('setUploadStatus successfully');
  } catch (err) {
    console.error(`setUploadStatus failed with error: ${err.code}, ${err.message}`);
  }
}
```
