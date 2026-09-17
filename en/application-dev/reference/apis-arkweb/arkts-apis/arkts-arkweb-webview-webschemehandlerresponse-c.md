# WebSchemeHandlerResponse

WebSchemeHandlerResponse is a class used to construct HTTP response data in custom scheme interception scenarios. Developers use this class to create a Response object, set properties such as HTTP status code, status text, MIME type, character set, custom response headers, network error code, and redirection URL, and then return the custom response to the Web component through WebResourceHandler. This class is the core data carrier for custom resource interception.

WebSchemeHandlerResponse is used together with WebResourceHandler: the developer constructs a WebSchemeHandlerResponse object and fills in the response properties, and then sends the response header to the intercepted request through the didReceiveResponse method of WebResourceHandler.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

Constructs a **Response** object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## getCustomErrorCode

```TypeScript
getCustomErrorCode(): number
```

Get the custom error code of the Web response.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Return the custom error code that was set for this response. |

## getEncoding

```TypeScript
getEncoding(): string
```

Obtains the character encoding format of the response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Character encoding format of the response content, such as 'utf-8', 'gbk', etc. |

## getHeaderByName

```TypeScript
getHeaderByName(name: string): string
```

Obtains the value of a response header field by name.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the response header field to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Value of the response header field with the specified name. |

## getMimeType

```TypeScript
getMimeType(): string
```

Obtains the MIME type of this response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | MIME type string of the response content, for example, 'text/html' or 'application/json'. |

## getNetErrorCode

```TypeScript
getNetErrorCode(): WebNetErrorList
```

Obtains the network error code of the response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) | Network error code returned for the Response. |

## getStatus

```TypeScript
getStatus(): number
```

Obtains the HTTP status code of the response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the HTTP status code of the Response. |

## getStatusText

```TypeScript
getStatusText(): string
```

Obtains the status text of this response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Status text. |

## getUrl

```TypeScript
getUrl(): string
```

Obtains the redirection URL or the URL changed due to HSTS.

Risk warning: To obtain a URL for JavaScriptProxy communication API authentication, use [getLastJavascriptProxyCallingFrameUrl&lt;sup&gt;12+&lt;/sup&gt;](arkts-arkweb-webview-webviewcontroller-c.md#getlastjavascriptproxycallingframeurl).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | URL after redirection or HSTS change. |

## setCustomErrorCode

```TypeScript
setCustomErrorCode(customErrorCode: number): void
```

Set the custom error code for the Web response.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| customErrorCode | number | Yes | The custom error code for this response, Web engine will pass the custom error code directly to the application through onErrorReceive. |

## setEncoding

```TypeScript
setEncoding(encoding: string): void
```

Sets the character encoding format for the current response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | Yes | Character encoding format. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |

## setHeaderByName

```TypeScript
setHeaderByName(name: string, value: string, overwrite: boolean): void
```

Sets the header information for this response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the header, which specifies the HTTP response header field name to set. Common values include 'Content-Type', 'Authorization', 'Cache-Control', etc. |
| value | string | Yes | Value of the header, which specifies the content of the HTTP response header field. It must match the header field corresponding to the name parameter. For example, when name is 'Content-Type', value can be 'text/html; charset=utf-8'. |
| overwrite | boolean | Yes | Whether to override the existing header. The value **true** means to override the existing header, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## setMimeType

```TypeScript
setMimeType(type: string): void
```

Sets the MIME type for the current response. For example, set it to text/html when injecting HTML content, and set it to application/json when injecting JSON data.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Media type (MIME type). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |

## setNetErrorCode

```TypeScript
setNetErrorCode(code: WebNetErrorList): void
```

Sets the network error code for this response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) | Yes | Network error code. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |

## setStatus

```TypeScript
setStatus(code: number): void
```

Sets the HTTP status code for this response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | HTTP status code. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |

## setStatusText

```TypeScript
setStatusText(text: string): void
```

Sets the status text for this response.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Status text. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |

## setUrl

```TypeScript
setUrl(url: string): void
```

Sets the redirection URL or the URL changed due to HSTS for this response. After the URL is set, a redirection to the new URL is triggered.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | URL after redirection or change due to HSTS. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types. |
