# createMediaSourceWithStreamData

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

<a id="createmediasourcewithstreamdata"></a>
## createMediaSourceWithStreamData

```TypeScript
function createMediaSourceWithStreamData(streams: Array<MediaStream>): MediaSource
```

创建流媒体多码率媒体来源实例方法，当前仅支持HTTP-FLV协议格式多码率。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-media-function createMediaSourceWithStreamData(streams: Array<MediaStream>): MediaSource--><!--Device-media-function createMediaSourceWithStreamData(streams: Array<MediaStream>): MediaSource-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streams | Array&lt;MediaStream&gt; | 是 | 可设置MediaStream数组，支持的流媒体格式：HTTP-FLV。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaSource](arkts-media-multimedia-media-mediasource-i.md) | 返回MediaSource，用于媒体资源设置。 |

**示例：**

```TypeScript
let streams : Array<media.MediaStream> = [];
streams.push({url: "http://xxx/480p.flv", width: 854, height: 480, bitrate: 800000});
streams.push({url: "http://xxx/720p.flv", width: 1280, height: 720, bitrate: 2000000});
streams.push({url: "http://xxx/1080p.flv", width: 1920, height: 1080, bitrate: 2000000});
let mediaSource : media.MediaSource = media.createMediaSourceWithStreamData(streams);

```

