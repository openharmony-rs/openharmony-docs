# OnSslErrorEventCallback

```TypeScript
export type OnSslErrorEventCallback = (sslErrorEvent: SslErrorEvent) => void
```

The callback of ssl error event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export type OnSslErrorEventCallback = (sslErrorEvent: SslErrorEvent) => void--><!--Device-unnamed-export type OnSslErrorEventCallback = (sslErrorEvent: SslErrorEvent) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sslErrorEvent | [SslErrorEvent](arkts-na-web-sslerrorevent-i.md) | 是 | callback information of onSslErrorEvent. |

