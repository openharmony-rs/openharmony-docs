# MediaAssetManager

媒体资产管理类，管理媒体资源读取。 > **说明：** > > - 本Class首批接口从API version 11开始支持。

**起始版本：** 23

<!--Device-photoAccessHelper-class MediaAssetManager--><!--Device-photoAccessHelper-class MediaAssetManager-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cancelRequest

```TypeScript
static cancelRequest(context: Context, requestId: string): Promise<void>
```

取消未触发回调的资产内容请求。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-MediaAssetManager-static cancelRequest(context: Context, requestId: string): Promise<void>--><!--Device-MediaAssetManager-static cancelRequest(context: Context, requestId: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| requestId | string | 是 | 需要取消的请求id，requestImage等接口返回的有效请求id。 |

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

## loadMovingPhoto

```TypeScript
static loadMovingPhoto(
      context: Context,
      imageFileUri: string,
      videoFileUri: string
    ): Promise<MovingPhoto>
```

加载应用沙箱的动态照片。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-MediaAssetManager-static loadMovingPhoto(      context: Context,      imageFileUri: string,      videoFileUri: string    ): Promise<MovingPhoto>--><!--Device-MediaAssetManager-static loadMovingPhoto(      context: Context,      imageFileUri: string,      videoFileUri: string    ): Promise<MovingPhoto>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入AbilityContext或者UIExtensionContext的实例。 |
| imageFileUri | string | 是 | 应用沙箱动态照片的图片uri。 <br>示例：'file://com.example.temptest/data/storage/el2/base/haps/ImageFile.jpg' |
| videoFileUri | string | 是 | 应用沙箱动态照片的视频uri。 <br>示例：'file://com.example.temptest/data/storage/el2/base/haps/VideoFile.mp4' |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md)&gt; | Promise对象，返回 [MovingPhoto]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000011 | Internal system error |

## quickRequestImage

```TypeScript
static quickRequestImage(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      dataHandler: QuickImageDataHandler<image.Picture>
    ): Promise<string>
```

根据不同的策略模式，快速请求图片资源。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-MediaAssetManager-static quickRequestImage(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      dataHandler: QuickImageDataHandler<image.Picture>    ): Promise<string>--><!--Device-MediaAssetManager-static quickRequestImage(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      dataHandler: QuickImageDataHandler<image.Picture>    ): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| asset | PhotoAsset | 是 | 待请求的媒体文件对象。 |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | 是 | 图片请求策略模式配置项。 |
| dataHandler | [QuickImageDataHandler](arkts-medialibrary-photoaccesshelper-quickimagedatahandler-i.md)&lt;image.Picture&gt; | 是 | 媒体资源处理器，当所请求的图片资源准备完成时会触发回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | Internal system error |

## requestImage

```TypeScript
static requestImage(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      dataHandler: MediaAssetDataHandler<image.ImageSource>
    ): Promise<string>
```

根据不同的策略模式，请求图片资源。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-MediaAssetManager-static requestImage(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      dataHandler: MediaAssetDataHandler<image.ImageSource>    ): Promise<string>--><!--Device-MediaAssetManager-static requestImage(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      dataHandler: MediaAssetDataHandler<image.ImageSource>    ): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| asset | PhotoAsset | 是 | 待请求的媒体文件对象。 |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | 是 | 图片请求策略模式配置项。 |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;image.ImageSource&gt; | 是 | 媒体资源处理器，请求完成时触发回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## requestImageData

```TypeScript
static requestImageData(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      dataHandler: MediaAssetDataHandler<ArrayBuffer>
    ): Promise<string>
```

根据不同的策略模式，请求图片资源数据。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-MediaAssetManager-static requestImageData(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      dataHandler: MediaAssetDataHandler<ArrayBuffer>    ): Promise<string>--><!--Device-MediaAssetManager-static requestImageData(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      dataHandler: MediaAssetDataHandler<ArrayBuffer>    ): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| asset | PhotoAsset | 是 | 待请求的媒体文件对象。 |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | 是 | 图片请求策略模式配置项。 |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;ArrayBuffer&gt; | 是 | 媒体资源处理器，当所请求的图片资源准备完成时会触发回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## requestMovingPhoto

```TypeScript
static requestMovingPhoto(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      dataHandler: MediaAssetDataHandler<MovingPhoto>
    ): Promise<string>
```

根据不同的策略模式，请求动态照片对象（动态照片对象可用于请求动态照片的资源数据）。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-MediaAssetManager-static requestMovingPhoto(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      dataHandler: MediaAssetDataHandler<MovingPhoto>    ): Promise<string>--><!--Device-MediaAssetManager-static requestMovingPhoto(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      dataHandler: MediaAssetDataHandler<MovingPhoto>    ): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| asset | PhotoAsset | 是 | 待请求的媒体文件对象。 |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | 是 | 图片请求策略模式配置项。 |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;[MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md)&gt; | 是 | 媒体资源处理器，当所请求的图片资源准备完成时会触发回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail |

## requestVideoFile

```TypeScript
static requestVideoFile(
      context: Context,
      asset: PhotoAsset,
      requestOptions: RequestOptions,
      fileUri: string,
      dataHandler: MediaAssetDataHandler<boolean>
    ): Promise<string>
```

根据不同的策略模式，请求视频资源数据到沙箱路径。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-MediaAssetManager-static requestVideoFile(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      fileUri: string,      dataHandler: MediaAssetDataHandler<boolean>    ): Promise<string>--><!--Device-MediaAssetManager-static requestVideoFile(      context: Context,      asset: PhotoAsset,      requestOptions: RequestOptions,      fileUri: string,      dataHandler: MediaAssetDataHandler<boolean>    ): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| asset | PhotoAsset | 是 | 待请求的媒体文件对象。 |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | 是 | 视频请求策略模式配置项。 |
| fileUri | string | 是 | 目标写入沙箱路径uri。 示例fileUri：'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.mp4'。 |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;boolean&gt; | 是 | 媒体资源处理器，当所请求的视频资源写入完成时会触发回调。 <br>视频资源写入成功时返回true，写入失败则返回false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 15+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

