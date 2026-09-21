# WebResourceResponse

```TypeScript
declare class WebResourceResponse
```

WebResourceResponse is a class in the Web component that represents HTTP responses and allows custom web page resource responses. In events such as onHttpErrorReceive, it provides the app with information including the status code, status code description, response header, response data, encoding, and MIME type of the server response. In resource request interception scenarios, it allows the app to customize the status code, status code description, response header, response data, encoding, MIME type, and data readiness state of the response, so that the app takes over the return content of specific resources. For sample code, see [onHttpErrorReceive event](arkts-arkweb-web-comp-attribute.md#onhttperrorreceive).

**Since:** 8

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor of WebResourceResponse. It is used to create an HTTP response object, commonly used for customizing response content in resource request interception scenarios.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## getReasonMessage

```TypeScript
getReasonMessage(): string
```

Obtains the status code description of the resource response.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Status code description of the resource response, for example, 'OK' and 'Not Found'. |

## getResponseCode

```TypeScript
getResponseCode(): number
```

Obtains the status code of the resource response.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Status code of the resource response. For example, 200 indicates success and 404 indicates not found. |

## getResponseData

```TypeScript
getResponseData(): string
```

Obtains the data in the resource response.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Resource response data in HTML string format. |

## getResponseDataEx

```TypeScript
getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined
```

Obtains resource response data, supporting multiple data types. Compared with getResponseData, this method supports returning various types such as number (file handle), ArrayBuffer (binary data), and Resource ($rawfile resource). It is recommended to use this method when flexible data type support is needed.

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; number &#124; ArrayBuffer &#124; Resource &#124; undefined | An HTML string when the type is string; a file descriptor when the type is number; binary data when the type is ArrayBuffer; a **$rawfile** resource when the type is resource; or **undefined** if no data is available. |

## getResponseEncoding

```TypeScript
getResponseEncoding(): string
```

Obtains the encoding string of the resource response.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Encoding of the resource response, for example, 'utf-8', 'gbk', and other character set encodings. |

## getResponseHeader

```TypeScript
getResponseHeader(): Array<Header>
```

Obtains the resource response header.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[Header](arkts-arkweb-web-comp-header-i.md)&gt; | Resource response header. |

## getResponseIsReady

```TypeScript
getResponseIsReady(): boolean
```

Obtains whether the response data is ready.

**Since:** 13

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** indicates that the response data is ready, and **false** indicates the opposite. |

## getResponseMimeType

```TypeScript
getResponseMimeType(): string
```

Obtains the MIME type of the resource response.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Media (MIME) type of the resource response, for example, 'text/html', 'application/json', etc. |

## setReasonMessage

```TypeScript
setReasonMessage(reason: string): void
```

Sets the status code description of the resource response.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | string | Yes | Status code description of the resource response to set. The status code description is a textual explanation of the status code, usually used in correspondence with the status code. For example, when the status code is 200, the description can be set to "OK", and when the status code is 404, the description can be set to "Not Found". This description is included in the HTTP response, making it easier for the client or developer to understand the response result. |

## setResponseBody

```TypeScript
setResponseBody(data: string | number | Resource | ArrayBuffer): void
```

Sets the response data.

> **NOTE:** 
> 
> - This API supports obtaining HSP resources based on Resource objects, which [setResponseData](#setresponsedata) does not support.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string &#124; number &#124; Resource &#124; ArrayBuffer | Yes | The response data. string type indicates strings in HTML format. number type indicates file handle. Resource type indicates $rawfile resource or HSP resource. ArrayBuffer type indicates binary data. |

## setResponseCode

```TypeScript
setResponseCode(code: number): void
```

Sets the status code of the resource response.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| code | number | Yes | Status code of the resource response to set. If the resource request fails or the response status is an error status, refer to [@ohos.web.netErrorList](../arkts-apis/arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) to set the corresponding error code. Common error code scenarios: 404 indicates that the resource does not exist. Check the resource path. 500 indicates an internal server error. Check the server status. 403 indicates no access permission. Apply for the corresponding access permission. 401 indicates unauthorized access. Check the authentication information. Check the network configuration, server status, or resource access permission based on the error code. Avoid setting the error code to ERR_IO_PENDING, which may cause XMLHttpRequest synchronous requests to be blocked. |

## setResponseData

```TypeScript
setResponseData(data: string | number | Resource | ArrayBuffer): void
```

Sets the response data.

> **NOTE:** 
> 
> - This API does not support obtaining HSP resources based on Resource objects. To obtain HSP resources,use [setResponseBody](#setresponsebody) instead.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string &#124; number &#124; Resource &#124; ArrayBuffer | Yes | The response data. string type indicates strings in HTML format. number type indicates file handle. Resource type indicates $rawfile resource. ArrayBuffer type indicates binary data.<br>**Since:** 11 |

## setResponseEncoding

```TypeScript
setResponseEncoding(encoding: string): void
```

Sets the encoding string of the resource response.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encoding | string | Yes | Encoding of the resource response to set. The encoding format must be consistent with the actual encoding of the response data. The encoding format affects how the browser or client parses and displays the response content. |

## setResponseHeader

```TypeScript
setResponseHeader(header: Array<Header>): void
```

Sets the resource response header.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| header | Array&lt;[Header](arkts-arkweb-web-comp-header-i.md)&gt; | Yes | Resource response header to set. The response header is used to pass HTTP protocol header information, for example, setting "Cache-Control" to control the caching policy, setting "Access-Control-Allow-Origin" to implement cross-origin access, and setting "Content-Type" to specify thecontent type. Setting the response header affects how the browser or client processes the resource. |

## setResponseIsReady

```TypeScript
setResponseIsReady(IsReady: boolean): void
```

Sets whether the resource response data is ready.

> **NOTE:** 
> 
> - In resource request interception scenarios, call setResponseData(), setResponseEncoding(), setResponseMimeType(), setResponseHeader(), setResponseCode(), setReasonMessage(), and other methods first to set the response attributes. Finally, call setResponseIsReady(true) to trigger resource return.
> 
> - Asynchronous data scenario: Call setResponseIsReady(false) first. After the data is ready, call setResponseData () and other setting methods, and finally call setResponseIsReady(true) to trigger resource return.
> 
> - If the calling sequence is incorrect, XMLHttpRequest synchronous requests may be blocked.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| IsReady | boolean | Yes | Whether the resource response data is ready.<br>The value **true** indicates that the resource response data is ready, and **false** indicates the opposite. <br>If the data is provided asynchronously, this parameter must be explicitly set to **false**. If this parameter is set to an invalid value, for example, **null** or **undefined**, or is not set, the data is considered ready. |

## setResponseMimeType

```TypeScript
setResponseMimeType(mimeType: string): void
```

Sets the MIME type of the resource response.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mimeType | string | Yes | Media (MIME) type of the resource response to set. Common MIME types include text/html (HTML document), application/json (JSON data), image/png (PNG image), etc. |
