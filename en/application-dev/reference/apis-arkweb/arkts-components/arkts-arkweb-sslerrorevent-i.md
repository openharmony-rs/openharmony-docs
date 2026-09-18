# SslErrorEvent

Callback details triggered when an SSL error occurs during resource loading by the user, including the URL, error type, and certificate chain. It is suitable for scenarios where detailed analysis of SSL errors is required, improving security issue diagnosis and troubleshooting efficiency.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## certChainData

```TypeScript
certChainData?: Array<Uint8Array>
```

Certificate chain data.

**Type:** Array&lt;Uint8Array&gt;

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## error

```TypeScript
error: SslError
```

Error code.

**Type:** [SslError](arkts-arkweb-sslerror-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: SslErrorHandler
```

User operation.

**Type:** [SslErrorHandler](arkts-arkweb-sslerrorhandler-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## isFatalError

```TypeScript
isFatalError: boolean
```

Whether the error is a fatal error. A fatal error prevents the page from loading and rendering properly (for example, certificate verification failure or protocol error), while a non-fatal error affects only the loading of some resources (for example, image loading failure).

The value **true** indicates a fatal error, and **false** indicates a non-fatal error.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

Whether the resource is a main resource.

The value **true** indicates a main resource, and **false** indicates a non-main resource.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## originalUrl

```TypeScript
originalUrl: string
```

Original URL of the request.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## referrer

```TypeScript
referrer: string
```

Referrer URL.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
