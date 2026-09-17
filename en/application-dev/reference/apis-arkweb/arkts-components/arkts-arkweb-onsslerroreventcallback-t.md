# OnSslErrorEventCallback

```TypeScript
type OnSslErrorEventCallback = (sslErrorEvent: SslErrorEvent) => void
```

Callback invoked when an SSL error occurs during resource loading. Returns detailed information about the SSL error.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sslErrorEvent | [SslErrorEvent](arkts-arkweb-sslerrorevent-i.md) | Yes | Detailed information passed when an SSL error occurs during resource loading. |
