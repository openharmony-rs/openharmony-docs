# SourceReadCallback

```TypeScript
type SourceReadCallback = (uuid: number, requestedOffset: number, requestedLength: number) => void
```

由应用实现此回调函数，应用需记录读取请求，并在数据充足时通过对应的MediaSourceLoadingRequest对象的[respondData](@ohos.multimedia.media:media.MediaSourceLoadingRequest.respondData(uuid: number, offset: number, buffer: ArrayBuffer))方法推送数据。

> **注意：**  
>  
> 客户端在处理完请求后应立刻返回。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type SourceReadCallback = (uuid: long, requestedOffset: long, requestedLength: long) => void--><!--Device-unnamed-type SourceReadCallback = (uuid: long, requestedOffset: long, requestedLength: long) => void-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | number | 是 | 资源句柄的标识。  |
| requestedOffset | number | 是 | 当前媒体数据相对于资源起始位置的偏移量。  |
| requestedLength | number | 是 | 当前请求的长度。值为-1时，表示到达资源末尾，此时推送完成后需通过 [finishLoading](@ohos.multimedia.media:media.MediaSourceLoadingRequest.finishLoading)方法通知播放器推送结束。  |

