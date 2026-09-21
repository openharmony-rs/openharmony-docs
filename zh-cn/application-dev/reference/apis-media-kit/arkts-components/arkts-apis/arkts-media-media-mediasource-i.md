# MediaSource

```TypeScript
interface MediaSource
```

媒体数据信息。来源于[createMediaSourceWithUrl](arkts-media-media-createmediasourcewithurl-f.md)。

> **说明：** 
> 
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 12开始支持。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableOfflineCache

```TypeScript
enableOfflineCache(enable: boolean): void
```

是否在视频播放期间启用离线缓存。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否在视频播放期间启用离线缓存。true表示启用，false表示不启用。 |

## getID

```TypeScript
getID(): string
```

获取媒体源的标识符。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回媒体源的标识符，失败时返回空字符串。 |

## getTrackSelectionFilter

```TypeScript
getTrackSelectionFilter(): TrackSelectionFilter | undefined
```

获取已配置的音视频特征筛选值

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) &#124; undefined | 如果存在TrackSelectionFilter对象，返回TrackSelectionFilter对象。 否则, 返回TrackSelectionFilter对象。 |

## setMediaResourceLoaderDelegate

```TypeScript
setMediaResourceLoaderDelegate(resourceLoader: MediaSourceLoader): void
```

设置MediaSourceLoader，帮助播放器请求媒体数据。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resourceLoader | [MediaSourceLoader](arkts-media-media-mediasourceloader-i.md) | 是 | 应用实现的媒体数据获取接口，方便播放器获取数据。 |

**示例**

```TypeScript
import { HashMap } from '@kit.ArkTS';
import { media } from '@kit.MediaKit';

let headers: Record<string, string> = {"User-Agent" : "User-Agent-Value"};
let mediaSource : media.MediaSource = media.createMediaSourceWithUrl("http://xxx",  headers);
let uuid: number = 1;
let requests: HashMap<number, media.MediaSourceLoadingRequest> = new HashMap();

let sourceOpenCallback: media.SourceOpenCallback = (request: media.MediaSourceLoadingRequest) => {
  console.info(`Opening resource: ${request.url}`);
  // 成功打开资源，返回唯一的句柄, 保证uuid和request对应。
  uuid += 1;
  requests.set(uuid, request);
  return uuid;
};

let sourceReadCallback: media.SourceReadCallback = (uuid: number, requestedOffset: number, requestedLength: number) => {
  console.info(`Reading resource with handle ${uuid}, offset: ${requestedOffset}, length: ${requestedLength}`);
  // 判断uuid是否合法、存储read请求，不要在read请求阻塞去推送数据和头信息。
};

let sourceCloseCallback: media.SourceCloseCallback = (uuid: number) => {
  console.info(`Closing resource with handle ${uuid}`);
  // 清除当前uuid相关资源。
  requests.remove(uuid);
};

// 应用按需实现。
let resourceLoader: media.MediaSourceLoader = {
  open: sourceOpenCallback,
  read: sourceReadCallback,
  close: sourceCloseCallback
};

mediaSource.setMediaResourceLoaderDelegate(resourceLoader);
```

## setMimeType

```TypeScript
setMimeType(mimeType: AVMimeTypes): void
```

设置媒体MIME类型，以帮助播放器处理扩展的媒体源。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mimeType | [AVMimeTypes](arkts-media-media-avmimetypes-e.md) | 是 | 媒体MIME类型。 |

## setTrackSelectionFilter

```TypeScript
setTrackSelectionFilter(filter: TrackSelectionFilter): void
```

设置MediaSource的音视频特征筛选项，用户定义MediaSource的音视频筛选项后，在播放或离线下载MediaSource数据时，优先在筛选特征内执行对应的操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [TrackSelectionFilter](arkts-media-media-trackselectionfilter-i.md) | 是 | 指定预下载流媒体的音视频特征。 |
