# Class (WebResourceResponse)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-07T04:51:44.775Z pushedAt=2026-08-07T08:12:50.587Z -->

WebResourceResponse is a class in the Web component that represents HTTP responses and allows custom web page resource responses. In events such as onHttpErrorReceive, it provides the app with information including the status code, status code description, response header, response data, encoding, and MIME type of the server response. In resource request interception scenarios, it allows the app to customize the status code, status code description, response header, response data, encoding, MIME type, and data readiness state of the response, so that the app takes over the return content of specific resources. For sample code, see [onHttpErrorReceive event](./arkts-basic-components-web-events.md#onhttperrorreceive).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 8.
>
> - The sample effect is subject to the actual device.

## constructor

constructor()

Constructor of WebResourceResponse. It is used to create an HTTP response object, commonly used for customizing response content in resource request interception scenarios.

**System capability**: SystemCapability.Web.Webview.Core

## getReasonMessage

getReasonMessage(): string

Obtains the status code description of the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description           |
| ------ | ------------- |
| string | Status code description of the resource response, for example, 'OK' and 'Not Found'. |

## getResponseCode

getResponseCode(): number

Obtains the status code of the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description         |
| ------ | ----------- |
| number | Status code of the resource response. For example, 200 indicates success and 404 indicates not found. |

## getResponseData

getResponseData(): string

Obtains the data in the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description       |
| ------ | --------- |
| string | Resource response data in HTML string format. |

## getResponseEncoding

getResponseEncoding(): string

Obtains the encoding string of the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description        |
| ------ | ---------- |
| string | Encoding of the resource response, for example, 'utf-8', 'gbk', and other character set encodings. |

## getResponseHeader

getResponseHeader() : Array\<Header\>

Obtains the resource response header.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type                        | Description      |
| -------------------------- | -------- |
| Array\<[Header](./arkts-basic-components-web-i.md#header)\> | Resource response header.|

## getResponseMimeType

getResponseMimeType(): string

Obtains the MIME type of the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type    | Description                |
| ------ | ------------------ |
| string | Media (MIME) type of the resource response, for example, 'text/html', 'application/json', etc. |

## getResponseDataEx<sup>13+</sup>

getResponseDataEx(): string | number | ArrayBuffer | Resource | undefined

Obtains resource response data, supporting multiple data types. Compared with getResponseData, this method supports returning various types such as number (file handle), ArrayBuffer (binary data), and Resource ($rawfile resource). It is recommended to use this method when flexible data type support is needed.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

|Type|Description|
|---|---|
|string \| number \| ArrayBuffer \| [Resource](../apis-arkui/arkui-ts/ts-types.md#resource) \| undefined | An HTML string when the type is string; a file descriptor when the type is number; binary data when the type is ArrayBuffer; a **$rawfile** resource when the type is resource; or **undefined** if no data is available.|

## getResponseIsReady<sup>13+</sup>

getResponseIsReady(): boolean

Obtains whether the response data is ready.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

|Type|Description|
|---|---|
|boolean|**true** indicates that the response data is ready, and **false** indicates the opposite.|

## setResponseData<sup>9+</sup>

setResponseData(data: string \| number \| Resource \| ArrayBuffer): void

Sets the data in the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type                                    | Mandatory  | Description                                    |
| ---- | ---------------------------------------- | ---- | ---------------------------------------- |
| data | string \| number \| [Resource](../apis-arkui/arkui-ts/ts-types.md#resource) \| ArrayBuffer<sup>11+</sup> | Yes   | Resource response data to set. When set to a string, the value indicates a string in HTML format. When set to a number, the value indicates a file handle, which is closed by the system **Web** component. When set to a **Resource** object, the value indicates the file resources in the **rawfile** directory of the application. When set to an **ArrayBuffer** object, the value indicates the original binary data of a resource.|

## setResponseEncoding<sup>9+</sup>

setResponseEncoding(encoding: string): void

Sets the encoding string of the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name     | Type  | Mandatory  | Description        |
| -------- | ------ | ---- | ------------ |
| encoding | string | Yes    | Encoding of the resource response to set. The encoding format must be consistent with the actual encoding of the response data. The encoding format affects how the browser or client parses and displays the response content. |

## setResponseMimeType<sup>9+</sup>

setResponseMimeType(mimeType: string): void

Sets the MIME type of the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name     | Type  | Mandatory  | Description                |
| -------- | ------ | ---- | -------------------- |
| mimeType | string | Yes | Media (MIME) type of the resource response to set. Common MIME types include text/html (HTML document), application/json (JSON data), image/png (PNG image), etc. |

## setReasonMessage<sup>9+</sup>

setReasonMessage(reason: string): void

Sets the status code description of the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type  | Mandatory  | Description           |
| ------ | ------ | ---- | --------------- |
| reason | string | Yes   | Status code description of the resource response to set. The status code description is a textual explanation of the status code, usually used in correspondence with the status code. For example, when the status code is 200, the description can be set to "OK", and when the status code is 404, the description can be set to "Not Found". This description is included in the HTTP response, making it easier for the client or developer to understand the response result. |

## setResponseHeader<sup>9+</sup>

setResponseHeader(header: Array\<Header\>): void

Sets the resource response header.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name   | Type                      | Mandatory  | Description      |
| ------ | -------------------------- | ---- | ---------- |
| header | Array\<[Header](./arkts-basic-components-web-i.md#header)\> | Yes | Resource response header to set. The response header is used to pass HTTP protocol header information, for example, setting "Cache-Control" to control the caching policy, setting "Access-Control-Allow-Origin" to implement cross-origin access, and setting "Content-Type" to specify the content type. Setting the response header affects how the browser or client processes the resource. |

## setResponseCode<sup>9+</sup>

setResponseCode(code: number): void

Sets the status code of the resource response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type  | Mandatory  | Description         |
| ---- | ------ | ---- | ------------- |
| code | number | Yes | Status code of the resource response to set. If the resource request fails or the response status is an error status, refer to [@ohos.web.netErrorList](arkts-apis-netErrorList.md) to set the corresponding error code. Common error code scenarios: 404 indicates that the resource does not exist. Check the resource path. 500 indicates an internal server error. Check the server status. 403 indicates no access permission. Apply for the corresponding access permission. 401 indicates unauthorized access. Check the authentication information. Check the network configuration, server status, or resource access permission based on the error code. Avoid setting the error code to ERR_IO_PENDING, which may cause XMLHttpRequest synchronous requests to be blocked. |

## setResponseIsReady<sup>9+</sup>

setResponseIsReady(IsReady: boolean): void

Sets whether the resource response data is ready.

> **NOTE**
>
> - In resource request interception scenarios, call setResponseData(), setResponseEncoding(), setResponseMimeType(), setResponseHeader(), setResponseCode(), setReasonMessage(), and other methods first to set the response attributes. Finally, call setResponseIsReady(true) to trigger resource return.
> - Asynchronous data scenario: Call setResponseIsReady(false) first. After the data is ready, call setResponseData() and other setting methods, and finally call setResponseIsReady(true) to trigger resource return.
> - If the calling sequence is incorrect, XMLHttpRequest synchronous requests may be blocked.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   | Mandatory | Description         |
| ------- | ------- | ---- | ------------- |
| IsReady | boolean | Yes  | Whether the resource response data is ready.<br>The value **true** indicates that the resource response data is ready, and **false** indicates the opposite.<br>If the data is provided asynchronously, this parameter must be explicitly set to **false**. If this parameter is set to an invalid value, for example, **null** or **undefined**, or is not set, the data is considered ready.|