# Album

实体相册。

**继承/实现关系：** Album extends [AbsAlbum](arkts-medialibrary-photoaccesshelper-absalbum-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## deleteAssets

```TypeScript
deleteAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

从回收站中彻底删除图片或者视频，需要先在回收站中预置文件资源。使用callback异步回调。

> **说明：** 
> 
> 此操作不可逆，执行此操作后文件资源将彻底删除，请谨慎操作。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deleteassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 回收站中待彻底删除图片或者视频数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## deleteAssets

```TypeScript
deleteAssets(assets: Array<PhotoAsset>): Promise<void>
```

从回收站中彻底删除图片或者视频，需要先在回收站中预置文件资源，建议删除数量不超过1000张。使用Promise异步回调。

> **说明：** 
> 
> 此操作不可逆，执行此操作后文件资源将彻底删除，请谨慎操作。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deleteassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 回收站中待彻底删除图片或者视频数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## getAttribute

```TypeScript
getAttribute(attrs: AlbumAttribute[]): Promise<Record<AlbumAttribute, AlbumAttributeInfo>>
```

获取相册属性信息。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attrs | [AlbumAttribute](arkts-medialibrary-photoaccesshelper-albumattribute-e-sys.md)[] | 是 | 相册获取的属性。 最大长度为20且不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;[AlbumAttribute](arkts-medialibrary-photoaccesshelper-albumattribute-e-sys.md), [AlbumAttributeInfo](arkts-medialibrary-photoaccesshelper-albumattributeinfo-i-sys.md)&gt;&gt; | Returns a record of attributes and their values. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1. Unsupported attribute; <br>2. The attrs size exceed 20; <br>3. Empty or duplicate attribute; |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs. Possible causes:<br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## getFaceId

```TypeScript
getFaceId(): Promise<string>
```

获取人像相册或合影相册的封面人脸标识。

**起始版本：** 13

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，人像相册返回tag_id，合影相册返回group_tag，未找到返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## getFusionAssetsInfo

```TypeScript
getFusionAssetsInfo(): Promise<FusionAssetsInfo[]>
```

获取融合资产信息。

**起始版本：** 22

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FusionAssetsInfo](arkts-medialibrary-photoaccesshelper-fusionassetsinfo-i-sys.md)[]&gt; | Returns fusion assets information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs.<br>Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |

## getSelectedAssets

```TypeScript
getSelectedAssets(optionCheck: FetchOptions, filter?: string): Promise<FetchResult<PhotoAsset>>
```

获取符合系统预设筛选条件的人像相册资产。

**起始版本：** 22

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| optionCheck | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项，限制返回资产数量。 |
| filter | string | 否 | 过滤选项，必须是一个Json字符串<br>过滤选项，必须是一个Json字符串。<br>当前仅支持传递currentFileId，表示当前精选人像卡片展示图片的file_id。例如:'{"currentFileId":"123"}'。<br>&gt;如果不填写，则从头开始返回资产。<br>如果填写了currentFileId，则根据该currentFileId内部计算评分，返回评分小于或等于该评分的资产。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[FetchResult](arkts-medialibrary-photoaccesshelper-fetchresult-i.md)&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt;&gt; | Promise对象，返回获取的图片结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails.<br>Possible causes: 1. The input parameter is not within the valid range. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs.<br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## recoverAssets

```TypeScript
recoverAssets(assets: Array<PhotoAsset>, callback: AsyncCallback<void>): void
```

从回收站中恢复图片或者视频，需要先在回收站中预置文件资源。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [recoverAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#recoverassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 回收站中待恢复图片或者视频数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## recoverAssets

```TypeScript
recoverAssets(assets: Array<PhotoAsset>): Promise<void>
```

从回收站中恢复图片或者视频，需要先在回收站中预置文件资源。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [recoverAssets](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#recoverassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;[PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md)&gt; | 是 | 回收站中待恢复图片或者视频数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## setCoverUri

```TypeScript
setCoverUri(uri: string, callback: AsyncCallback<void>): void
```

设置用户相册封面。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [setCoverUri](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#setcoveruri)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待设置为相册封面文件的uri。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## setCoverUri

```TypeScript
setCoverUri(uri: string): Promise<void>
```

设置用户相册封面。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [setCoverUri](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#setcoveruri)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待设置为相册封面文件的uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

**示例**

```TypeScript
phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。
```

## dateAdded

```TypeScript
readonly dateAdded?: number
```

相册添加时间，单位：秒。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateModified

```TypeScript
readonly dateModified?: number
```

相册修改时间，单位：秒。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
