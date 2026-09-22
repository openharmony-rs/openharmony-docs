# OnInterceptRequestEvent

```TypeScript
declare interface OnInterceptRequestEvent
```

Defines the callback information triggered before the **Web** component loads a URL, including the request details. It is suitable for scenarios where intercepting or modifying network requests is required, improving request control flexibility and security.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## request

```TypeScript
request: WebResourceRequest
```

Information about the URL request.

**Type:** [WebResourceRequest](arkts-arkweb-web-comp-webresourcerequest-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
