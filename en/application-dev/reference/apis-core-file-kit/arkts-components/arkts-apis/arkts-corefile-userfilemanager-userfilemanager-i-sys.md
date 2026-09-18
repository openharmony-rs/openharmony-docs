# UserFileManager (System API)

Defines the UserFileManager class and provides functions to access the data in user file storage.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [PhotoAccessHelper](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## createAlbum

```TypeScript
createAlbum(name: string, callback: AsyncCallback<Album>): void
```

Creates an album. This API uses an asynchronous callback to return the result.

The album name must meet the following requirements:

- The album name is a string of 1 to 255 characters.  
- The album name cannot contain any of the following characters:

. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

- The album name is case-insensitive.  
- Duplicate album names are not allowed.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [createAlbumRequest](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#createalbumrequest)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the album to create. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Album](arkts-corefile-userfilemanager-album-i-sys.md)&gt; | Yes | Callback used to return the created album instance. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## createAlbum

```TypeScript
createAlbum(name: string): Promise<Album>
```

Creates an album. This API uses a promise to return the result.

The album name must meet the following requirements:

- The album name is a string of 1 to 255 characters.  
- The album name cannot contain any of the following characters:

. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

- The album name is case-insensitive.  
- Duplicate album names are not allowed.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [createAlbumRequest](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#createalbumrequest)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the album to create. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Album](arkts-corefile-userfilemanager-album-i-sys.md)&gt; | Promise that returns the created album instance. |

**Examples**

See [createAlbum](#createalbum)

## createAudioAsset

```TypeScript
createAudioAsset(displayName: string, callback: AsyncCallback<FileAsset>): void
```

Creates an audio asset. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Required permissions:** ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayName | string | Yes | File name of the audio asset to create. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Callback used to return the created audio asset. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type displayName is not string |
| 14000001 | if type displayName invalid |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## createAudioAsset

```TypeScript
createAudioAsset(displayName: string): Promise<FileAsset>
```

Creates an audio asset. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Required permissions:** ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayName | string | Yes | File name of the audio asset to create. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Promise that returns the created audio asset. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type displayName is not string |

**Examples**

See [createAudioAsset](#createaudioasset)

## createPhotoAsset

```TypeScript
createPhotoAsset(displayName: string, albumUri: string, callback: AsyncCallback<FileAsset>): void
```

Creates an image or video asset with the specified file name and URI. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [createAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#createasset)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayName | string | Yes | File name of the image or video to create. |
| albumUri | string | Yes | URI of the album where the image or video is located. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Callback used to return the image or video created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type displayName or albumUri is not string |
| 14000001 | if type displayName invalid |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## createPhotoAsset

```TypeScript
createPhotoAsset(displayName: string, callback: AsyncCallback<FileAsset>): void
```

Creates an image or video asset with the specified file name. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [createAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#createasset)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayName | string | Yes | File name of the image or video to create. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Callback used to return the image or video created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type displayName is not string |
| 14000001 | if type displayName invalid |

**Examples**

See [createPhotoAsset](#createphotoasset)

## createPhotoAsset

```TypeScript
createPhotoAsset(displayName: string, albumUri?: string): Promise<FileAsset>
```

Creates an image or video asset with the specified file name and album URI. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [createAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#createasset)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayName | string | Yes | File name of the image or video to create. |
| albumUri | string | No | URI of the album where the image or video is located. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Promise that returns the created image or video asset. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type displayName or albumUri is not string |

**Examples**

See [createPhotoAsset](#createphotoasset)

## createPhotoAsset

```TypeScript
createPhotoAsset(displayName: string, createOption: PhotoCreateOptions): Promise<FileAsset>
```

Creates an image or video asset with the specified file name and options. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [createAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#createasset)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayName | string | Yes | File name of the image or video to create. |
| createOption | [PhotoCreateOptions](arkts-corefile-userfilemanager-photocreateoptions-i-sys.md) | Yes | Options for creating an image or video asset. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Promise that returns the created image or video asset. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type displayName is not string |

**Examples**

See [createPhotoAsset](#createphotoasset)

## createPhotoAsset

```TypeScript
createPhotoAsset(displayName: string, createOption: PhotoCreateOptions, callback: AsyncCallback<FileAsset>): void
```

Creates an image or video asset with the specified file name and options. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [createAsset](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#createasset)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displayName | string | Yes | File name of the image or video to create. |
| createOption | [PhotoCreateOptions](arkts-corefile-userfilemanager-photocreateoptions-i-sys.md) | Yes | Options for creating an image or video asset. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Callback used to return the image or video created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type displayName is not string |
| 14000001 | if type displayName invalid |

**Examples**

See [createPhotoAsset](#createphotoasset)

## delete

```TypeScript
delete(uri: string, callback: AsyncCallback<void>): void
```

Deletes a media file. This API uses an asynchronous callback to return the result. The deleted file is moved to the recycle bin. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [deleteAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#deleteassets)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO and ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.READ_AUDIO and ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the media file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type uri is not string |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## delete

```TypeScript
delete(uri: string): Promise<void>
```

Deletes media assets. The deleted assets are moved to the trash. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [deleteAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#deleteassets)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO and ohos.permission.WRITE_IMAGEVIDEO or ohos.permission.READ_AUDIO and ohos.permission.WRITE_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the media file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type uri is not string |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## deleteAlbums

```TypeScript
deleteAlbums(albums: Array<Album>, callback: AsyncCallback<void>): void
```

Deletes user albums. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [deleteAlbums](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deletealbums)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| albums | Array&lt;[Album](arkts-corefile-userfilemanager-album-i-sys.md)&gt; | Yes | Albums to delete. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## deleteAlbums

```TypeScript
deleteAlbums(albums: Array<Album>): Promise<void>
```

Deletes user albums. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [deleteAlbums](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deletealbums)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| albums | Array&lt;[Album](arkts-corefile-userfilemanager-album-i-sys.md)&gt; | Yes | Albums to delete. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [deleteAlbums](#deletealbums)

## getActivePeers

```TypeScript
getActivePeers(callback: AsyncCallback<Array<PeerInfo>>): void
```

Obtains information about online peer devices. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**System capability:** SystemCapability.FileManagement.UserFileManager.DistributedCore

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[PeerInfo](arkts-corefile-userfilemanager-peerinfo-i-sys.md)&gt;&gt; | Yes | Callback used to return a list of online peer devices. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## getActivePeers

```TypeScript
getActivePeers(): Promise<Array<PeerInfo>>
```

Obtains the information about online peer devices. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**System capability:** SystemCapability.FileManagement.UserFileManager.DistributedCore

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PeerInfo](arkts-corefile-userfilemanager-peerinfo-i-sys.md)&gt;&gt; | Promise that returns a list of online peer devices. |

**Examples**

See [getActivePeers](#getactivepeers)

## getAlbums

```TypeScript
getAlbums(
      type: AlbumType,
      subType: AlbumSubType,
      options: FetchOptions,
      callback: AsyncCallback<FetchResult<Album>>
    ): void
```

Obtains albums based on the specified options and album type. This API uses an asynchronous callback to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#gethiddenalbums) to obtain hidden albums.

Before the operation, ensure that the albums to obtain exist.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** getAlbums

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AlbumType](arkts-corefile-userfilemanager-albumtype-e-sys.md) | Yes | Type of the album to obtain. |
| subType | [AlbumSubType](arkts-corefile-userfilemanager-albumsubtype-e-sys.md) | Yes | Subtype of the album. |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Yes | Retrieval options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[Album](arkts-corefile-userfilemanager-album-i-sys.md)&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not FetchOption |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## getAlbums

```TypeScript
getAlbums(type: AlbumType, subType: AlbumSubType, callback: AsyncCallback<FetchResult<Album>>): void
```

Obtains albums by type. This API uses an asynchronous callback to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#gethiddenalbums) to obtain hidden albums.

Before the operation, ensure that the albums to obtain exist.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** getAlbums

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AlbumType](arkts-corefile-userfilemanager-albumtype-e-sys.md) | Yes | Type of the album to obtain. |
| subType | [AlbumSubType](arkts-corefile-userfilemanager-albumsubtype-e-sys.md) | Yes | Subtype of the album. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[Album](arkts-corefile-userfilemanager-album-i-sys.md)&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not FetchOption |

**Examples**

See [getAlbums](#getalbums)

## getAlbums

```TypeScript
getAlbums(type: AlbumType, subType: AlbumSubType, options?: FetchOptions): Promise<FetchResult<Album>>
```

Obtains albums based on the specified options and album type. This API uses a promise to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#gethiddenalbums) to obtain hidden albums.

Before the operation, ensure that the albums to obtain exist.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** getAlbums

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AlbumType](arkts-corefile-userfilemanager-albumtype-e-sys.md) | Yes | Type of the album to obtain. |
| subType | [AlbumSubType](arkts-corefile-userfilemanager-albumsubtype-e-sys.md) | Yes | Subtype of the album. |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | No | Options for fetching the albums. If this parameter is not specified, the albums are obtained based on the album type by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[Album](arkts-corefile-userfilemanager-album-i-sys.md)&gt;&gt; | Promise that returns the albums. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not FetchOption |

**Examples**

See [getAlbums](#getalbums)

## getAllPeers

```TypeScript
getAllPeers(callback: AsyncCallback<Array<PeerInfo>>): void
```

Obtains information about all peer devices. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**System capability:** SystemCapability.FileManagement.UserFileManager.DistributedCore

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[PeerInfo](arkts-corefile-userfilemanager-peerinfo-i-sys.md)&gt;&gt; | Yes | Callback used to return a list of online peer devices. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## getAllPeers

```TypeScript
getAllPeers(): Promise<Array<PeerInfo>>
```

Obtains the information about all peer devices. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**System capability:** SystemCapability.FileManagement.UserFileManager.DistributedCore

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PeerInfo](arkts-corefile-userfilemanager-peerinfo-i-sys.md)&gt;&gt; | Promise that returns the information obtained. |

**Examples**

See [getAllPeers](#getallpeers)

## getAudioAssets

```TypeScript
getAudioAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<FileAsset>>): void
```

Obtains audio assets. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Required permissions:** ohos.permission.READ_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Yes | Retrieval options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt;&gt; | Yes | Callback used to return the audio assets obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not FetchOptions |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## getAudioAssets

```TypeScript
getAudioAssets(options: FetchOptions): Promise<FetchResult<FileAsset>>
```

Obtains an audio asset. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Required permissions:** ohos.permission.READ_AUDIO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Yes | Retrieval options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt;&gt; | Promise that returns the audio assets obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not FetchOptions |

**Examples**

See [getAudioAssets](#getaudioassets)

## getPhotoAlbums

```TypeScript
getPhotoAlbums(options: AlbumFetchOptions, callback: AsyncCallback<FetchResult<Album>>): void
```

Obtains image and video albums. This API uses an asynchronous callback to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#gethiddenalbums) to obtain hidden albums.

This API will be deprecated. Use [getAlbums](#getalbums) instead.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getAlbums](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getalbums)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AlbumFetchOptions](arkts-corefile-userfilemanager-albumfetchoptions-i-sys.md) | Yes | Options for fetching the albums. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[Album](arkts-corefile-userfilemanager-album-i-sys.md)&gt;&gt; | Yes | Callback used to return the albums obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not AlbumFetchOptions |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## getPhotoAlbums

```TypeScript
getPhotoAlbums(options: AlbumFetchOptions): Promise<FetchResult<Album>>
```

Obtains albums. This API uses a promise to return the result.

This API cannot be used to obtain hidden albums. Use [getHiddenAlbums](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#gethiddenalbums) to obtain hidden albums.

This API will be deprecated. Use [getAlbums](#getalbums) instead.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getAlbums](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getalbums)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [AlbumFetchOptions](arkts-corefile-userfilemanager-albumfetchoptions-i-sys.md) | Yes | Options for fetching the albums. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[Album](arkts-corefile-userfilemanager-album-i-sys.md)&gt;&gt; | Promise that returns the albums obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not AlbumFetchOptions |

**Examples**

See [getPhotoAlbums](#getphotoalbums)

## getPhotoAssets

```TypeScript
getPhotoAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<FileAsset>>): void
```

Obtains image and video assets. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Yes | Options for fetching the image and video assets. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt;&gt; | Yes | Callback used to return the image and video assets obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not FetchOptions |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## getPhotoAssets

```TypeScript
getPhotoAssets(options: FetchOptions): Promise<FetchResult<FileAsset>>
```

Obtains image and video assets. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#getassets)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Yes | Options for fetching the image and video assets. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt;&gt; | Promise that returns the image and video assets obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not FetchOptions |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## getPhotoIndex

```TypeScript
getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions, callback: AsyncCallback<number>): void
```

Obtains the index of an image or video in an album. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getPhotoIndex](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#getphotoindex)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| photoUri | string | Yes | URI of the media asset whose index is to be obtained. |
| albumUri | string | Yes | Album URI, which can be an empty string. If it is an empty string, all the media assets in the Gallery are obtained by default. |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Yes | Retrieval options. Only one search condition or sorting mode must be set in **predicates**. If no value is set or multiple search criteria or sorting modes are set, the API cannot be called successfully. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the index obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## getPhotoIndex

```TypeScript
getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions): Promise<number>
```

Obtains the index of an image or video in an album. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getPhotoIndex](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#getphotoindex)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| photoUri | string | Yes | URI of the media asset whose index is to be obtained. |
| albumUri | string | Yes | Album URI, which can be an empty string. If it is an empty string, all the media assets in the Gallery are obtained by default. |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Yes | Retrieval options. Only one search condition or sorting mode must be set in **predicates**. If no value is set or multiple search criteria or sorting modes are set, the API cannot be called successfully. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise that returns the index obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |

**Examples**

See [getPhotoIndex](#getphotoindex)

## getPrivateAlbum

```TypeScript
getPrivateAlbum(type: PrivateAlbumType, callback: AsyncCallback<FetchResult<PrivateAlbum>>): void
```

Obtains the system album. This API uses an asynchronous callback to return the result.

This API will be deprecated. Use [getAlbums](#getalbums) instead.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** getAlbums

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [PrivateAlbumType](arkts-corefile-userfilemanager-privatealbumtype-e-sys.md) | Yes | Type of the system album to obtain. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[PrivateAlbum](arkts-corefile-userfilemanager-privatealbum-i-sys.md)&gt;&gt; | Yes | Callback used to return the albums obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type type is not PrivateAlbumType |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## getPrivateAlbum

```TypeScript
getPrivateAlbum(type: PrivateAlbumType): Promise<FetchResult<PrivateAlbum>>
```

Obtains the private album. This API uses a promise to return the result.

This API will be deprecated. Use [getAlbums](#getalbums) instead.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** getAlbums

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [PrivateAlbumType](arkts-corefile-userfilemanager-privatealbumtype-e-sys.md) | Yes | Type of the system album to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[PrivateAlbum](arkts-corefile-userfilemanager-privatealbum-i-sys.md)&gt;&gt; | Promise that returns the albums obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type type is not PrivateAlbumType |

**Examples**

See [getPrivateAlbum](#getprivatealbum)

## off

```TypeScript
off(type: ChangeEvent, callback?: Callback<void>): void
```

Unsubscribes from changes of the file management library. This API uses a callback to return the result.

This API will be deprecated. Use [off](#off-1) instead.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [off](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#offmedialibraryavailability)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ChangeEvent](arkts-corefile-userfilemanager-changeevent-t-sys.md) | Yes | Type of event to subscribe to.<br>**'deviceChange'**: device change. <br>**'albumChange'**: album change. <br>**'imageChange'**: image change. <br>**'audioChange'**: audio file change. <br>**'videoChange'**: video file change. <br>**'remoteFileChange'**: change of the file on a registered device. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## off

```TypeScript
off(uri: string, callback?: Callback<ChangeData>): void
```

Unregisters the listener for the specified URI. Multiple callbacks can be registered for a URI for listening. You can use this API to unregister the specified callbacks or all callbacks.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** unregisterChange

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file asset or album, or [DefaultChangeUri](arkts-corefile-userfilemanager-defaultchangeuri-e-sys.md). |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeData](arkts-corefile-cloudsync-changedata-i.md)&gt; | No | Callback registered by [on](#on-1). If this parameter is not specified, all listener callbacks registered for the URI will be unregistered. <br>Note that the specified callback will not be invoked. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if parameter is invalid |

**Examples**

See [off](#off)

## on

```TypeScript
on(type: ChangeEvent, callback: Callback<void>): void
```

Subscribes to changes of the file management library. This API uses a callback to return the result.

This API will be deprecated. Use [on](#on-1) instead.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [on](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#onmedialibraryavailability)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ChangeEvent](arkts-corefile-userfilemanager-changeevent-t-sys.md) | Yes | Type of event to subscribe to.<br>**'deviceChange'**: device change. <br>**'albumChange'**: album change. <br>**'imageChange'**: image change. <br>**'audioChange'**: audio file change. <br>**'videoChange'**: video file change. <br>**'remoteFileChange'**: change of the file on a registered device. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## on

```TypeScript
on(uri: string, forSubUri: boolean, callback: Callback<ChangeData>): void
```

Registers a listener for the specified URI. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [registerChange](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#registerchange)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file asset or album, or [DefaultChangeUri](arkts-corefile-userfilemanager-defaultchangeuri-e-sys.md). |
| forSubUri | boolean | Yes | Whether to perform fuzzy listening.<br>If **uri** is the URI of the album, the value **true** means to listen for the file change in the album; the value **false** means to listen for the album change only. If **uri** is the URI of the file asset, there is no difference whether **forSubUri** is **true** or **false**. If **uri** is **DefaultChangeUri**, the value must be **true**, otherwise, the URI cannot be found and no message can be received. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeData](arkts-corefile-cloudsync-changedata-i.md)&gt; | Yes | Callback used to return [ChangeData](arkts-corefile-userfilemanager-changedata-i-sys.md). <br>Note that different callbacks can be registered for a URI. You can use [off](#off-1) to disable the specified callback or all callbacks for the URI. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if parameter is invalid |

**Examples**

See [on](#on)

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this **UserFileManager** instance. This API uses an asynchronous callback to return the result.

Call this API when the APIs in the **UserFileManager** instance are no longer used.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [release](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#release)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in [userFileManager.getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md).
```

## release

```TypeScript
release(): Promise<void>
```

Releases this **UserFileManager** instance. This API uses a promise to return the result.

Call this API when the APIs in the **UserFileManager** instance are no longer used.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [release](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#release)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [release](#release)
