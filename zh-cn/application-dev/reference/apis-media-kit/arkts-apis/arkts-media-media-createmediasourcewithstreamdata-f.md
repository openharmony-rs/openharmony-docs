# createMediaSourceWithStreamData

## createMediaSourceWithStreamData

```TypeScript
function createMediaSourceWithStreamData(streams: Array<MediaStream>): MediaSource
```

创建流媒体多码率媒体来源实例方法，当前仅支持HTTP-FLV协议格式多码率。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-media-function createMediaSourceWithStreamData(streams: Array<MediaStream>): MediaSource--><!--Device-media-function createMediaSourceWithStreamData(streams: Array<MediaStream>): MediaSource-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streams | Array&lt;[MediaStream](arkts-media-multimedia-media-mediastream-i.md)&gt; | 是 | 可设置MediaStream数组，支持的流媒体格式：HTTP-FLV。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaSource](arkts-media-multimedia-media-mediasource-i.md) | 返回MediaSource，用于媒体资源设置。 |

## 示例

```TypeScript
let streams : Array<media.MediaStream> = [];
streams.push({url: "http://xxx/480p.flv", width: 854, height: 480, bitrate: 800000});
streams.push({url: "http://xxx/720p.flv", width: 1280, height: 720, bitrate: 2000000});
streams.push({url: "http://xxx/1080p.flv", width: 1920, height: 1080, bitrate: 2000000});
let mediaSource : media.MediaSource = media.createMediaSourceWithStreamData(streams);
```


## createMediaSourceWithStreamData

```TypeScript
function createMediaSourceWithStreamData(streams: Array<MediaStream>): MediaSource | undefined
```

Creates a multi-bitrate media source for streaming media. Currently, only the HTTP-FLV multi-bitrate media source is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-media-function createMediaSourceWithStreamData(streams: Array<MediaStream>): MediaSource | undefined--><!--Device-media-function createMediaSourceWithStreamData(streams: Array<MediaStream>): MediaSource | undefined-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| streams | Array&lt;[MediaStream](arkts-media-multimedia-media-mediastream-i.md)&gt; | 是 | Array of MediaStream objects. The supported streaming media format is HTTP-FLV. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [MediaSource](arkts-media-multimedia-media-mediasource-i.md) | MediaSource instance if the operation is successful; returns null otherwise. |

