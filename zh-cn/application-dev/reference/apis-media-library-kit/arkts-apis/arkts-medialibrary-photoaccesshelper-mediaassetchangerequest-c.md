# MediaAssetChangeRequest

MediaAssetChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md). 资产变更请求。 > **说明：** > > - 本Class首批接口从API version 11开始支持。

**继承/实现关系：** MediaAssetChangeRequest implements [MediaChangeRequest](arkts-medialibrary-photoaccesshelper-mediachangerequest-i.md)

**起始版本：** 23

<!--Device-photoAccessHelper-class MediaAssetChangeRequest--><!--Device-photoAccessHelper-class MediaAssetChangeRequest-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## addResource

```TypeScript
addResource(type: ResourceType, fileUri: string): void
```

通过文件URI从应用沙箱添加资源，待添加资源的数据来源可参考 [@ohos.file.fileuri (File URI)](../../apis-core-file-kit/arkts-apis/arkts-file-fileuri.md). > **注意：** > > 对于同一个资产变更请求，成功添加资源后不支持重复调用该接口。对于动态照片，可调用两次该接口分别添加图片和视频资源。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-addResource(type: ResourceType, fileUri: string): void--><!--Device-MediaAssetChangeRequest-addResource(type: ResourceType, fileUri: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | ResourceType | 是 | 待添加资源的类型。 |
| fileUri | string | 是 | 待添加资源的数据来源，在应用沙箱下的uri。示例fileUri：'file://com.example.temptest/data/storage/el2/base/ haps/entry/files/test.jpg'。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000016 | Operation Not Support |
| 13900002 | The file corresponding to the URI is not in the app sandbox. |
| 14000011 | System inner fail |

## addResource

```TypeScript
addResource(type: ResourceType, data: ArrayBuffer): void
```

通过ArrayBuffer数据添加资源。 > **注意：** > > 对于同一个资产变更请求，成功添加资源后不支持重复调用该接口。对于动态照片，可调用两次该接口分别添加图片和视频资源。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-addResource(type: ResourceType, data: ArrayBuffer): void--><!--Device-MediaAssetChangeRequest-addResource(type: ResourceType, data: ArrayBuffer): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | ResourceType | 是 | 待添加资源的类型。 |
| data | ArrayBuffer | 是 | 待添加资源的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000016 | Operation Not Support |
| 14000011 | System inner fail |

## constructor

```TypeScript
constructor(asset: PhotoAsset)
```

构造函数，用于初始化资产变更请求。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-constructor(asset: PhotoAsset)--><!--Device-MediaAssetChangeRequest-constructor(asset: PhotoAsset)-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| asset | PhotoAsset | 是 | 需要变更的资产。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

## createAssetRequest

```TypeScript
static createAssetRequest(context: Context, photoType: PhotoType, extension: string, options?: CreateOptions): MediaAssetChangeRequest
```

指定文件类型和扩展名，创建资产变更请求。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-static createAssetRequest(context: Context, photoType: PhotoType, extension: string, options?: CreateOptions): MediaAssetChangeRequest--><!--Device-MediaAssetChangeRequest-static createAssetRequest(context: Context, photoType: PhotoType, extension: string, options?: CreateOptions): MediaAssetChangeRequest-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| photoType | PhotoType | 是 | 待创建的文件类型，IMAGE或者VIDEO类型。 |
| extension | string | 是 | 文件扩展名，例如：'jpg'。 |
| options | [CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | 否 | 创建选项，例如：{title: 'testPhoto'}。 <br>文件名中不允许出现非法英文字符，包括：. .. \ / : ? " ' ` &lt; &gt; \| { } [ ] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | MediaAssetChangeRequest** created. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

## createAssetRequest

```TypeScript
static createAssetRequest(context: Context, photoType: PhotoType, extension: string, options?: CreateOptions): MediaAssetChangeRequest | null
```

指定文件类型和扩展名，创建资产变更请求。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-static createAssetRequest(context: Context, photoType: PhotoType, extension: string, options?: CreateOptions): MediaAssetChangeRequest | null--><!--Device-MediaAssetChangeRequest-static createAssetRequest(context: Context, photoType: PhotoType, extension: string, options?: CreateOptions): MediaAssetChangeRequest | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | Context of the ability instance. |
| photoType | PhotoType | 是 | Type of the file to create, which can be IMAGE or VIDEO. |
| extension | string | 是 | File name extension, for example, 'jpg'. |
| options | [CreateOptions](arkts-medialibrary-photoaccesshelper-createoptions-i.md) | 否 | Options for creating the image or video asset, for example, {title: 'testPhoto'}. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | Returns a MediaAssetChangeRequest instance, if the operation fails, returns null |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## createImageAssetRequest

```TypeScript
static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest
```

创建图片资产变更请求。 指定待创建资产的数据来源，可参考 [@ohos.file.fileuri (File URI)](../../apis-core-file-kit/arkts-apis/arkts-file-fileuri.md).

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest--><!--Device-MediaAssetChangeRequest-static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| fileUri | string | 是 | fileUri - 图片资产的数据来源，在应用沙箱下的uri。示例fileUri：'file://com.example.temptest/data/storage/ el2/base/haps/entry/files/test.jpg'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | 返回创建资产的变更请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900002 | The file corresponding to the URI is not in the app sandbox. |
| 14000011 | System inner fail |

## createImageAssetRequest

```TypeScript
static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest | null
```

创建图片资产变更请求。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest | null--><!--Device-MediaAssetChangeRequest-static createImageAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | Context of the ability instance. |
| fileUri | string | 是 | Data source of the image asset, which is specified by a URI in the application sandbox directory. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | Returns a MediaAssetChangeRequest instance, if the operation fails, returns null |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| 23800101 | The file corresponding to the URI is not in the app sandbox. |

## createVideoAssetRequest

```TypeScript
static createVideoAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest
```

创建视频资产变更请求。 指定待创建资产的数据来源，可参考 [@ohos.file.fileuri (File URI)](../../apis-core-file-kit/arkts-apis/arkts-file-fileuri.md).

**起始版本：** 11

<!--Device-MediaAssetChangeRequest-static createVideoAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest--><!--Device-MediaAssetChangeRequest-static createVideoAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| fileUri | string | 是 | 视频资产的数据来源，在应用沙箱下的uri。示例fileUri：'file://com.example.temptest/data/storage/ el2/base/haps/entry/files/test.mp4'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | 返回创建资产的变更请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900002 | The file corresponding to the URI is not in the app sandbox. |
| 14000011 | System inner fail |

## createVideoAssetRequest

```TypeScript
static createVideoAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest | null
```

创建视频资产变更请求。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-static createVideoAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest | null--><!--Device-MediaAssetChangeRequest-static createVideoAssetRequest(context: Context, fileUri: string): MediaAssetChangeRequest | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | Context of the ability instance. |
| fileUri | string | 是 | Data source of the video asset, which is specified by a URI in the application sandbox directory. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md) | Returns a MediaAssetChangeRequest instance. if the operation fails, returns null. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| 23800101 | The file corresponding to the URI is not in the app sandbox. |

## deleteAssets

```TypeScript
static deleteAssets(context: Context, assets: Array<PhotoAsset>): Promise<void>
```

通过PhotoAsset对象删除媒体文件（删除的文件会进入到回收站）。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAssetChangeRequest-static deleteAssets(context: Context, assets: Array<PhotoAsset>): Promise<void>--><!--Device-MediaAssetChangeRequest-static deleteAssets(context: Context, assets: Array<PhotoAsset>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| assets | Array&lt;PhotoAsset&gt; | 是 | 待删除的媒体文件数组，数组中元素个数不超过300 个。<!--Del-->系统应用对此无限制。<!--DelEnd--> |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail |

## deleteAssets

```TypeScript
static deleteAssets(context: Context, uriList: Array<string>): Promise<void>
```

通过uri删除媒体文件（删除的文件会进入到回收站）。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAssetChangeRequest-static deleteAssets(context: Context, uriList: Array<string>): Promise<void>--><!--Device-MediaAssetChangeRequest-static deleteAssets(context: Context, uriList: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| uriList | Array&lt;string&gt; | 是 | 待删除的媒体文件uri数组，数组中元素个数不超过300 个。<!--Del-->系统应用对此无限制。<!--DelEnd--> |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000002 | The uri format is incorrect or does not exist. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail |

## deleteAssetsToTrashWithUris

```TypeScript
static deleteAssetsToTrashWithUris(context: Context, uriList: Array<string>): Promise<void>
```

Deletes media assets. This API uses a promise to return the result. The deleted assets are moved to the trash.

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAssetChangeRequest-static deleteAssetsToTrashWithUris(context: Context, uriList: Array<string>): Promise<void>--><!--Device-MediaAssetChangeRequest-static deleteAssetsToTrashWithUris(context: Context, uriList: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | Context of the ability instance. |
| uriList | Array&lt;string&gt; | 是 | URIs of the media files to delete. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Returns void |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. context is null or invalid; <br>2. The uri format is incorrect or does not exist. |

## discardCameraPhoto

```TypeScript
discardCameraPhoto(): void
```

删除相机拍摄的照片。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-discardCameraPhoto(): void--><!--Device-MediaAssetChangeRequest-discardCameraPhoto(): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000016 | Operation Not Support |
| 14000011 | Internal system error |

## getAsset

```TypeScript
getAsset(): PhotoAsset
```

获取当前资产变更请求中的资产。 > **注意：** > > 对于创建资产的变更请求，在调用接口 > > [applyChanges](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#applychanges) > > 的提交生效之前，该接口会返回null。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-getAsset(): PhotoAsset--><!--Device-MediaAssetChangeRequest-getAsset(): PhotoAsset-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PhotoAsset | 返回当前资产变更请求中的资产。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000011 | System inner fail |

## getAsset

```TypeScript
getAsset(): PhotoAsset | null
```

获取当前资产变更请求中的资产。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-getAsset(): PhotoAsset | null--><!--Device-MediaAssetChangeRequest-getAsset(): PhotoAsset | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PhotoAsset | Returns the asset. if the operation fails, returns null. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## getWriteCacheHandler

```TypeScript
getWriteCacheHandler(): Promise<int>
```

获取临时文件写句柄。使用Promise异步回调。 > **注意：** > > 对于同一个资产变更请求，不支持在成功获取临时文件写句柄后，重复调用该接口。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-MediaAssetChangeRequest-getWriteCacheHandler(): Promise<int>--><!--Device-MediaAssetChangeRequest-getWriteCacheHandler(): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回临时文件写句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 14000016 | Operation Not Support |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## saveCameraPhoto

```TypeScript
saveCameraPhoto(): void
```

保存相机拍摄的照片。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-saveCameraPhoto(): void--><!--Device-MediaAssetChangeRequest-saveCameraPhoto(): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000016 | Operation Not Support |
| 14000011 | System inner fail |

## saveCameraPhoto

```TypeScript
saveCameraPhoto(imageFileType: ImageFileType): void
```

保存相机拍摄的照片。需要指定保存的类型。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-saveCameraPhoto(imageFileType: ImageFileType): void--><!--Device-MediaAssetChangeRequest-saveCameraPhoto(imageFileType: ImageFileType): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| imageFileType | [ImageFileType](arkts-medialibrary-photoaccesshelper-imagefiletype-e.md) | 是 | 需要保存的类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 14000016 | Operation Not Support |
| 14000011 | System inner fail |

## setOrientation

```TypeScript
setOrientation(orientation: int): void
```

设置图片的显示旋转角度。本接口通过修改exif元数据实现对图片旋转角度的调整。

**起始版本：** 23

<!--Device-MediaAssetChangeRequest-setOrientation(orientation: int): void--><!--Device-MediaAssetChangeRequest-setOrientation(orientation: int): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orientation | int | 是 | 待修改的图片旋转角度，且只能为0、90、180、270。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

## setTitle

```TypeScript
setTitle(title: string): void
```

修改媒体资产的标题。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-setTitle(title: string): void--><!--Device-MediaAssetChangeRequest-setTitle(title: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| title | string | 是 | 待修改的资产标题。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | System inner fail |

## comment

```TypeScript
readonly comment: string
```

用于MediaChangeRequest类型校验。 如果类（如[MediaAssetChangeRequest](#mediaassetchangerequest)或 [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md)）对象可以访问，就说明该类是MediaChangeRequest的实现类。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetChangeRequest-readonly comment: string--><!--Device-MediaAssetChangeRequest-readonly comment: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

