# KeyRequestCallback

```TypeScript
type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void
```

许可证请求事件的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-avSession-type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void--><!--Device-avSession-type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetId | string | 是 | 媒体ID。 |
| requestData | Uint8Array | 是 | 媒体许可证请求数据。 |

