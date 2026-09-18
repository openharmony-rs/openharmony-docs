# OnErrorReceiveEvent

Defines the callback information triggered when an error occurs during web page loading, including the request and error details. It is suitable for scenarios where monitoring and handling web page loading errors are required, improving error handling timeliness and user experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## error

```TypeScript
error: WebResourceError
```

Encapsulated information about the web page resource loading error.

**Type:** [WebResourceError](arkts-arkweb-webresourceerror-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## request

```TypeScript
request: WebResourceRequest
```

Encapsulation of a web page request.

**Type:** [WebResourceRequest](arkts-arkweb-webresourcerequest-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
