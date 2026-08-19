# MediaAssetDataHandler

媒体资源处理器，应用在onDataPrepared方法中可自定义媒体资源处理逻辑。 > **说明：** > > - 本Interface首批接口从API version 11开始支持。

**起始版本：** 23

<!--Device-photoAccessHelper-interface MediaAssetDataHandler--><!--Device-photoAccessHelper-interface MediaAssetDataHandler-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## onDataPrepared

```TypeScript
onDataPrepared(data: T, map?: Map<string, string>): void
```

媒体资源就绪通知，系统在资源准备就绪时回调此方法。若资源准备出错，回调的data为undefined。资源请求与回调一一对应。 T支持ArrayBuffer，[ImageSource](../../apis-image-kit/arkts-apis/arkts-image-image-imagesource-i.md)， [MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md)和boolean四种数据类型。其中，ArrayBuffer表示图片/视频资源数据， [ImageSource](../../apis-image-kit/arkts-apis/arkts-image-image-imagesource-i.md)表示图片源， [MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md)表示动态照片对象，boolean表示图片/视频资源是否成功写入应用沙箱，true表示成功，false表示失败。 map支持返回的信息： | map键名 | 值说明 | |----------|-------| | 'quality' | 图片质量。高质量为'high'，低质量为'low'。 |

**起始版本：** 11

<!--Device-MediaAssetDataHandler-onDataPrepared(data: T, map?: Map<string, string>): void--><!--Device-MediaAssetDataHandler-onDataPrepared(data: T, map?: Map<string, string>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | T | 是 | 已就绪的图片资源数据。泛型，支持ArrayBuffer, [ImageSource](../../apis-image-kit/arkts-apis/arkts-image-image-imagesource-i.md), [MovingPhoto](arkts-medialibrary-photoaccesshelper-movingphoto-i.md)和boolean四种数据类型。 |
| map | Map&lt;string, string&gt; | 否 | 用于获取图片资源的额外信息，如图片质量。当前仅支持'quality'。<br>**起始版本：** 12 |

## onDataPrepared

```TypeScript
onDataPrepared(data: T | undefined, map?: Map<string, string>): void
```

所需的媒体资产数据已准备就绪。

**起始版本：** 23

<!--Device-MediaAssetDataHandler-onDataPrepared(data: T | undefined, map?: Map<string, string>): void--><!--Device-MediaAssetDataHandler-onDataPrepared(data: T | undefined, map?: Map<string, string>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | T \| undefined | 是 | the returned data of media asset if data of media asset is invalid, return undefined. |
| map | Map&lt;string, string&gt; | 否 | additional information for the data |

