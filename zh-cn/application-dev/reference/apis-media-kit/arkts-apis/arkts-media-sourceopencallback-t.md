# SourceOpenCallback

```TypeScript
type SourceOpenCallback = (request: MediaSourceLoadingRequest) => number
```

由应用实现此回调函数，应用需处理传入的资源打开请求，并返回所打开资源对应的唯一句柄。

> **注意：**  
>  
> 客户端在处理完请求后应立刻返回。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type SourceOpenCallback = (request: MediaSourceLoadingRequest) => long--><!--Device-unnamed-type SourceOpenCallback = (request: MediaSourceLoadingRequest) => long-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| request | [MediaSourceLoadingRequest](arkts-media-multimedia-media-mediasourceloadingrequest-i.md) | 是 | 打开请求参数，包含请求资源的具体信息和数据推送方式。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前资源打开请求的句柄。大于0表示请求成功，小于或等于0表示请求失败。<br/> - request对象对应句柄唯一。  |

