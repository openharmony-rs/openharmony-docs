# AudioRendererWriteDataCallback

```TypeScript
type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult | void
```

回调函数类型，用于音频渲染器的数据写入，回调函数结束后，音频服务会把data指向的数据放入队列里等待播放，因此请勿在回调外再次更改data指向的数据, 且务必保证往data填满待播放数据, 否则会导致音频服务播放杂音。

**起始版本：** 12

<!--Device-audio-type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult | void--><!--Device-audio-type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult | void-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | ArrayBuffer | 是 | 待写入缓冲区的数据。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDataCallbackResult](arkts-audio-audio-audiodatacallbackresult-e.md) \| void | 如果返回 void 或 AudioDataCallbackResult.VALID：表示数据有效，将播放音频数据；如果返回 AudioDataCallbackResult.INVALID：表示数据无效，且音频数据不播放。  |

