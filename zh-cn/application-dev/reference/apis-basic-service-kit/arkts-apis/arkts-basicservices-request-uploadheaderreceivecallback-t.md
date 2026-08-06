# UploadHeaderReceiveCallback

```TypeScript
export type UploadHeaderReceiveCallback = (header: object) => void
```

The callback function for the HTTP Response Header event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-request-export type UploadHeaderReceiveCallback = (header: object) => void--><!--Device-request-export type UploadHeaderReceiveCallback = (header: object) => void-End-->

**系统能力：** SystemCapability.MiscServices.Upload

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| header | object | 是 | HTTP Response Header returned by the developer server.  |

