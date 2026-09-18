# AbsAlbum (System API)

Defines the AbsAlbum.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [AbsAlbum](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-absalbum-i.md)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## getPhotoAssets

```TypeScript
getPhotoAssets(options: FetchOptions, callback: AsyncCallback<FetchResult<FileAsset>>): void
```

Obtains image and video assets. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-absalbum-i.md#getassets)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Yes | Retrieval options. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt;&gt; | Yes | Callback used to return the image and video assets obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not FetchOptions |

## getPhotoAssets

```TypeScript
getPhotoAssets(options: FetchOptions): Promise<FetchResult<FileAsset>>
```

Obtains image and video assets. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-absalbum-i.md#getassets)

**Required permissions:** ohos.permission.READ_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Yes | Retrieval options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md)&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt;&gt; | Promise that returns the image and video assets obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if type options is not FetchOptions |

## albumName

```TypeScript
albumName: string
```

Name of the album.

> **NOTE:** 
> 
> The user album is writable, but the system album is not writable.

**Type:** string

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [albumName](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-absalbum-i.md#albumname)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## albumSubType

```TypeScript
readonly albumSubType: AlbumSubType
```

Subtype of the album.

**Type:** [AlbumSubType](arkts-corefile-userfilemanager-albumsubtype-e-sys.md)

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** albumSubType

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## albumType

```TypeScript
readonly albumType: AlbumType
```

Type of the album to obtain.

**Type:** [AlbumType](arkts-corefile-userfilemanager-albumtype-e-sys.md)

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [albumType](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-absalbum-i.md#albumtype)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## albumUri

```TypeScript
readonly albumUri: string
```

URI of the album.

**Type:** string

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [albumUri](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-absalbum-i.md#albumuri)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## count

```TypeScript
readonly count: number
```

Number of files in the album.

**Type:** number

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [count](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-absalbum-i.md#count)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## coverUri

```TypeScript
coverUri: string
```

URI of the cover file of the album.

> **NOTE:** 
> 
> The user album is writable, but the system album is not writable.

**Type:** string

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [coverUri](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-absalbum-i.md#coveruri)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## dateModified

```TypeScript
readonly dateModified: number
```

Time when the album was modified. Unit: ms, The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [dateModified](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-album-i-sys.md#datemodified)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.
