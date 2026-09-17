# MediaShareAlbumChangeRequest (System API)

Represents a change request for managing the share album.

**Inheritance/Implementation:** MediaShareAlbumChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**Since:** 26.1.0

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## addShareMember

```TypeScript
public addShareMember(owner: string, member: string, status: ShareMemberStatus): void
```

Add member of share Album.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | The OwnerId of share album. |
| member | string | Yes | The member of share album. |
| status | [ShareMemberStatus](arkts-medialibrary-photoaccesshelper-sharememberstatus-e-sys.md) | Yes | The share member status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: 1. The albums are not share album. |

## constructor

```TypeScript
public constructor(album: Album)
```

Constructor used to initialize a new MediaShareAlbumChangeRequest.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| album | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Yes | Share album to change. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: 1. the album is not share album. |

## createShareAlbum

```TypeScript
public static createShareAlbum(context: Context, owner: string, name: string, cloudId: 
      string, lpath: string): MediaShareAlbumChangeRequest|null
```

Creates a MediaShareAlbumChangeRequest instance of creating share album.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| owner | string | Yes | The OwnerId of share album. |
| name | string | Yes | Name of the album. |
| cloudId | string | Yes | The cloudId of share album. |
| lpath | string | Yes | The virtual path of share album. |

**Return value:**

| Type | Description |
| --- | --- |
| [MediaShareAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediasharealbumchangerequest-c-sys.md) &#124; null | Returns a MediaAlbumChangeRequest instance. if the operation fails, returns null. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: 1. The context is null. 2. The album name must meet the following requirements: The total length of the album name must be between 1 and 255 characters. It must not contain any invalid characters, which are: . \ / : * ? " ' ` &lt; &gt; &#124; { } [ ] It is case-insensitive. 3. The lpath does not meet the uniqueness requirement. |

## deleteMemberShareAlbum

```TypeScript
public static deleteMemberShareAlbum(context: Context, owner: string, albums: Album[]): Promise<void>
```

Delete member share album.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| owner | string | Yes | The OwnerId of share album. |
| albums | [Album](arkts-medialibrary-photoaccesshelper-album-i.md)[] | Yes | Array of albums to delete. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The context is null. <br>2. The albums are not share album. <br>3. The operator must be the member of the share album when deleting the local share album. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. You are advised to retry and check the logs. Possible causes: 1. The database is corrupted. 2. The file system is abnormal. 3. The IPC request timed out. |

## deleteShareAlbum

```TypeScript
public static deleteShareAlbum(context: Context, owner: string, albums: Album[]): Promise<void>
```

Delete share album.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| owner | string | Yes | The OwnerId of share album. |
| albums | [Album](arkts-medialibrary-photoaccesshelper-album-i.md)[] | Yes | Array of albums to delete. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The context is null. <br>2. The albums are not share album. <br>3. The operator must be the owner of the share album when deleting the album. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. You are advised to retry and check the logs. Possible causes: 1. The database is corrupted. 2. The file system is abnormal. 3. The IPC request timed out. |

## deleteShareAssets

```TypeScript
public static deleteShareAssets(context: Context, owner: string, assets: string[]): Promise<void>
```

Delete assets of share album.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| owner | string | Yes | The OwnerId of share album. |
| assets | string[] | Yes | Assets to delete. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The context is null. <br>2. The albums are not share album. <br>3. Asset uri array size is empty or bigger than 500. <br>4. When a deleted photo belongs to a shared album, only the album owner or the person who shared the photo can delete it. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error. You are advised to retry and check the logs. Possible causes: 1. The database is corrupted. 2. The file system is abnormal. 3. The IPC request timed out. |

## deleteShareMember

```TypeScript
public deleteShareMember(owner: string, member: string): void
```

delete share member.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | The OwnerId of share album. |
| member | string | Yes | The member of share album. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The albums are not share album. |

## getShareAlbumMemberInfo

```TypeScript
public static getShareAlbumMemberInfo(context: Context, owner: string, 
      album: Album): Promise<ShareAlbumMemberInfo>
```

Get the member information of share album.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| owner | string | Yes | The OwnerId of share album. |
| album | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | Yes | The target album. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ShareAlbumMemberInfo](arkts-medialibrary-photoaccesshelper-sharealbummemberinfo-c-sys.md)&gt; | Promise used to return member information of share album. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes:<br>1. The context is null. <br>2. The albums are not share album. |
| [23800301](../errorcode-medialibrary.md#23800301-system-internal-error) | Internal system error.It is recommended to retry and check the logs.<br>Possible causes:1. Database corrupted.2. The file system is abnormal.3. The IPC request timed out. |

## setShareAlbumName

```TypeScript
public setShareAlbumName(owner: string, name: string): void
```

set the name of share album.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | The OwnerId of share album. |
| name | string | Yes | The name of share album to modified. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: <br>1. The albums are not share album. <br>2. The album name must meet the following requirements: The total length of the album name must be between 1 and 255 characters. It must not contain any invalid characters, which are: . \ / : * ? " ' ` &lt; &gt; &#124; { } [ ] |

## updateShareMemberStatus

```TypeScript
public updateShareMemberStatus(owner: string, member: string, status: ShareMemberStatus): void
```

update share member status.

**Since:** 26.1.0

**Required permissions:** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owner | string | Yes | The OwnerId of share album. |
| member | string | Yes | The member of share album. |
| status | [ShareMemberStatus](arkts-medialibrary-photoaccesshelper-sharememberstatus-e-sys.md) | Yes | The share member status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-failed-to-verify-scene-parameters) | The scenario parameter verification fails. Possible causes: The albums are not share album. |

## comment

```TypeScript
readonly comment: string
```

A readonly member for type checking.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
