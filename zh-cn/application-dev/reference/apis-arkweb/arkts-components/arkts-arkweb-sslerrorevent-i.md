# SslErrorEvent

用户加载资源时发生SSL错误时触发的回调详情，包括URL、错误类型和证书链。适用于需要详细分析SSL错误的场景，提升安全问题的诊断和排查效率。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## certChainData

```TypeScript
certChainData?: Array<Uint8Array>
```

证书链数据。

**类型：** Array&lt;Uint8Array&gt;

**起始版本：** 20

**系统能力：** SystemCapability.Web.Webview.Core

## error

```TypeScript
error: SslError
```

错误码。

**类型：** [SslError](arkts-arkweb-sslerror-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: SslErrorHandler
```

通知Web组件用户操作行为。

**类型：** [SslErrorHandler](arkts-arkweb-sslerrorhandler-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isFatalError

```TypeScript
isFatalError: boolean
```

是否是致命错误。致命错误会导致页面无法正常加载和渲染（如证书验证失败、协议错误），非致命错误只影响部分资源的加载（如图片加载失败）。true表示致命错误，false表示非致命错误。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

是否是主资源。true表示主资源，false表示非主资源。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## originalUrl

```TypeScript
originalUrl: string
```

请求的原始url地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## referrer

```TypeScript
referrer: string
```

referrer url地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

url地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core
