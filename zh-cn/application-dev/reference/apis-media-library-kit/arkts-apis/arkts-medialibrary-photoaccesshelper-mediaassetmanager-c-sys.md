# MediaAssetManager

```TypeScript
class MediaAssetManager
```

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

## requestCompositeAuxiliaryImageData

```TypeScript
static requestCompositeAuxiliaryImageData(
      context: Context,
      asset: PhotoAsset,
      dataHandler: MediaAssetDataHandler<ArrayBuffer>
    ): Promise<string>
```

请求复合图辅助图

AI增强会额外产生一张图片，该图片与原始图组成复合图。复合图中一张用于显示，另外一张称为辅助图。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 上下文。 |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | 是 | 待请求的资产。 |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;ArrayBuffer&gt; | 是 | 回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 返回请求id，可以使用 [cancelRequest](arkts-medialibrary-photoaccesshelper-mediaassetmanager-c.md#cancelrequest)取消请求。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes: 1. The asset is not a cloud-enhanced composite photo asset. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. The database is corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

class MediaHandler implements photoAccessHelper.MediaAssetDataHandler<ArrayBuffer> {
  onDataPrepared(data: ArrayBuffer) {
    if (data === undefined) {
      console.error('Error occurred when preparing data');
      return;
    }
    console.info('Succeeded in preparing composite auxiliary image data');
  }
}

async function example(context: Context) {
  console.info('requestCompositeAuxiliaryImageData');
  // 构造查询条件，获取媒体库中的复合图（云增强）照片资产。
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  // 创建数据处理器，用于接收复合图中的辅助图的数据。
  const handler = new MediaHandler();
  let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  phAccessHelper.getAssets(fetchOptions, async (err, fetchResult) => {
    if (err) {
      console.error(`Failed to get assets. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting assets');
    // 获取查询结果中的第一个资产。
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    try {
      // 请求复合图中的辅助图的数据，返回的requestId可用于cancelRequest接口取消该请求。
      let requestId: string = await photoAccessHelper.MediaAssetManager.requestCompositeAuxiliaryImageData(context, photoAsset, handler);
      console.info('Succeeded in requesting composite auxiliary image data, requestId: ' + requestId);
    } catch (err) {
      console.error(`failed to requestCompositeAuxiliaryImageData, error code is ${err.code}, message is ${err.message}`);
    }
  });
}
```

## requestEnhancementImage

```TypeScript
static requestEnhancementImage(
      context: Context, 
      asset: PhotoAsset, 
      dataHandler: MediaAssetDataHandler<image.ImageSource>
    ) : Promise<string>
```

请求端侧云增强图片。若端侧云增强图片尚未生成，则触发立即生成。

AI增强分类端侧AI增强和云侧AI增强，该接口仅限于端侧AI增强。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 应用的上下文。 |
| asset | [PhotoAsset](arkts-medialibrary-photoaccesshelper-photoasset-i.md) | 是 | 待请求的资产。 |
| dataHandler | [MediaAssetDataHandler](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md)&lt;[image.ImageSource](../../apis-image-kit/arkts-apis/arkts-image-image-imagesource-i.md)&gt; | 是 | 请求数据准备好会被调用的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 返回请求Id，[cancelRequest](arkts-medialibrary-photoaccesshelper-mediaassetmanager-c.md#cancelrequest)可以取消请求 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| 23800108 | The specified asset does not exist. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes: 1. The context is invalid. 2. The photoAsset does not support local AI enhancement. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: 1. The database is corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |
