# SslErrorEvent

Defines the ssl error event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SslErrorEvent--><!--Device-unnamed-export declare interface SslErrorEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## certChainData

```TypeScript
certChainData?: Array<Uint8Array>
```

Certificate chain data in DER format.

**类型：** Array&lt;Uint8Array&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SslErrorEvent-certChainData?: Array<Uint8Array>--><!--Device-SslErrorEvent-certChainData?: Array<Uint8Array>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## error

```TypeScript
error: SslError
```

Error codes.

**类型：** SslError

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SslErrorEvent-error: SslError--><!--Device-SslErrorEvent-error: SslError-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: SslErrorHandler
```

Notifies the user of the operation behavior of the web component.

**类型：** SslErrorHandler

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SslErrorEvent-handler: SslErrorHandler--><!--Device-SslErrorEvent-handler: SslErrorHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isFatalError

```TypeScript
isFatalError: boolean
```

Whether the error is fatal.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SslErrorEvent-isFatalError: boolean--><!--Device-SslErrorEvent-isFatalError: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

Whether the request is main frame.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SslErrorEvent-isMainFrame: boolean--><!--Device-SslErrorEvent-isMainFrame: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## originalUrl

```TypeScript
originalUrl: string
```

Original url.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SslErrorEvent-originalUrl: string--><!--Device-SslErrorEvent-originalUrl: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## referrer

```TypeScript
referrer: string
```

Referrer.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SslErrorEvent-referrer: string--><!--Device-SslErrorEvent-referrer: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

Request url.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-SslErrorEvent-url: string--><!--Device-SslErrorEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

