# OnSslErrorEventReceiveEvent

定义网页收到SSL错误时触发。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## certChainData

```TypeScript
certChainData?: Array<Uint8Array>
```

证书链数据。

**类型：** Array<Uint8Array>

**起始版本：** 15

**系统能力：** SystemCapability.Web.Webview.Core

## error

```TypeScript
error: SslError
```

错误码。

**类型：** SslError

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: SslErrorHandler
```

通知Web组件用户操作行为。

**类型：** SslErrorHandler

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

