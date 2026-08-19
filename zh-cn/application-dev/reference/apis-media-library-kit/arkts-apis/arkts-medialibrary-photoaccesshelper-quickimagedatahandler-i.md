# QuickImageDataHandler

媒体资源处理器，应用在onDataPrepared方法中可自定义媒体资源处理逻辑。 > **说明：** > > - 本Interface首批接口从API version 13开始支持。

**起始版本：** 23

<!--Device-photoAccessHelper-interface QuickImageDataHandler--><!--Device-photoAccessHelper-interface QuickImageDataHandler-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## onDataPrepared

```TypeScript
onDataPrepared(data: T, imageSource: image.ImageSource, map: Map<string, string>): void
```

当请求的图片资源准备就绪时，系统会回调媒体资源就绪通知方法。如果资源准备出错，回调的data将为undefined。 map支持返回的信息： | map键名 | 值说明 | |----------|-------| | 'quality' | 图片质量。高质量为'high'，低质量为'low'。 |

**起始版本：** 13

<!--Device-QuickImageDataHandler-onDataPrepared(data: T, imageSource: image.ImageSource, map: Map<string, string>): void--><!--Device-QuickImageDataHandler-onDataPrepared(data: T, imageSource: image.ImageSource, map: Map<string, string>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | T | 是 | 已就绪的图片资源数据。 It is of the generic type and supports the [Picture](../../apis-image-kit/arkts-apis/arkts-image-image-picture-i.md) type. |
| imageSource | image.ImageSource | 是 | 已就绪的图片资源数据。 |
| map | Map&lt;string, string&gt; | 是 | 用于获取图片资源的额外信息，如图片质量。仅支持'quality'。 |

## onDataPrepared

```TypeScript
onDataPrepared(data: T | undefined, imageSource: image.ImageSource | null, map: Map<string, string>): void
```

所需的媒体资产数据已快速准备就绪。

**起始版本：** 23

<!--Device-QuickImageDataHandler-onDataPrepared(data: T | undefined, imageSource: image.ImageSource | null, map: Map<string, string>): void--><!--Device-QuickImageDataHandler-onDataPrepared(data: T | undefined, imageSource: image.ImageSource | null, map: Map<string, string>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | T \| undefined | 是 | the returned data of picture if data of media asset is invalid, return undefined. |
| imageSource | image.ImageSource \| null | 是 | the returned data of imageSource if data of imageSource is invalid, return null. |
| map | Map&lt;string, string&gt; | 是 | additional information for the data |

