# WebSchemeHandlerRequest

The WebSchemeHandlerRequest class defines a wrapper object for resource requests intercepted through WebSchemeHandler. When a developer registers a custom protocol handler (WebSchemeHandler), the Web kernel creates a WebSchemeHandlerRequest instance and passes it to the callback method upon intercepting a request matching the protocol. This object provides the following request information query methods: getting request header information, request URL, request method, source URL, determining whether it is a main frame request, whether it is associated with a user gesture, getting the request body stream, resource type, and the frame URL that triggered the request, so as to determine whether to intercept the request and construct a corresponding response.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## getFrameUrl

```TypeScript
getFrameUrl(): string
```

Obtains the URL of the frame that triggers this request.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | URL of the frame that triggers the request. |

## getHeader

```TypeScript
getHeader(): Array<WebHeader>
```

Obtains the information about the resource request header.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[WebHeader](arkts-arkweb-webview-webheader-i.md)&gt; | Information about the resource request header. |

## getHttpBodyStream

```TypeScript
getHttpBodyStream(): WebHttpBodyStream | null
```

Obtains the **WebHttpBodyStream** instance in this resource request.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [WebHttpBodyStream](arkts-arkweb-webview-webhttpbodystream-c.md) &#124; null | **WebHttpBodyStream** instance in the resource request. If there is no **WebHttpBodyStream** instance, **null** is returned. |

## getReferrer

```TypeScript
getReferrer(): string
```

Obtains the referrer.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Obtained referrer. |

## getRequestMethod

```TypeScript
getRequestMethod(): string
```

Obtains the request method.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Request method. |

## getRequestResourceType

```TypeScript
getRequestResourceType(): WebResourceType
```

Obtains the resource type of this resource request.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [WebResourceType](arkts-arkweb-webview-webresourcetype-e.md) | Resource type of the resource request. |

## getRequestUrl

```TypeScript
getRequestUrl(): string
```

Obtains the URL of the resource request.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | URL of the resource request. |

## hasGesture

```TypeScript
hasGesture(): boolean
```

Checks whether the resource request is associated with a gesture (for example, a tap).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true if the resource request is associated with a gesture (such as a tap); false otherwise. |

## isMainFrame

```TypeScript
isMainFrame(): boolean
```

Checks whether the resource request is from the main frame.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the resource request is for the main frame. The value **true** indicates the resource request is for the main frame, and **false** indicates otherwise. |
