# AudioRendererWriteDataCallback

```TypeScript
type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult
```

Type definition of callback function for audio renderer write data.

**起始版本：** 23

<!--Device-audio-type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult--><!--Device-audio-type AudioRendererWriteDataCallback = (data: ArrayBuffer) => AudioDataCallbackResult-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | ArrayBuffer | 是 | audio data array buffer. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioDataCallbackResult](arkts-audio-audio-audiodatacallbackresult-e.md) | result of callback. If AudioDataCallbackResult.VALID is returned, it indicates the data is valid and will be played. If AudioDataCallbackResult.INVALID is returned, it indicates the data is will not be played. |

