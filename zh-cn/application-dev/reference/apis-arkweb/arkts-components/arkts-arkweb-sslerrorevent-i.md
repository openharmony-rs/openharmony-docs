# SslErrorEvent

Defines the ssl error event.

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## certChainData

```TypeScript
certChainData?: Array<Uint8Array>
```

证书链数据。

**类型：** Array<Uint8Array>

**起始版本：** 20

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

## isFatalError

```TypeScript
isFatalError: boolean
```

是否是致命错误。

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

是否是主资源。

**类型：** boolean

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## originalUrl

```TypeScript
originalUrl: string
```

请求的原始url地址。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## referrer

```TypeScript
referrer: string
```

referrer url地址。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

url地址。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

