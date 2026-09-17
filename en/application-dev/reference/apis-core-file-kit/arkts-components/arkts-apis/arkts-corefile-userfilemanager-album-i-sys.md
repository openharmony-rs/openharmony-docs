# Album (System API)

Provides APIs to manage albums.

**Inheritance/Implementation:** Album extends [AbsAlbum](arkts-corefile-userfilemanager-absalbum-i-sys.md)

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [Album](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-album-i.md)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## addPhotoAssets

```TypeScript
addPhotoAssets(assets: Array<FileAsset>, callback: AsyncCallback<void>): void
```

Adds image and video assets to an album. Before the operation, ensure that the image and video assets to add and the album exist. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [addAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#addassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Array of the image and video assets to add. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if PhotoAssets is invalid |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## addPhotoAssets

```TypeScript
addPhotoAssets(assets: Array<FileAsset>): Promise<void>
```

Adds image and video assets to an album. Before the operation, ensure that the image and video assets to add and the album exist. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [addAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#addassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Array of the image and video assets to add. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if PhotoAssets is invalid |

**Examples**

See [addPhotoAssets](#addphotoassets)

## commitModify

```TypeScript
commitModify(callback: AsyncCallback<void>): void
```

Commits the modification on the album attributes to the database. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [commitModify](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-album-i.md#commitmodify)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## commitModify

```TypeScript
commitModify(): Promise<void>
```

Commits the modification on the album attributes to the database. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [commitModify](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-album-i.md#commitmodify)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## deletePhotoAssets

```TypeScript
deletePhotoAssets(assets: Array<FileAsset>, callback: AsyncCallback<void>): void
```

Deletes image or video assets from the recycle bin. Before the operation, ensure that the image or video assets exist in the recycle bin. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This operation is irreversible. The assets deleted cannot be restored. Exercise caution when performing this
> operation.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [deleteAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deleteassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Array of the image or video assets to delete. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if PhotoAssets is invalid |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## deletePhotoAssets

```TypeScript
deletePhotoAssets(assets: Array<FileAsset>): Promise<void>
```

Deletes image or video assets from the recycle bin. Before the operation, ensure that the image or video assets exist in the recycle bin. This API uses a promise to return the result.

> **NOTE:** 
> 
> This operation is irreversible. The assets deleted cannot be restored. Exercise caution when performing this
> operation.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [deleteAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deleteassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Array of the image or video assets to delete. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if PhotoAssets is invalid |

**Examples**

See [deletePhotoAssets](#deletephotoassets)

## recoverPhotoAssets

```TypeScript
recoverPhotoAssets(assets: Array<FileAsset>, callback: AsyncCallback<void>): void
```

Recovers image or video assets from the recycle bin. Before the operation, ensure that the image or video assets exist in the recycle bin. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [recoverAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-album-i-sys.md#recoverassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Array of the image or video assets to recover. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if PhotoAssets is invalid |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## recoverPhotoAssets

```TypeScript
recoverPhotoAssets(assets: Array<FileAsset>): Promise<void>
```

Recovers image or video assets from the recycle bin. Before the operation, ensure that the image or video assets exist in the recycle bin. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [recoverAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-album-i-sys.md#recoverassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Array of the image or video assets to recover. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if PhotoAssets is invalid |

**Examples**

See [recoverPhotoAssets](#recoverphotoassets)

## removePhotoAssets

```TypeScript
removePhotoAssets(assets: Array<FileAsset>, callback: AsyncCallback<void>): void
```

Removes image and video assets from an album. The album and file resources must exist. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [removeAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#removeassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Array of the image and video assets to remove. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if PhotoAssets is invalid |

**Examples**

```TypeScript
For details about how to create a userFileManager instance, see the example in userFileManager.getUserFileMgr.
```

## removePhotoAssets

```TypeScript
removePhotoAssets(assets: Array<FileAsset>): Promise<void>
```

Removes image and video assets from an album. The album and file resources must exist. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [removeAssets](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md#removeassets)

**Required permissions:** ohos.permission.WRITE_IMAGEVIDEO

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assets | Array&lt;[FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md)&gt; | Yes | Array of the image and video assets to remove. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900020 | if PhotoAssets is invalid |

**Examples**

See [removePhotoAssets](#removephotoassets)
