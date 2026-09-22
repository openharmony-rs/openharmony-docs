# WebResourceRequest

```TypeScript
declare class WebResourceRequest
```

WebResourceRequest is a class in the Web component that represents a network resource request, providing detailed metadata about the requested resource. This object is used in event callbacks such as `onErrorReceive`, `onHttpErrorReceive`, and request interception to help developers diagnose network errors, monitor request status, and implement resource interception control. By using this class, the app can improve error handling, enhance request controllability, and optimize user experience. For sample code, see [onErrorReceive event](arkts-arkweb-web-comp-attribute.md#onerrorreceive).

**Since:** 8

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **WebResourceRequest** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## getRequestHeader

```TypeScript
getRequestHeader(): Array<Header>
```

Obtains the information about the resource request header.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[Header](arkts-arkweb-web-comp-header-i.md)&gt; | Array containing the key-value pair information of the request headers. Each **Header** object contains the name and corresponding value of a request header, such as User-Agent and Content-Type. |

## getRequestMethod

```TypeScript
getRequestMethod(): string
```

Obtains the request method.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | HTTP request method string. Common values include GET, POST, PUT, DELETE, etc., indicating the HTTP method type used for the resource request. |

## getRequestUrl

```TypeScript
getRequestUrl(): string
```

Obtains the URL of the resource request.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the complete resource request URL string, including the protocol, domain name, path, and query parameters. |

## isMainFrame

```TypeScript
isMainFrame(): boolean
```

Checks whether the resource request is for the main frame. Used to differentiate between main frame and subframe requests.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the resource request is a main frame request.<br>The value **true** indicates that the resource request is a main frame request, and **false** indicates that the resource request is not a main frame request. |

## isRedirect

```TypeScript
isRedirect(): boolean
```

Checks whether the resource request is redirected by the server. Used to inspect the request redirect chain and identify malicious redirects.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the resource request is redirected by the server.<br>The value **true** indicates that the resource request is redirected by the server, and **false** indicates that the resource request is not redirected by the server. |

## isRequestGesture

```TypeScript
isRequestGesture(): boolean
```

Checks whether the resource request is associated with a gesture (such as a tap).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the resource request is associated with a gesture (for example, a tap).<br>The value **true** indicates that the resource request is associated with a gesture, and **false** indicates the opposite. |
