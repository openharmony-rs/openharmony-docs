# OnSslErrorEventReceiveEvent

Defines the triggered callback when the Web page receives an ssl Error.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface OnSslErrorEventReceiveEvent--><!--Device-unnamed-export declare interface OnSslErrorEventReceiveEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## certChainData

```TypeScript
certChainData?: Array<Uint8Array>
```

Certificate chain data in DER format.

**类型：** Array&lt;Uint8Array&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-OnSslErrorEventReceiveEvent-certChainData?: Array<Uint8Array>--><!--Device-OnSslErrorEventReceiveEvent-certChainData?: Array<Uint8Array>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## error

```TypeScript
error: SslError
```

Error codes.

**类型：** [SslError](arkts-na-web-sslerror-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-OnSslErrorEventReceiveEvent-error: SslError--><!--Device-OnSslErrorEventReceiveEvent-error: SslError-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: SslErrorHandler
```

Notifies the user of the operation behavior of the web component.

**类型：** [SslErrorHandler](arkts-na-web-sslerrorhandler-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-OnSslErrorEventReceiveEvent-handler: SslErrorHandler--><!--Device-OnSslErrorEventReceiveEvent-handler: SslErrorHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

