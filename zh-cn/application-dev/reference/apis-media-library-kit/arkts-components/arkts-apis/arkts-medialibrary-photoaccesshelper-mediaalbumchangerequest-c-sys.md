# MediaAlbumChangeRequest

MediaAlbumChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md).

相册变更请求。

> **说明：** 
> 
> - 本Class首批接口从API version 11开始支持。

**继承/实现关系：** MediaAlbumChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## createAlbumRequest

```TypeScript
static createAlbumRequest(context: Context, name: string): MediaAlbumChangeRequest
```

创建相册变更请求。

相册名的参数规格为：

- 相册名字符串长度为1~255。  
- 不允许出现的非法英文字符，包括：

. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

- 英文字符大小写不敏感。  
- 相册名不允许重名。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| name | string | 是 | 待创建相册的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md) | 返回创建相册的变更请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## deleteAlbums

```TypeScript
static deleteAlbums(context: Context, albums: Array<Album>): Promise<void>
```

删除存在的用户相册。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| albums | Array&lt;[Album](arkts-medialibrary-photoaccesshelper-album-i.md)&gt; | 是 | 待删除的相册数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## deleteAlbumsWithUri

```TypeScript
static deleteAlbumsWithUri(context: Context, albumUris: Array<string>): Promise<void>
```

删除已存在的用户相册。使用promise异步回调。

**起始版本：** 19

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| albumUris | Array&lt;string&gt; | 是 | 待删除相册Uri的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 13900020 | Invalid argument |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out; |

**示例**

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

从回收站中彻底删除资产。

> **注意：**
> 
> 此操作不可逆，执行此操作后文件资源将彻底删除，请谨慎操作。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 待从回收站中彻底删除的资产数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## deleteAssetsWithUri

```TypeScript
deleteAssetsWithUri(assetUris: Array<string>): void
```

从回收站中彻底删除资产。

> **注意：**
> 
> 此操作不可逆，执行此操作后文件资源将被彻底删除，请谨慎操作。

**起始版本：** 19

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetUris | Array&lt;string&gt; | 是 | 待从回收站中彻底删除的资产Uri数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 13900020 | Invalid argument |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| 14000016 | Operation Not Support |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## dismiss

```TypeScript
dismiss(): void
```

删除合影相册。

**起始版本：** 13

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## dismissAssets

```TypeScript
dismissAssets(assets: Array<PhotoAsset>): void
```

从该人像相册或合影相册中移除指定图片。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 需要移除的文件列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## mergeAlbum

```TypeScript
mergeAlbum(target: Album): void
```

将两个人像相册合并。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | 是 | 需要合并的目标相册，合并相册必须重命名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## moveAssets

```TypeScript
moveAssets(assets: Array<PhotoAsset>, targetAlbum: Album): void
```

从相册中移动资产到另一个目标相册。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 待从相册中移出的资产数组。 |
| targetAlbum | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | 是 | 待移入资产的目标相册。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## moveAssetsWithUri

```TypeScript
moveAssetsWithUri(assetUris: Array<string>, targetAlbum: Album): void
```

把相册中的资产移动到另一个目标相册。

**起始版本：** 19

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetUris | Array&lt;string&gt; | 是 | 待从相册中移出的资产Uri数组。 |
| targetAlbum | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | 是 | 待移入资产的目标相册。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 13900020 | Invalid argument |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| 14000016 | Operation Not Support |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## operateAttribute

```TypeScript
operateAttribute(operation: AlbumOperation): void
```

操作相册属性。

**起始版本：** 26.0.0

