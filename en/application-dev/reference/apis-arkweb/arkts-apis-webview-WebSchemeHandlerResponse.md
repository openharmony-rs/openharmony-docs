# Class (WebSchemeHandlerResponse)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:49:33.631Z pushedAt=2026-08-07T08:11:48.954Z -->

WebSchemeHandlerResponse is a class used to construct HTTP response data in custom scheme interception scenarios. Developers use this class to create a Response object, set properties such as HTTP status code, status text, MIME type, character set, custom response headers, network error code, and redirection URL, and then return the custom response to the Web component through WebResourceHandler. This class is the core data carrier for custom resource interception.

WebSchemeHandlerResponse is used together with WebResourceHandler: the developer constructs a WebSchemeHandlerResponse object and fills in the response properties, and then sends the response header to the intercepted request through the didReceiveResponse method of WebResourceHandler.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## Modules to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## constructor<sup>12+</sup>

constructor()

Constructs a **Response** object.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

```ts
// xxx.ets
import { webview, WebNetErrorList } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();

  build() {
    Column() {
      Button('response').onClick(() => {
        let response = new webview.WebSchemeHandlerResponse();
        try {
          response.setUrl("http://www.example.com")
          response.setStatus(200)
          response.setStatusText("OK")
          response.setMimeType("text/html")
          response.setEncoding("utf-8")
          response.setHeaderByName("header1", "value1", false)
          response.setNetErrorCode(WebNetErrorList.NET_OK)
          console.info("[schemeHandler] getUrl:" + response.getUrl())
          console.info("[schemeHandler] getStatus:" + response.getStatus())
          console.info("[schemeHandler] getStatusText:" + response.getStatusText())
          console.info("[schemeHandler] getMimeType:" + response.getMimeType())
          console.info("[schemeHandler] getEncoding:" + response.getEncoding())
          console.info("[schemeHandler] getHeaderByName:" + response.getHeaderByName("header1"))
          console.info("[schemeHandler] getNetErrorCode:" + response.getNetErrorCode())

        } catch (error) {
          console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
        }
      })
      Web({ src: 'https://www.example.com', controller: this.controller })
    }
  }
}

```

## setUrl<sup>12+</sup>

setUrl(url: string): void

Sets the redirection URL or the URL changed due to HSTS for this response. After the URL is set, a redirection to the new URL is triggered.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   |  Mandatory | Description                      |
| --------| ------- | ---- | ---------------------------|
| url | string | Yes | URL after redirection or change due to HSTS. |

**Example**

For details about the sample code, see [constructor](#constructor12).

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types.    |

## setNetErrorCode<sup>12+</sup>

setNetErrorCode(code: WebNetErrorList): void

Sets the network error code for this response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   |  Mandatory | Description                      |
| --------| ------- | ---- | ---------------------------|
|  code | [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist) | Yes  | Network error code.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.    |

**Example**

For details about the sample code, see [constructor](#constructor12).

## setStatus<sup>12+</sup>

setStatus(code: number): void

Sets the HTTP status code for this response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   |  Mandatory | Description                      |
| --------| ------- | ---- | ---------------------------|
| code | number | Yes | HTTP status code. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types. |

**Example**

For details about the sample code, see [constructor](#constructor12).

## setStatusText<sup>12+</sup>

setStatusText(text: string): void

Sets the status text for this response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   |  Mandatory | Description                      |
| --------| ------- | ---- | ---------------------------|
|  text | string | Yes  | Status text.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types.    |

**Example**

For details about the sample code, see [constructor](#constructor12).

## setMimeType<sup>12+</sup>

setMimeType(type: string): void

Sets the MIME type for the current response. For example, set it to text/html when injecting HTML content, and set it to application/json when injecting JSON data.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   |  Mandatory | Description                      |
| --------| ------- | ---- | ---------------------------|
| type | string | Yes | Media type (MIME type). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types.    |

**Example**

For details about the sample code, see [constructor](#constructor12).

## setEncoding<sup>12+</sup>

setEncoding(encoding: string): void

Sets the character encoding format for the current response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   |  Mandatory | Description                      |
| --------| ------- | ---- | ---------------------------|
| encoding | string | Yes | Character encoding format. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Incorrect parameter types.    |

**Example**

For details about the sample code, see [constructor](#constructor12).

## setHeaderByName<sup>12+</sup>

setHeaderByName(name: string, value: string, overwrite: boolean): void

Sets the header information for this response.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   |  Mandatory | Description                      |
| --------| ------- | ---- | ---------------------------|
| name | string | Yes | Name of the header, which specifies the HTTP response header field name to set. Common values include 'Content-Type', 'Authorization', 'Cache-Control', etc. |
| value | string | Yes | Value of the header, which specifies the content of the HTTP response header field. It must match the header field corresponding to the name parameter. For example, when name is 'Content-Type', value can be 'text/html; charset=utf-8'. |
|  overwrite | boolean | Yes  | Whether to override the existing header. The value **true** means to override the existing header, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                 |
| -------- | ----------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.    |

**Example**

For details about the sample code, see [constructor](#constructor12).

## getUrl<sup>12+</sup>

getUrl(): string

Obtains the redirection URL or the URL changed due to HSTS.

Risk warning: To obtain a URL for JavaScriptProxy communication API authentication, use [getLastJavascriptProxyCallingFrameUrl<sup>12+</sup>](./arkts-apis-webview-WebviewController.md#getlastjavascriptproxycallingframeurl12).

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | URL after redirection or HSTS change. |

**Example**

For details about the sample code, see [constructor](#constructor12).

## getNetErrorCode<sup>12+</sup>

getNetErrorCode(): WebNetErrorList

Obtains the network error code of the response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist) | Network error code returned for the Response. |

**Example**

For details about the sample code, see [constructor](#constructor12).

## getStatus<sup>12+</sup>

getStatus(): number

Obtains the HTTP status code of the response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| number | Returns the HTTP status code of the Response. |

**Example**

For details about the sample code, see [constructor](#constructor12).

## getStatusText<sup>12+</sup>

getStatusText(): string

Obtains the status text of this response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Status text.|

**Example**

For details about the sample code, see [constructor](#constructor12).

## getMimeType<sup>12+</sup>

getMimeType(): string

Obtains the MIME type of this response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | MIME type string of the response content, for example, 'text/html' or 'application/json'. |

**Example**

For details about the sample code, see [constructor](#constructor12).

## getEncoding<sup>12+</sup>

getEncoding(): string

Obtains the character encoding format of the response.

**System capability**: SystemCapability.Web.Webview.Core

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Character encoding format of the response content, such as 'utf-8', 'gbk', etc. |

**Example**

For details about the sample code, see [constructor](#constructor12).

## getHeaderByName<sup>12+</sup>

getHeaderByName(name: string): string

Obtains the value of a response header field by name.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name | Type            | Mandatory| Description                 |
| ------- | ---------------- | ---- | -------------------- |
| name     | string | Yes   | Name of the response header field to obtain.      |

**Return value**

| Type   | Description                                    |
| ------- | --------------------------------------- |
| string | Value of the response header field with the specified name. |

**Example**

For details about the sample code, see [constructor](#constructor12).