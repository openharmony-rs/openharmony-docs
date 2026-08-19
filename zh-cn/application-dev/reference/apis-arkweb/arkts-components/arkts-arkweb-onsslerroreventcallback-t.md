# OnSslErrorEventCallback

```TypeScript
type OnSslErrorEventCallback = (sslErrorEvent: SslErrorEvent) => void
```

用户加载资源时发生SSL错误时触发的回调，返回SSL错误详细信息。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnSslErrorEventCallback = (sslErrorEvent: SslErrorEvent) => void--><!--Device-unnamed-type OnSslErrorEventCallback = (sslErrorEvent: SslErrorEvent) => void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sslErrorEvent | [SslErrorEvent](arkts-arkweb-sslerrorevent-i.md) | 是 | 用户加载资源时发生SSL错误时传递的详细信息。 |

