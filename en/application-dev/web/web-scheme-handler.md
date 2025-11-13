# Intercepting Network Requests Initiated by the Web Component
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

You can intercept network requests initiated by web components using [onInterceptRequest](../reference/apis-arkweb/arkts-basic-components-web-events.md#oninterceptrequest9) or SchemeHandler. SchemeHandler provides two sets of APIs: ArkTS APIs and NDK APIs.

> **Notice**
>
> You cannot obtain post data using the onInterceptRequest API. To obtain post data, use the SchemeHandler mechanism to intercept network requests.

## Intercepting Network Requests (onInterceptRequest API)

For details about how to intercept network requests initiated by web components through the onInterceptRequest API, see [Customizing Page Request Responses](./web-resource-interception-request-mgmt.md).

## Intercepting Network Requests (SchemeHandler Mechanism)

Intercept network requests initiated by web components using the SchemeHandler mechanism.

### Setting SchemeHandler for Web Components

ArkWeb allows you to intercept HTTP(s) and custom protocol requests sent by web components or ServiceWorker using SchemeHandler.

When the web kernel sends a scheme request, the callback of the SchemeHandler set for the scheme is triggered. SchemeHandler contains two callbacks: one for the request start and the other for the request end. The app needs to notify the web kernel whether to intercept the request in the callback for the request start, and clear related resources after the request ends to avoid memory leakage.

Callback for the request start: 
NDK: [ArkWeb_OnRequestStart](../reference/apis-arkweb/capi-arkweb-scheme-handler-h.md#arkweb_onrequeststart) 
ArkTS: [onRequestStart](../reference/apis-arkweb/arkts-apis-webview-WebSchemeHandler.md#onrequeststart12) 

Callback for request end: 
NDK: [ArkWeb_OnRequestStop](../reference/apis-arkweb/capi-arkweb-scheme-handler-h.md#arkweb_onrequeststop) 
ArkTS: [onRequestStop](../reference/apis-arkweb/arkts-apis-webview-WebSchemeHandler.md#onrequeststop12) 

> **Notice**
>
> - You need to set SchemeHandler after the web component is initialized. Otherwise, the setting will fail.
> - If you want to intercept the first request sent by the web component, you can initialize the web component in advance by calling [initializeWebEngine](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#initializewebengine) and then set SchemeHandler to intercept the request. For details, see [Sample Code](#sample-code).

In C++, use the NDK API to set SchemeHandler for the web component.

  ```c++
    // Create an ArkWeb_SchemeHandler object.
    ArkWeb_SchemeHandler *schemeHandler;
    OH_ArkWeb_CreateSchemeHandler(&schemeHandler);

    // Set the ArkWeb_OnRequestStart and ArkWeb_OnRequestStop callbacks for ArkWeb_SchemeHandler.
    OH_ArkWebSchemeHandler_SetOnRequestStart(schemeHandler, OnURLRequestStart);
    OH_ArkWebSchemeHandler_SetOnRequestStop(schemeHandler, OnURLRequestStop);

    // Intercept the request whose scheme is https sent by the Web component whose webTag is scheme-handler.
    OH_ArkWeb_SetSchemeHandler("https", "scheme-handler", schemeHandler);
    OH_ArkWebServiceWorker_SetSchemeHandler("https", schemeHandler);

    // Intercept the request whose scheme is custom sent by the Web component whose webTag is scheme-handler.
    OH_ArkWeb_SetSchemeHandler("custom", "scheme-handler", schemeHandler);
    OH_ArkWebServiceWorker_SetSchemeHandler("custom", schemeHandler);
  ```

In ArkTS, set the SchemeHandler for the web component.

  ```ts
    // Initialize the WebView controller and Scheme processor.
    controller: webview.WebviewController = new webview.WebviewController();
    schemeHandler: webview.WebSchemeHandler = new webview.WebSchemeHandler();
    // Set the SchemeHandler for the current web component.
    this.controller.setWebSchemeHandler('https', this.schemeHandler);
  ```

### Rules for Setting a Custom Scheme

To intercept the request of a custom scheme, you need to register the custom scheme with the web kernel before initializing the web component. If you register the custom scheme after the initialization, the registration will fail.

The creation of a web component triggers the initialization of the web kernel. In addition, ArkWeb provides the initializeWebEngine API for web initialization.

In the NDK, you can call testNapi.registerCustomSchemes on the ETS side to register a custom protocol, and then call [initializeWebEngine](../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#initializewebengine) to initialize the web kernel. The following is an example:

  ```ts
    export default class EntryAbility extends UIAbility {
        onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
            // Register the scheme configuration.
            testNapi.registerCustomSchemes();
            // Initialize the Web Engine, which will initialize the Browser process and create a BrowserContext. 
            webview.WebviewController.initializeWebEngine();
            // Create and set ArkWeb_SchemeHandler.
            testNapi.setSchemeHandler();
        }
        ...
    };
  ```

testNapi.registerCustomSchemes C++ implementation:

  ```c++
    // Register the custom scheme with the Web component and specify that this scheme should follow the standard scheme rules, allowing cross-origin requests from this scheme.
    OH_ArkWeb_RegisterCustomSchemes("custom", ARKWEB_SCHEME_OPTION_STANDARD | ARKWEB_SCHEME_OPTION_CORS_ENABLED);
    // Register the custom-local scheme with the Web component and specify that this scheme should follow the same rules as the file scheme.
    OH_ArkWeb_RegisterCustomSchemes("custom-local", ARKWEB_SCHEME_OPTION_LOCAL);
    // Register custom-csp-bypassing with the Web component and specify that this scheme should follow the standard scheme rules, allowing it to bypass CSP checks.
    OH_ArkWeb_RegisterCustomSchemes("custom-csp-bypassing", ARKWEB_SCHEME_OPTION_CSP_BYPASSING | ARKWEB_SCHEME_OPTION_STANDARD);
    // Register custom-isolated with the Web component and specify that requests for this scheme must be initiated from web pages loaded with the same scheme. 
    OH_ArkWeb_RegisterCustomSchemes("custom-isolated", ARKWEB_SCHEME_OPTION_DISPLAY_ISOLATED);
  ```

You can register a custom protocol by using customizeSchemes. The following is an example:

 ``` ts
    // xxx.ets
    import { webview } from '@kit.ArkWeb';
    import { BusinessError } from '@kit.BasicServicesKit';

    @Entry
    @Component
    struct WebComponent {
    controller: webview.WebviewController = new webview.WebviewController();
    responseWeb: WebResourceResponse = new WebResourceResponse();
    scheme1: webview.WebCustomScheme = { schemeName: "name1", isSupportCORS: true, isSupportFetch: true };
    scheme2: webview.WebCustomScheme = { schemeName: "name2", isSupportCORS: true, isSupportFetch: true };
    scheme3: webview.WebCustomScheme = { schemeName: "name3", isSupportCORS: true, isSupportFetch: true };

    aboutToAppear(): void {
        try {
        webview.WebviewController.customizeSchemes([this.scheme1, this.scheme2, this.scheme3]);
        } catch (error) {
        console.error(`ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
        }
    }

    build() {
        Column() {
        Web({ src: 'www.example.com', controller: this.controller })
            .onInterceptRequest((event) => {
            if (event) {
                console.info('url:' + event.request.getRequestUrl());
            }
            return this.responseWeb;
            })
        }
      }
    }
  ```

### Obtaining Information About Intercepted Requests

In the callback at the beginning of a request, the app can obtain the basic request information, including the URL, method, referrer, request headers, resource type, and post data. You can obtain the upload data of PUT/POST requests. The data type can be BYTES, FILE, BLOB, or CHUNKED.

Obtain information about intercepted requests in the NDK.

  ```c++
    char* url;
    OH_ArkWebResourceRequest_GetUrl(resourceRequest_, &url);
    OH_ArkWeb_ReleaseString(url);

    char* method;
    OH_ArkWebResourceRequest_GetMethod(resourceRequest_, &method);
    OH_ArkWeb_ReleaseString(method);

    int32_t resourceType = OH_ArkWebResourceRequest_GetResourceType(resourceRequest_);

    char* frameUrl;
    OH_ArkWebResourceRequest_GetFrameUrl(resourceRequest_, &frameUrl);
    OH_ArkWeb_ReleaseString(frameUrl);

    // Obtain the uploaded data of the intercepted request.
    OH_ArkWebResourceRequest_GetHttpBodyStream(resourceRequest(), &stream_);
    // Set the read callback used to read the uploaded data.
    OH_ArkWebHttpBodyStream_SetReadCallback(stream_, ReadCallback);
    // Initialize ArkWeb_HttpBodyStream. Other OH_ArkWebHttpBodyStream* functions need to be called during initialization.
    OH_ArkWebHttpBodyStream_Init(stream_, InitCallback);
  ```

In ArkTS, obtain the information about the intercepted request.
  ```ts
  this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest, resourceHandler: webview.WebResourceHandler) => {
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
  })
  ```

### Intercepting Web Core Requests and Providing Customized Responses for Intercepted Requests

Network interception enables you to provide customized responses for intercepted requests in streaming mode in the worker thread. You can also use specific network error codes to end the current intercepted request.

Error code definition: 
NDK: [Network error code (arkweb_net_error_list.h)](../reference/apis-arkweb/capi-arkweb-net-error-list-h.md) 
ArkTS: [Network error code (@ohos.web.netErrorList.d.ts)](../reference/apis-arkweb/arkts-apis-netErrorList.md) 

> **Notice**
>
> ArkWeb does not support custom error codes. Use the error codes provided by ArkWeb to end requests.

In the NDK, provide customized responses for intercepted requests.

  ```c++
    // Create a response header for the intercepted request.
    ArkWeb_Response *response;
    OH_ArkWeb_CreateResponse(&response);

    // Set the HTTP status code to 200.
    OH_ArkWebResponse_SetStatus(response, 200);
    // Set the character set in the response header to UTF-8.
    OH_ArkWebResponse_SetCharset(response, "UTF-8");
    // Set the content-length in the response header to the size of the response body.
    OH_ArkWebResponse_SetHeaderByName(response, "content-length", "1024", false);
    // Pass the response header created for the intercepted request to the Web component.
    OH_ArkWebResourceHandler_DidReceiveResponse(resourceHandler, response);

    // This function can be called for multiple times, and data can be transferred to the Web component in multiple copies.
    OH_ArkWebResourceHandler_DidReceiveData(resourceHandler, buffer, bufLen);

    // The response body for reading ends. If you want the request to fail, you can also call OH_ArkWebResourceHandler_DidFailWithError(resourceHandler_, errorCode).
    // Pass an error code to the Web component and end the request.
    OH_ArkWebResourceHandler_DidFinish(resourceHandler);
  ```

In ArkTS, provide custom response information for intercepted requests.

   ```ts
   this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest, resourceHandler: webview.WebResourceHandler) => {
    let response = new webview.WebSchemeHandlerResponse();
    try {
      // Set the network error code to OK, indicating that the request is successful.
      response.setNetErrorCode(WebNetErrorList.NET_OK);

      // Set the HTTP status code to 200, indicating that the request is successfully processed.
      response.setStatus(200);

      // Set the status text to OK to describe the status code.
      response.setStatusText("OK");

      // Set the MIME type to text/html, indicating that the returned data is an HTML document.
      response.setMimeType("text/html");

      // Set the encoding mode to utf-8, indicating that the content is encoded using UTF-8.
      response.setEncoding("utf-8");

      // Set the value of the custom response header header1 to value1. false indicates that the existing header with the same name is not overwritten.
      response.setHeaderByName("header1", "value1", false);

      // Call didReceiveResponse to pass the constructed response header to the intercepted request.
      resourceHandler.didReceiveResponse(response);

      // Call didReceiveResponseBody to pass the constructed response body to the intercepted request.
      resourceHandler.didReceiveResponseBody(buf.buffer);

      // Call didFinish to notify the web component that the intercepted request is complete.
      resourceHandler.didFinish();
    } catch (error) {
      console.error(`[schemeHandler] ErrorCode: ${(error as BusinessError).code},  Message: ${(error as BusinessError).message}`);
    }
  })
  ```

If you want to end the current request by using [OH_ArkWebResourceHandler_DidFailWithError](../reference/apis-arkweb/capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didfailwitherror) or [didFail(code: WebNetErrorList)](../reference/apis-arkweb/arkts-apis-webview-WebResourceHandler.md#didfail12), you must return a response header to the web kernel by using [OH_ArkWebResourceHandler_DidReceiveResponse](../reference/apis-arkweb/capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didreceiveresponse) or [didReceiveResponse](../reference/apis-arkweb/arkts-apis-webview-WebResourceHandler.md#didreceiveresponse12) before calling this interface. Otherwise, the request cannot be ended.

From API version 20, you can end a network request directly by using [OH_ArkWebResourceHandler_DidFailWithErrorV2](../reference/apis-arkweb/capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didfailwitherrorv2) or [didFail(code: WebNetErrorList, completeIfNoResponse: boolean)](../reference/apis-arkweb/arkts-apis-webview-WebResourceHandler.md#didfail20), without waiting for the response header returned by [OH_ArkWebResourceHandler_DidReceiveResponse](../reference/apis-arkweb/capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didreceiveresponse) or [didReceiveResponse](../reference/apis-arkweb/arkts-apis-webview-WebResourceHandler.md#didreceiveresponse12).

NDK sample code:
  ```c++
  void OnRequestStart(){
    // Return the network error code ARKWEB_ERR_CONNECTION_FAILED to end the request.
    OH_ArkWebResourceHandler_DidFailWithErrorV2(resourceHandler_, ARKWEB_ERR_CONNECTION_FAILED, true);
  }
  ```
ArkTS sample code:
  ```ts
  this.schemeHandler.onRequestStart((request: webview.WebSchemeHandlerRequest, resourceHandler: webview.WebResourceHandler) => {
    // Directly call didFail(WebNetErrorList.ERR_CONNECTION_FAILED, true) to automatically construct a network request error ERR_CONNECTION_FAILED.
    resourceHandler.didFail(WebNetErrorList.ERR_CONNECTION_FAILED, true);
  })
  ```

## Sample Code

[Intercepting Network Requests Initiated by Web Components](https://gitee.com/harmonyos_samples/guide-snippets/tree/master/ArkWebKit/ArkWebSchemeHandler)
