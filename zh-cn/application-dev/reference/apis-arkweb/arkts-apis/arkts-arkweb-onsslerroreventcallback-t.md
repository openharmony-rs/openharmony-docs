# OnSslErrorEventCallback

```TypeScript
type OnSslErrorEventCallback = (sslErrorEvent: SslErrorEvent) => void
```

SSL错误事件的回调函数。

**起始版本：** 12

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sslErrorEvent | SslErrorEvent | 是 | callback information of onSslErrorEvent. |

