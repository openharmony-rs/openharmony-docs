# OnSslErrorEventReceiveEvent

```TypeScript
declare interface OnSslErrorEventReceiveEvent
```

Defines the callback information triggered when the web page receives an SSL error, including the error code and certificate chain. It is suitable for scenarios where handling SSL errors is required, improving security exception monitoring and handling capabilities.

**Since:** 12

<!--Device-unnamed-declare interface OnSslErrorEventReceiveEvent--><!--Device-unnamed-declare interface OnSslErrorEventReceiveEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## certChainData

```TypeScript
certChainData?: Array<Uint8Array>
```

Certificate chain data.

**Type:** Array&lt;Uint8Array&gt;

**Since:** 15

<!--Device-OnSslErrorEventReceiveEvent-certChainData?: Array<Uint8Array>--><!--Device-OnSslErrorEventReceiveEvent-certChainData?: Array<Uint8Array>-End-->

**System capability:** SystemCapability.Web.Webview.Core

## error

```TypeScript
error: SslError
```

Error code.

**Type:** [SslError](arkts-arkweb-web-comp-sslerror-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnSslErrorEventReceiveEvent-error: SslError--><!--Device-OnSslErrorEventReceiveEvent-error: SslError-End-->

**System capability:** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: SslErrorHandler
```

User operation.

**Type:** [SslErrorHandler](arkts-arkweb-web-comp-sslerrorhandler-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnSslErrorEventReceiveEvent-handler: SslErrorHandler--><!--Device-OnSslErrorEventReceiveEvent-handler: SslErrorHandler-End-->

**System capability:** SystemCapability.Web.Webview.Core
