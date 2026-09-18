# OnHttpErrorReceiveEvent

Defines the callback information triggered when the web page receives an HTTP error during resource loading, including the request and response details. It is suitable for scenarios where monitoring and handling HTTP errors are required, improving network error diagnosis accuracy and user experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## request

```TypeScript
request: WebResourceRequest
```

The information of request.

**Type:** [WebResourceRequest](arkts-arkweb-webresourcerequest-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## response

```TypeScript
response: WebResourceResponse
```

Web resource response of event.

**Type:** [WebResourceResponse](arkts-arkweb-webresourceresponse-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
