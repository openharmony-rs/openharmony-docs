# Class (WebResourceHandler)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:48:06.185Z pushedAt=2026-08-07T08:11:43.257Z -->

WebResourceHandler is a handler used to return the result of an intercepted request to the **Web** component in custom scheme interception scenarios. After **WebSchemeHandler** decides to intercept a request, the developer uses **WebResourceHandler** to provide a custom response header (**didReceiveResponse**) and response body data (**didReceiveResponseBody**) to the **Web** component, and notifies the request of completion (**didFinish**) or failure (**didFail**). **didFail** supports an overloaded method (API version 20+) to simplify the error handling process. This API enables the app layer to fully customize the response to network requests.

**WebResourceHandler** works with [WebSchemeHandler](./arkts-apis-webview-WebSchemeHandler.md) and [WebSchemeHandlerResponse](./arkts-apis-webview-WebSchemeHandlerResponse.md): the **onRequestStart** callback of **WebSchemeHandler** receives a **WebResourceHandler** instance, the developer constructs a **WebSchemeHandlerResponse** object, passes the response header and response body data through **didReceiveResponse** and **didReceiveResponseBody** of **WebResourceHandler**, and finally calls **didFinish** or **didFail** to end the request.

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

## didReceiveResponse<sup>12+</sup>

didReceiveResponse(response: WebSchemeHandlerResponse): void

Passes the constructed response header to the intercepted request. This API must be called before **didFinish** or **didFail**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type   |  Mandatory | Description                                           |
| ---------------| ------- | ---- | ------------- |
| response      | [WebSchemeHandlerResponse](./arkts-apis-webview-WebSchemeHandlerResponse.md)  | Yes   | Response to the intercepted request, which is used to pass custom response header information, including the status code and response header fields, to the Web component. The developer must construct this object first and then pass it to the intercepted request through the didReceiveResponse method. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.    |
| 17100021 | The resource handler is invalid. |

**Example**

For details about the example, see [OnRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## didReceiveResponseBody<sup>12+</sup>

didReceiveResponseBody(data: ArrayBuffer): void

Passes the constructed response body to the intercepted request. This API must be called before **didFinish** or **didFail**.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type   |  Mandatory | Description                                           |
| ---------------| ------- | ---- | ------------- |
| data      | ArrayBuffer  | Yes   | Binary data of the ArrayBuffer type, used to pass HTTP response body content. Developers need to construct binary data in the corresponding format based on the response content type (such as text, images, JSON, etc.). |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
|  401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.    |
| 17100021 | The resource handler is invalid. |

**Example**

For details about the example, see [OnRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## didFinish<sup>12+</sup>

didFinish(): void

Notifies the **Web** component that the intercepted request is complete and no more data is available. Before calling this API, call [didReceiveResponse](#didreceiveresponse12) to pass in the response header.

**System capability**: SystemCapability.Web.Webview.Core

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 17100021 | The resource handler is invalid. |

**Example**

For details about the example, see [OnRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## didFail<sup>12+</sup>

didFail(code: WebNetErrorList): void

Notifies the ArkWeb kernel that the intercepted request will fail and ends the network request. Before calling this API, call [didReceiveResponse](#didreceiveresponse12) to pass in the response header.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   |  Mandatory | Description                      |
| --------| ------- | ---- | ---------------------------|
| code | [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist) | Yes | Network error code, used to identify the cause of the request failure. |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md) and [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 17100021 | The resource handler is invalid. |

**Example**

For details about the example, see [OnRequestStart](./arkts-apis-webview-WebSchemeHandler.md#onrequeststart12).

## didFail<sup>20+</sup>

didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void

Notifies the ArkWeb kernel that the intercepted request will fail. If **completeIfNoResponse** is set to **false**, call [didReceiveResponse](#didreceiveresponse12) first to pass in the response header. If **completeIfNoResponse** is set to **true** and [didReceiveResponse](#didreceiveresponse12) is not called beforehand, a response header is automatically generated with the network error code -104. For details, see [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type   |  Mandatory | Description                      |
| --------| ------- | ---- | ---------------------------|
| code | [WebNetErrorList](arkts-apis-netErrorList.md#webneterrorlist) | Yes | Network error code that identifies the cause of the request failure. |
| completeIfNoResponse | boolean | Yes | Whether to automatically complete this network request when [didReceiveResponse](#didreceiveresponse12) is not called. The value **true** means to automatically generate a response header (with network error code -104) and complete the request, and **false** means to wait for the app to call [didReceiveResponse](#didreceiveresponse12). |

**Error codes**

For details about the error codes, see [Webview Error Codes](errorcode-webview.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 17100101 | The errorCode is either ARKWEB_NET_OK or outside the range of error codes in WebNetErrorList. |
| 17100021 | The resource handler is invalid. |

**Example**

```ts
// xxx.ets
import { webview, WebNetErrorList } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();

  build() {
    Column() {
      Web({ src: 'https://www.example.com', controller: this.controller })
        .onControllerAttached(() => {
          try {
            this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest, resourceHandler: webview.WebResourceHandler) => {
              console.info('[schemeHandler] onRequestStart');
              try {
                console.info('[schemeHandler] onRequestStart url:' + request.getRequestUrl());
                console.info('[schemeHandler] onRequestStart method:' + request.getRequestMethod());
                console.info('[schemeHandler] onRequestStart referrer:' + request.getReferrer());
                console.info('[schemeHandler] onRequestStart isMainFrame:' + request.isMainFrame());
                console.info('[schemeHandler] onRequestStart hasGesture:' + request.hasGesture());
                console.info('[schemeHandler] onRequestStart header size:' + request.getHeader().length);
                console.info('[schemeHandler] onRequestStart resource type:' + request.getRequestResourceType());
                console.info('[schemeHandler] onRequestStart frame url:' + request.getFrameUrl());
                let header = request.getHeader();
                for (let i = 0; i < header.length; i++) {
                  console.info('[schemeHandler] onRequestStart header:' + header[i].headerKey + ' ' + header[i].headerValue);
                }
                let stream = request.getHttpBodyStream();
                if (stream) {
                  console.info('[schemeHandler] onRequestStart has http body stream');
                } else {
                  console.info('[schemeHandler] onRequestStart has no http body stream');
                }
              } catch (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              if (request.getRequestUrl().endsWith('example.com')) {
                return false;
              }

              try {
                // Directly calls didFail(WebNetErrorList.ERR_FAILED, true). If didReceiveResponse was not called before this, the system automatically generates a response header, and the network error code is -104 (corresponding to ERR_CONNECTION_FAILED).
                resourceHandler.didFail(WebNetErrorList.ERR_FAILED, true);
              } catch (error) {
                // When error.code is 17100101(The errorCode is either ARKWEB_NET_OK or outside the range of error codes in WebNetErrorList)
                // and the code value of didFail(code: WebNetErrorList, completeIfNoResponse: boolean) is not null, the API is still called.
                console.error(`[schemeHandler] ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }
              return true;
            })

            this.schemeHandler.onRequestStop((request: webview.WebSchemeHandlerRequest) => {
              console.info('[schemeHandler] onRequestStop');
            });

            this.controller.setWebSchemeHandler('https', this.schemeHandler);
          } catch (error) {
            console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
          }
        })
        .javaScriptAccess(true)
        .domStorageAccess(true)
    }
  }
}
```