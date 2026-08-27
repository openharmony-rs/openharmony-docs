# MediaAssetManager

媒体资产管理类，管理媒体资源读取。

> **说明：**
> 
> - 本Class首批接口从API version 11开始支持。

**起始版本：** 11

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

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| requestId | string | 是 | 需要取消的请求id，requestImage等接口返回的有效请求id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | System inner fail |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(context: Context) {
  try {
    let requestId: string = 'xxx-xxx'; // 应用需使用requestImage等接口返回的有效requestId
    await photoAccessHelper.MediaAssetManager.cancelRequest(context, requestId);
    console.info("request cancelled successfully");
  } catch (err) {
    console.error(`cancelRequest failed with error: ${err.code}, ${err.message}`);
  }
}
```

## loadMovingPhoto

```TypeScript
static loadMovingPhoto(
      context: Context,
      imageFileUri: string,
      videoFileUri: string
    ): Promise<MovingPhoto>
```

加载应用沙箱的动态照片。使用Promise异步回调。

**起始版本：** 12

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入AbilityContext或者UIExtensionContext的实例。 |
| imageFileUri | string | 是 | 应用沙箱动态照片的图片uri。 示例：'file://com.example.temptest/data/storage/el2/base/haps/ImageFile.jpg' |
| videoFileUri | string | 是 | 应用沙箱动态照片的视频uri。 示例：'file://com.example.temptest/data/storage/el2/base/haps/VideoFile.mp4' |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md)&gt; | Promise对象，返回 [MovingPhoto]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

```TypeScript
async function example(context: Context) {
  try {
    let imageFileUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/ImageFile.jpg'; // 应用沙箱动态照片的图片uri。
    let videoFileUri: string = 'file://com.example.temptest/data/storage/el2/base/haps/VideoFile.mp4'; // 应用沙箱动态照片的视频uri。
    let movingPhoto: photoAccessHelper.MovingPhoto = await photoAccessHelper.MediaAssetManager.loadMovingPhoto(context, imageFileUri, videoFileUri);
  } catch (err) {
    console.error(`loadMovingPhoto failed with error: ${err.code}, ${err.message}`);
  }
}
```

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

**起始版本：** 13

**需要权限：** ohos.permission.READ_IMAGEVIDEO

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
| Promise & lt;string & gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

class MediaHandler implements photoAccessHelper.QuickImageDataHandler<image.Picture> {
  onDataPrepared(data: image.Picture, imageSource: image.ImageSource, map: Map<string, string>) {
    console.info('on image data prepared');
  }
}

async function example(context: Context) {
  console.info('quickRequestImage');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.HIGH_QUALITY_MODE,
  }
  const handler = new MediaHandler();
  let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      await photoAccessHelper.MediaAssetManager.quickRequestImage(context, photoAsset, requestOptions, handler);
      console.info('quickRequestImage successfully');
  });
}
```

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

**起始版本：** 11

**需要权限：** ohos.permission.READ_IMAGEVIDEO

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
| Promise & lt;string & gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | System inner fail. Possible causes:  1. The database is corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

class MediaHandler implements photoAccessHelper.MediaAssetDataHandler<image.ImageSource> {
  onDataPrepared(data: image.ImageSource) {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    console.info('on image data prepared');
  }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('requestImage');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.HIGH_QUALITY_MODE,
  }
  const handler = new MediaHandler();

  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
    console.info('fetchResult success');
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (photoAsset === undefined) {
      console.error('photoAsset is undefined');
      return;
    }
    await photoAccessHelper.MediaAssetManager.requestImage(context, photoAsset, requestOptions, handler);
    console.info('requestImage successfully');
  });
}
```

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

**起始版本：** 11

**需要权限：** ohos.permission.READ_IMAGEVIDEO

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
| Promise & lt;string & gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| 14000011 | System inner fail. Possible causes:  1. The database is corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

class MediaDataHandler implements photoAccessHelper.MediaAssetDataHandler<ArrayBuffer> {
  onDataPrepared(data: ArrayBuffer) {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    console.info('on image data prepared');
  }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('requestImageData');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.HIGH_QUALITY_MODE,
  }
  const handler = new MediaDataHandler();

  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      if (photoAsset === undefined) {
      console.error('requestImageData photoAsset is undefined');
      return;
    }
      await photoAccessHelper.MediaAssetManager.requestImageData(context, photoAsset, requestOptions, handler);
      console.info('requestImageData successfully');
  });
}
```

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

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

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
| Promise & lt;string & gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 18+ |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

class MovingPhotoHandler implements photoAccessHelper.MediaAssetDataHandler<photoAccessHelper.MovingPhoto> {
  async onDataPrepared(movingPhoto: photoAccessHelper.MovingPhoto) {
    if (movingPhoto === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    console.info("moving photo acquired successfully, uri: " + movingPhoto.getUri());
  }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo(photoAccessHelper.PhotoKeys.PHOTO_SUBTYPE, photoAccessHelper.PhotoSubtype.MOVING_PHOTO);
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  // 请确保图库内存在动态照片。
  let assetResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let asset: photoAccessHelper.PhotoAsset = await assetResult.getFirstObject();
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.FAST_MODE,
  }
  const handler = new MovingPhotoHandler();
  try {
    let requestId: string = await photoAccessHelper.MediaAssetManager.requestMovingPhoto(context, asset, requestOptions, handler);
    console.info("moving photo requested successfully, requestId: " + requestId);
  } catch (err) {
    console.error(`failed to request moving photo, error code is ${err.code}, message is ${err.message}`);
  }
}
```

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

**起始版本：** 12

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| asset | PhotoAsset | 是 | 待请求的媒体文件对象。 |
| requestOptions | [RequestOptions](arkts-medialibrary-photoaccesshelper-requestoptions-i.md) | 是 | 视频请求策略模式配置项。 |
| fileUri | string | 是 | 目标写入沙箱路径uri。 示例fileUri：'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.mp4'。 |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;boolean&gt; | 是 | 媒体资源处理器，当所请求的视频资源写入完成时会触发回调。 视频资源写入成功时返回true，写入失败则返回false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象，返回请求id，可用于 [cancelRequest]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 15+ |
| 14000011 | System inner fail. Possible causes:  1. The database is corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

class MediaDataHandler implements photoAccessHelper.MediaAssetDataHandler<boolean> {
    onDataPrepared(data: boolean) {
        console.info('on video request status prepared');
    }
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context) {
  console.info('requestVideoFile');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let requestOptions: photoAccessHelper.RequestOptions = {
    deliveryMode: photoAccessHelper.DeliveryMode.HIGH_QUALITY_MODE,
  }
  const handler = new MediaDataHandler();
  let fileUri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.mp4';
  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
      console.info('fetchResult success');
      let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
      await photoAccessHelper.MediaAssetManager.requestVideoFile(context, photoAsset, requestOptions, fileUri, handler);
      console.info('requestVideoFile successfully');
  });
}
```
