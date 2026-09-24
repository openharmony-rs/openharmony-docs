# MediaShareAlbumChangeRequest（系统接口）

```TypeScript
class MediaShareAlbumChangeRequest implements MediaChangeRequest
```

表示管理共享相册的变更请求。

**继承/实现关系：** MediaShareAlbumChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**起始版本：** 26.0.1

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## addShareMember

```TypeScript
public addShareMember(owner: string, member: string, status: ShareMemberStatus): void
```

添加共享相册的成员。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 共享相册的所有者ID。 |
| member | string | 是 | 共享专辑的成员。 |
| status | [ShareMemberStatus](arkts-medialibrary-photoaccesshelper-sharememberstatus-e-sys.md) | 是 | 共享成员状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: 1. The albums are not share album. |

## constructor

```TypeScript
public constructor(album: Album)
```

用于初始化一个新的MediaShareAlbumChangeRequest的构造函数。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| album | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | 是 | Share album to change. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: 1. the album is not share album. |

## createShareAlbum

```TypeScript
public static createShareAlbum(context: Context, owner: string, name: string, cloudId: 
      string, albumConfig: ValuesBucket): MediaShareAlbumChangeRequest|null
```

创建创建共享相册的MediaShareAlbumChangeRequest实例。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 实例上下文。 |
| owner | string | 是 | 共享相册的创建者。 |
| name | string | 是 | 共享相册名称名称。 |
| cloudId | string | 是 | 共享相册的cloudId。 |
| albumConfig | [ValuesBucket](arkts-medialibrary-photoaccesshelper-valuesbucket-t-sys.md) | 是 | The configuration of share album. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaShareAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediasharealbumchangerequest-c-sys.md) &#124; null | 返回一个MediaAlbumChangeRequest实例。如果操作失败，则返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: 1. The context is null. 2. The album name must meet the following requirements: The total length of the album name must be between 1 and 255 characters. It must not contain any invalid characters, which are: . \ / : * ? " ' ` &lt; &gt; &#124; { } [ ]It is case-insensitive. 3. The lpath does not meet the uniqueness requirement. |

## deleteMemberShareAlbum

```TypeScript
public static deleteMemberShareAlbum(context: Context, owner: string, albums: Album[]): Promise<void>
```

删除成员共享相册。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 实例上下文。 |
| owner | string | 是 | 共享相册的所有者ID。 |
| albums | [Album](arkts-medialibrary-photoaccesshelper-album-i.md)[] | 是 | 要删除的相册数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. The context is null. <br>2. The albums are not share album. <br>3. The operator must be the member of the share album when deleting the local share album. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: 1. The database is corrupted. 2. The file system is abnormal. 3. The IPC request timed out. |

## deleteShareAlbum

```TypeScript
public static deleteShareAlbum(context: Context, owner: string, albums: Album[]): Promise<void>
```

删除共享相册。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 实例上下文。 |
| owner | string | 是 | 共享相册的所有者ID。 |
| albums | [Album](arkts-medialibrary-photoaccesshelper-album-i.md)[] | 是 | 要删除的相册数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. The context is null. <br>2. The albums are not share album. <br>3. The operator must be the owner of the share album when deleting the album. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: 1. The database is corrupted. 2. The file system is abnormal. 3. The IPC request timed out. |

## deleteShareAssets

```TypeScript
public static deleteShareAssets(context: Context, owner: string, assets: string[]): Promise<void>
```

删除共享相册的资产。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 实例上下文。 |
| owner | string | 是 | 共享相册的所有者ID。 |
| assets | string[] | 是 | 要删除的资产。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. The context is null. <br>2. The albums are not share album. <br>3. Asset uri array size is empty or bigger than 500. <br>4. When a deleted photo belongs to a shared album, only the album owner or the person who shared the photo can delete it. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: 1. The database is corrupted. 2. The file system is abnormal. 3. The IPC request timed out. |

## deleteShareMember

```TypeScript
public deleteShareMember(owner: string, member: string): void
```

删除共享成员。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 共享相册的所有者ID。 |
| member | string | 是 | 共享相册的成员。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. The albums are not share album. |

## getShareAlbumMemberInfo

```TypeScript
public static getShareAlbumMemberInfo(context: Context, owner: string, 
      album: Album): Promise<ShareAlbumMemberInfo>
```

获取共享相册的成员信息。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 实例上下文。 |
| owner | string | 是 | 共享相册的所有者ID。 |
| album | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | 是 | 目标相册。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ShareAlbumMemberInfo](arkts-medialibrary-photoaccesshelper-sharealbummemberinfo-c-sys.md)&gt; | Promise用于返回共享相册的成员信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. The context is null. <br>2. The albums are not share album. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs.<br>Possible causes:1. Database corrupted.2. The file system is abnormal.3. The IPC request timed out. |

## resetShareCoverUri

```TypeScript
public resetShareCoverUri(owner: string): void
```

重置共享相册的封面。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 共享相册的所有者ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: 1. The albums are not share album. |

## setShareAlbumName

```TypeScript
public setShareAlbumName(owner: string, name: string): void
```

设置共享相册的名称。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 共享相册的所有者ID。 |
| name | string | 是 | 要修改的共享相册名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The albums are not share album. <br>2. The album name must meet the following requirements: The total length of the album name must be between 1 and 255 characters. It must not contain any invalid characters, which are: . \ / : * ? " ' ` &lt; &gt; &#124; { } [ ] |

## setShareCoverUri

```TypeScript
public setShareCoverUri(owner: string, coverUri: string): void
```

设置共享相册的封面

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 共享相册的所有者ID。 |
| coverUri | string | 是 | 共享相册的封面。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: 1. The albums are not share album. |

## updateShareMemberStatus

```TypeScript
public updateShareMemberStatus(owner: string, member: string, status: ShareMemberStatus): void
```

更新共享成员状态。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO and ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| owner | string | 是 | 共享相册的所有者ID。 |
| member | string | 是 | 共享相册的成员。 |
| status | [ShareMemberStatus](arkts-medialibrary-photoaccesshelper-sharememberstatus-e-sys.md) | 是 | 共享成员状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The albums are not share album. |

## comment

```TypeScript
readonly comment: string
```

用于类型检查的只读成员。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
