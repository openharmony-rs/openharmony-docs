# Class (WebSchemeHandler)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=5bd67952550947311c46c7276be4f0642b76503e translatedAt=2026-08-07T04:50:46.415Z pushedAt=2026-08-07T08:11:44.831Z -->

WebSchemeHandler is an interceptor class used to intercept network requests for a specified scheme (protocol), supporting scenarios such as custom protocol handling, local resource substitution, and specific request interception. Developers implement the onRequestStart callback to decide whether to intercept a request, and intercepted requests can have custom response content returned through WebResourceHandler. The WebSchemeHandler instance is registered to a specified scheme through the [setWebSchemeHandler](./arkts-apis-webview-WebviewController.md#setwebschemehandler12) method of WebviewController, thereby intercepting and processing all requests for that scheme.

WebSchemeHandler works in conjunction with [WebSchemeHandlerRequest](./arkts-apis-webview-WebSchemeHandlerRequest.md), [WebResourceHandler](./arkts-apis-webview-WebResourceHandler.md), and [WebSchemeHandlerResponse](./arkts-apis-webview-WebSchemeHandlerResponse.md): the onRequestStart callback receives a WebSchemeHandlerRequest (information about the intercepted request) and a WebResourceHandler (the handler used to return a custom response), and returns a boolean value indicating whether to intercept. onRequestStop is triggered when the request ends (only for intercepted requests) and is used for resource cleanup.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## Module to Import

```ts
import { webview } from '@kit.ArkWeb';
```

## onRequestStart<sup>12+</sup>

onRequestStart(callback: (request: WebSchemeHandlerRequest, handler: WebResourceHandler) => boolean): void

Called when a request starts. In this callback, you can determine whether to intercept the request. If **false** is returned, the request is not intercepted and the handler is invalid. If **true** is returned, the request is intercepted.

> **NOTE**
>
> - Redirected URLs cannot be intercepted individually. To intercept a redirected URL, you must also intercept the original request URL.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                | Mandatory| Description      |
| -------- | -------------------- | ---- | ---------- |
| callback   | (request: [WebSchemeHandlerRequest](./arkts-apis-webview-WebSchemeHandlerRequest.md), handler: [WebResourceHandler](./arkts-apis-webview-WebResourceHandler.md)) => boolean | Yes | Callback invoked when interception of the corresponding scheme request starts. `request` is the request, and `handler` is used to provide custom response headers and response body to the Web component. The return value **true** indicates that the request is intercepted, and **false** indicates that the request is not intercepted and the handler becomes invalid. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
// xxx.ets
import { webview, WebNetErrorList } from '@kit.ArkWeb';
import { BusinessError } from '@kit.BasicServicesKit';
import { buffer } from '@kit.ArkTS';

@Entry
@Component
struct WebComponent {
  controller: webview.WebviewController = new webview.WebviewController();
  schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();
  htmlData: string = "<html><body bgcolor=\"white\">Source:<pre>source</pre></body></html>";

  build() {
    Column() {
      Web({ src: 'https://www.example.com', controller: this.controller })
        .onControllerAttached(() => {
          try {
            this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest, resourceHandler: webview.WebResourceHandler) => {
              console.info("[schemeHandler] onRequestStart");
              try {
                console.info("[schemeHandler] onRequestStart url:" + request.getRequestUrl());
                console.info("[schemeHandler] onRequestStart method:" + request.getRequestMethod());
                console.info("[schemeHandler] onRequestStart referrer:" + request.getReferrer());
                console.info("[schemeHandler] onRequestStart isMainFrame:" + request.isMainFrame());
                console.info("[schemeHandler] onRequestStart hasGesture:" + request.hasGesture());
                console.info("[schemeHandler] onRequestStart header size:" + request.getHeader().length);
                console.info("[schemeHandler] onRequestStart resource type:" + request.getRequestResourceType());
                console.info("[schemeHandler] onRequestStart frame url:" + request.getFrameUrl());
                let header = request.getHeader();
                for (let i = 0; i < header.length; i++) {
                  console.info("[schemeHandler] onRequestStart header:" + header[i].headerKey + " " + header[i].headerValue);
                }
                let stream = request.getHttpBodyStream();
                if (stream) {
                  console.info("[schemeHandler] onRequestStart has http body stream");
                } else {
                  console.info("[schemeHandler] onRequestStart has no http body stream");
                }
              } catch (error) {
                console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              if (request.getRequestUrl().endsWith("example.com")) {
                return false;
              }

              let response = new webview.WebSchemeHandlerResponse();
              try {
                response.setNetErrorCode(WebNetErrorList.NET_OK);
                response.setStatus(200);
                response.setStatusText("OK");
                response.setMimeType("text/html");
                response.setEncoding("utf-8");
                response.setHeaderByName("header1", "value1", false);
              } catch (error) {
                console.error(`[schemeHandler] ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }

              // Call didReceiveResponse to pass the constructed response header to the intercepted request before calling didFinish/didFail.
              let buf = buffer.from(this.htmlData)
              try {
                if (buf.length == 0) {
                  console.info("[schemeHandler] length 0");
                  resourceHandler.didReceiveResponse(response);
                  // If the value of buf.length is 0 in normal cases, call resourceHandler.didFinish(). Otherwise, call resourceHandler.didFail().
                  resourceHandler.didFail(WebNetErrorList.ERR_FAILED);
                } else {
                  console.info("[schemeHandler] length 1");
                  resourceHandler.didReceiveResponse(response);
                  resourceHandler.didReceiveResponseBody(buf.buffer);
                  resourceHandler.didFinish();
                }
              } catch (error) {
                console.error(`[schemeHandler] ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
              }
              return true;
            })

            this.schemeHandler.onRequestStop((request: webview.WebSchemeHandlerRequest) => {
              console.info("[schemeHandler] onRequestStop");
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

## onRequestStop<sup>12+</sup>

onRequestStop(callback: Callback\<WebSchemeHandlerRequest\>): void

Called when the request is complete. This callback is triggered only when the [onRequestStart](#onrequeststart12) callback intercepts the request. Specifically, this callback is invoked in the following cases:

1. WebResourceHandler calls didFail or didFinish.

2. The request is interrupted due to other reasons (such as network errors or system exceptions).

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name  | Type                | Mandatory| Description      |
| -------- | -------------------- | ---- | ---------- |
| callback | Callback\<[WebSchemeHandlerRequest](./arkts-apis-webview-WebSchemeHandlerRequest.md)\> | Yes  | Callback invoked when the request is complete.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message                             |
| -------- | ------------------------------------- |
| 401 | Invalid input parameter. |

**Example**

For the complete sample code, see [onRequestStart](#onrequeststart12).