**需要权限：** 
- API版本26：ohos.permission.ACCESS_MEDIALIB_THUMB_DB
- API版本26+：ohos.permission.ACCESS_MEDIALIB_THUMB_DB or ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| operation | [AlbumOperation](arkts-medialibrary-photoaccesshelper-albumoperation-i-sys.md) | 是 | 为相册执行的操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. The attr of operation is invalid; <br>2. The type of operation is invalid; <br>3. The values of operation is incorrect; |
| [23800201](../errorcode-medialibrary.md#23800201-不支持的操作类型) | Unsupported operation type. It is recommended to check the logs. Possible causes:<br>1. Unsupported AlbumAttribute for the album. <br>2. Unsupported AlbumOperationType for the AlbumAttribute. <br>3. Other operation limit. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs.<br>Possible causes:1. Database corrupted.2. The file system is abnormal.3. The IPC request timed out. |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## placeBefore

```TypeScript
placeBefore(album: Album): void
```

将当前相册排序到目标相册之前。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| album | [Album](arkts-medialibrary-photoaccesshelper-album-i.md) | 是 | 目标相册。如果要将当前相册排序到末位，则目标相册传入null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## recoverAssets

```TypeScript
recoverAssets(assets: Array<PhotoAsset>): void
```

从回收站中恢复指定的PhotoAsset对象数组所对应的资产。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 待从回收站中恢复的资产数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |
| 14000016 | Operation Not Support |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## recoverAssetsWithUri

```TypeScript
recoverAssetsWithUri(assetUris: Array<string>): void
```

从回收站中恢复指定的URI字符串数组所对应的资产。

**起始版本：** 19

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetUris | Array&lt;string&gt; | 是 | 待从回收站中恢复的资产Uri数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 13900020 | Invalid argument |
| 14000011 | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| 14000016 | Operation Not Support |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## resetCoverUri

```TypeScript
resetCoverUri(): void
```

恢复默认封面。

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](./arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## setAlbumNameByFile

```TypeScript
setAlbumNameByFile(name: string): void
```

设置相册名称，支持文管规则的.命名

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 相册名。<br>取值范围:1-255 <br>相册名参数规格：相册名字符串长度为1~255。不允许出现的非法英文字符，包括：\ / : * ? " ' ` &lt; &gt; &#124; { } [ ]不允许仅命名为.或者..英文字符大小写不敏感。相册名不允许重名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. The album is not exist; |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## setCoverUri

```TypeScript
setCoverUri(coverUri: string): void
```

设置相册封面。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| coverUri | string | 是 | 待设置为相册封面文件的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## setDisplayLevel

```TypeScript
setDisplayLevel(displayLevel: number): void
```

设置人像相册的显示级别。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayLevel | number | 是 | 设置人像相册的显示级别，<br>0：取消该人像相册收藏；<br>1：设置人像相册为首届面；<br>2：设置人像相册为更多界面；<br>3：设置人像相册为收藏界面。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## setHiddenAttribute

```TypeScript
setHiddenAttribute(hiddenState: boolean, isInherited: boolean): void
```

设置相册的UI隐藏属性

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hiddenState | boolean | 是 | 是否隐藏状态<br>相册的UI隐藏状态 |
| isInherited | boolean | 是 | 目录下所有文件或者子文件是否继承UI隐藏属性<br>是否所有子文件或者子目录是否继承 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. The ablum is not exist; |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## setIsMe

```TypeScript
setIsMe(): void
```

将人像相册的人物关系设置为“我”。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## setUploadStatus

```TypeScript
static setUploadStatus(context: Context, albums: Album[], allowUpload: boolean): Promise<void>
```

设置相册是否可以同步到云空间或家庭存储。使用promise异步回调。

**起始版本：** 22

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |
| albums | [Album](arkts-medialibrary-photoaccesshelper-album-i.md)[] | 是 | 待设置同步状态的相册数组，支持设置用户相册和来源相册，数组中元素个数不超过500个。 |
| allowUpload | boolean | 是 | 是否允许相册同步，true表示允许，false表示不允许。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. The context is empty; <br>2. Album array size is bigger than 500. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:<br>1.Database corrupted; <br>2.The file system is abnormal; <br>3.The IPC request timed out; |

**示例**

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
