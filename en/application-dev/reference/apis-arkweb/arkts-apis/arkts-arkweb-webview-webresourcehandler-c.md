# WebResourceHandler

WebResourceHandler is a handler used to return the result of an intercepted request to the **Web** component in custom scheme interception scenarios. After **WebSchemeHandler** decides to intercept a request, the developer uses **WebResourceHandler** to provide a custom response header (**didReceiveResponse**) and response body data (**didReceiveResponseBody**) to the **Web** component, and notifies the request of completion (**didFinish**) or failure (**didFail**). **didFail** supports an overloaded method (API version 20 and later) to simplify the error handling process. This API enables the app layer to fully customize the response to network requests.

**WebResourceHandler** works with [WebSchemeHandler](arkts-arkweb-webview-webschemehandler-c.md) and [WebSchemeHandlerResponse](arkts-arkweb-webview-webschemehandlerresponse-c.md): the **onRequestStart** callback of **WebSchemeHandler** receives a **WebResourceHandler** instance, the developer constructs a **WebSchemeHandlerResponse** object, passes the response header and response body data through **didReceiveResponse** and **didReceiveResponseBody** of **WebResourceHandler**, and finally calls **didFinish** or **didFail** to end the request.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## didFail

```TypeScript
didFail(code: WebNetErrorList): void
```

Notifies the ArkWeb kernel that the intercepted request will fail and ends the network request. Before calling this API, call [didReceiveResponse](#didreceiveresponse) to pass in the response header.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) | Yes | Network error code, used to identify the cause of the request failure. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [17100021](../errorcode-webview.md#17100021-webresourcehandler-is-invalid) | The resource handler is invalid. |

## didFail

```TypeScript
didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void
```

Notifies the ArkWeb kernel that the intercepted request will fail. If **completeIfNoResponse** is set to **false**, call [didReceiveResponse](#didreceiveresponse) first to pass in the response header. If **completeIfNoResponse** is set to **true** and [didReceiveResponse](#didreceiveresponse) is not called beforehand, a response header is automatically generated with the network error code -104. For details, see [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md).

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) | Yes | Network error code that identifies the cause of the request failure. |
| completeIfNoResponse | boolean | Yes | Whether to automatically complete this network request when [didReceiveResponse](#didreceiveresponse) is not called. The value **true** means to automatically generate a response header (with network error code -104) and complete the request, and **false** means to wait for the app to call [didReceiveResponse](#didreceiveresponse). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100101](../errorcode-webview.md#17100101-incorrect-network-error-code) | The errorCode is either ARKWEB_NET_OK or outside the range of error codes in WebNetErrorList. |
| [17100021](../errorcode-webview.md#17100021-webresourcehandler-is-invalid) | The resource handler is invalid. |

## didFail

```TypeScript
didFail(code: WebNetErrorList, completeIfNoResponse: boolean, customErrorCode: number): void
```

Notify that this request should be failed.

**Since:** 26.1.0

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) | Yes | Set response error code to intercept. |
| completeIfNoResponse | boolean | Yes | If completeIfNoResponse is true, when DidFailWithError is called, if DidReceiveResponse has not been called, a response is automatically constructed and the current request is terminated. |
| customErrorCode | number | Yes | The custom error code for this response, Web engine will pass the custom error code directly to the application through onErrorReceive. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100021](../errorcode-webview.md#17100021-webresourcehandler-is-invalid) | The resource handler is invalid. |

## didFinish

```TypeScript
didFinish(): void
```

Notifies the **Web** component that the intercepted request is complete and no more data is available. Before calling this API, call [didReceiveResponse](#didreceiveresponse) to pass in the response header.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100021](../errorcode-webview.md#17100021-webresourcehandler-is-invalid) | The resource handler is invalid. |

## didReceiveResponse

```TypeScript
didReceiveResponse(response: WebSchemeHandlerResponse): void
```

Passes the constructed response header to the intercepted request. This API must be called before **didFinish** or **didFail**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| response | [WebSchemeHandlerResponse](arkts-arkweb-webview-webschemehandlerresponse-c.md) | Yes | Response to the intercepted request, which is used to pass custom response header information, including the status code and response header fields, to the Web component. The developer must construct this object first and then pass it to the intercepted request through the didReceiveResponse method. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100021](../errorcode-webview.md#17100021-webresourcehandler-is-invalid) | The resource handler is invalid. |

## didReceiveResponseBody

```TypeScript
didReceiveResponseBody(data: ArrayBuffer): void
```

Passes the constructed response body to the intercepted request. This API must be called before **didFinish** or **didFail**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | ArrayBuffer | Yes | Binary data of the ArrayBuffer type, used to pass HTTP response body content. Developers need to construct binary data in the corresponding format based on the response content type (such as text, images, JSON, etc.). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. |
| [17100021](../errorcode-webview.md#17100021-webresourcehandler-is-invalid) | The resource handler is invalid. |
