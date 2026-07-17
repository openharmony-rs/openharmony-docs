# SslErrorEvent

Defines the ssl error event.

**起始版本：** 12

<!--Device-unnamed-declare interface SslErrorEvent--><!--Device-unnamed-declare interface SslErrorEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## certChainData

```TypeScript
certChainData?: Array<Uint8Array>
```

证书链数据。

**类型：** Array<Uint8Array>

**起始版本：** 20

<!--Device-SslErrorEvent-certChainData?: Array<Uint8Array>--><!--Device-SslErrorEvent-certChainData?: Array<Uint8Array>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## error

```TypeScript
error: SslError
```

错误码。

**类型：** SslError

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorEvent-error: SslError--><!--Device-SslErrorEvent-error: SslError-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: SslErrorHandler
```

通知Web组件用户操作行为。

**类型：** SslErrorHandler

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorEvent-handler: SslErrorHandler--><!--Device-SslErrorEvent-handler: SslErrorHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isFatalError

```TypeScript
isFatalError: boolean
```

是否是致命错误。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorEvent-isFatalError: boolean--><!--Device-SslErrorEvent-isFatalError: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

是否是主资源。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorEvent-isMainFrame: boolean--><!--Device-SslErrorEvent-isMainFrame: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## originalUrl

```TypeScript
originalUrl: string
```

请求的原始url地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorEvent-originalUrl: string--><!--Device-SslErrorEvent-originalUrl: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## referrer

```TypeScript
referrer: string
```

referrer url地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorEvent-referrer: string--><!--Device-SslErrorEvent-referrer: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

url地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorEvent-url: string--><!--Device-SslErrorEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

