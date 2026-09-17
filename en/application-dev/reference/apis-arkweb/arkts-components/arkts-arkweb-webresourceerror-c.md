# WebResourceError

WebResourceError is a class that provides error information when resource loading fails in the **Web** component. The error object is provided to the app through the `onErrorReceive` and `onHttpErrorReceive` event callbacks, encapsulating error details for debugging and error handling. It is typically used together with WebResourceRequest to determine which resource failed to load. For sample code, see [onErrorReceive event](arkts-arkweb-web-comp-attribute.md#onerrorreceive).

**Since:** 8

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor of WebResourceError. Creates a WebResourceError object to encapsulate error information when resource loading fails in the **Web** component.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## getCustomErrorCode

```TypeScript
getCustomErrorCode(): number
```

Gets the custom error code of the Web resource.

**Since:** 26.1.0

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Return the custom error code of the Web resource. |

## getErrorCode

```TypeScript
getErrorCode(): number
```

Obtains the error code of the resource loading. It is used to determine the specific cause of the resource loading failure (such as network errors, server errors, or permission issues), so that developers can take appropriate handling strategies based on the error type (such as retrying, prompting the user, or degrading the display).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Error code for loading the resource. For details about the error codes, see [WebNetErrorList](../arkts-apis/arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) or HTTP status codes. |

## getErrorInfo

```TypeScript
getErrorInfo(): string
```

Obtains the error information of the resource loading. It is used to describe the specific cause of the resource loading failure in detail. Developers can output the error information to logs for debugging and analysis, or display a user-friendly error message to users.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Error information about resource loading. |
