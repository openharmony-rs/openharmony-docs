# arkweb_scheme_handler.h

## Overview

The `arkweb_scheme_handler.h` file is a complete C API header file in ArkWeb for intercepting and customizing network requests. This module defines **ArkWeb_SchemeHandler** for registering custom scheme interceptors, **ArkWeb_ResourceHandler** for sending custom responses, **ArkWeb_Response** for building HTTP responses, **ArkWeb_ResourceRequest** for inspecting request details, as well as **ArkWeb_HttpBodyStream** for reading upload data and **ArkWeb_RequestHeaderList** for accessing request headers. This API works with the **ArkWeb_NativeAPIVariantKind** system and is registered through **OH_ArkWeb_SetSchemeHandler** or **OH_ArkWebServiceWorker_SetSchemeHandler**. Developers can implement custom protocol resource loading and responses, suitable for scenarios such as local resource replacement, encrypted data transmission, and offline caching. By intercepting and customizing network requests, it helps developers address special business requirements that standard protocols cannot fulfill, enhancing app security and data control capabilities while optimizing network resource loading efficiency.

**Library**: libohweb.so

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 11

**Related module**: [Web](capi-web.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkWeb_SchemeHandler_](capi-web-arkweb-schemehandler-.md) | ArkWeb_SchemeHandler | ArkWeb_SchemeHandler is a struct used to register custom scheme (protocol) interceptors. It defines two function pointers: the onRequestStart callback for request start and the onRequestStop callback for request stop. With this struct, network requests of a specified scheme in the Web component can be intercepted, which is applicable to scenarios such as resource localization, data simulation, request filtering, and protocol extension: in onRequestStart, whether to intercept is determined and custom data is returned; in onRequestStop, resource cleanup is performed; and onRequestStart and onRequestStop are called sequentially in the order of the request lifecycle. This struct works with ArkWeb_ResourceHandler and ArkWeb_Response to implement a complete request interception and custom response process. The call sequence is: ArkWeb_SchemeHandler intercepts the request → ArkWeb_ResourceHandler processes the resource → ArkWeb_Response returns the response. |
| [ArkWeb_ResourceHandler_](capi-web-arkweb-resourcehandler-.md) | ArkWeb_ResourceHandler | The ArkWeb_ResourceHandler struct is a resource handler for processing intercepted scheme requests. After ArkWeb_SchemeHandler intercepts a request of a specified scheme, this struct can be used to return custom response data to the Web component, including the response status code, response headers, and response body. This struct is passed as a parameter in the onRequestStart callback, through which developers can implement fully custom responses to intercepted requests. |
| [ArkWeb_Response_](capi-web-arkweb-response-.md) | ArkWeb_Response | Defines an **ArkWeb_Response** for the intercepted request. |
| [ArkWeb_ResourceRequest_](capi-web-arkweb-resourcerequest-.md) | ArkWeb_ResourceRequest | ArkWeb_ResourceRequest is a struct that contains detailed information about an intercepted scheme request, including the request URL, HTTP method, request headers, and other metadata. This struct is passed as a parameter in the onRequestStart callback of ArkWeb_SchemeHandler and is applicable to scenarios such as custom protocol handling and resource interception. It helps developers implement features like cross-origin request control and local resource mapping, thereby enhancing security and performance. Developers can use it to obtain complete information about the intercepted request and decide whether to intercept it and how to construct a custom response. |
| [ArkWeb_RequestHeaderList_](capi-web-arkweb-requestheaderlist-.md) | ArkWeb_RequestHeaderList | ArkWeb_RequestHeaderList is an HTTP request header list struct used to represent and manage a collection of key-value pairs of HTTP request headers in the ArkWeb NDK. This struct contains a request header array (headers) and the array length (headerCount), where headers is a pointer array of ArkWeb_RequestHeader and headerCount indicates the number of elements in the array. This struct is used together with ArkWeb_ResourceRequest and other structs to provide the capability of reading and setting network request headers for Web components. Use cases: processing HTTP request headers in a custom protocol handler, modifying request headers in a network request interceptor, adding authentication headers in API authentication scenarios, and configuring request headers in scenarios such as cache control and content negotiation. |
| [ArkWeb_HttpBodyStream_](capi-web-arkweb-httpbodystream-.md) | ArkWeb_HttpBodyStream | Defines the uploaded data of the request. You can use the **OH_ArkWebHttpBodyStream_** API to read the uploaded data. |
| [ArkWeb_ErrorInfo_](capi-web-arkweb-errorinfo-.md) | ArkWeb_ErrorInfo | The error info for setting response error details. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkWeb_CustomSchemeOption](#arkweb_customschemeoption) | ArkWeb_CustomSchemeOption | Enumerates the custom scheme options. |
| [ArkWeb_ResourceType](#arkweb_resourcetype) | ArkWeb_ResourceType | Enumerates the resource types of the request. The resource types match the corresponding items of **ResourceType** in Chromium and should not be renumbered. |

### Macro

| Name | Description |
| -- | -- |
| ARKWEB_SCHEME_HANDLER_H | The `arkweb_scheme_handler.h` file is a complete C API header file in ArkWeb for intercepting and customizing network requests. This module defines **ArkWeb_SchemeHandler** for registering custom scheme interceptors, **ArkWeb_ResourceHandler** for sending custom responses, **ArkWeb_Response** for building HTTP responses, **ArkWeb_ResourceRequest** for inspecting request details, as well as **ArkWeb_HttpBodyStream** for reading upload data and **ArkWeb_RequestHeaderList** for accessing request headers. This API works with the **ArkWeb_NativeAPIVariantKind** system and is registered through **OH_ArkWeb_SetSchemeHandler** or **OH_ArkWebServiceWorker_SetSchemeHandler**. Developers can implement custom protocol resource loading and responses, suitable for scenarios such as local resource replacement, encrypted data transmission, and offline caching. By intercepting and customizing network requests, it helps developers address special business requirements that standard protocols cannot fulfill, enhancing app security and data control capabilities while optimizing network resource loading efficiency.<br>**Since**: 12<br>**System capability**: SystemCapability.Web.Webview.Core |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*ArkWeb_OnRequestStart)(const ArkWeb_SchemeHandler* schemeHandler, ArkWeb_ResourceRequest* resourceRequest, const ArkWeb_ResourceHandler* resourceHandler, bool* intercept)](#arkweb_onrequeststart) | ArkWeb_OnRequestStart | Called when a request starts. This callback is used on the IO thread. It intercepts and handles network requests of a specified scheme at the start of the request. Developers can use this callback to implement custom protocol handling, local resource replacement, encrypted data transmission, and other features. |
| [typedef void (\*ArkWeb_OnRequestStop)(const ArkWeb_SchemeHandler* schemeHandler, const ArkWeb_ResourceRequest* resourceRequest)](#arkweb_onrequeststop) | ArkWeb_OnRequestStop | Called when the request stops. This callback is used on the IO thread. It is used to perform resource cleanup, status updates, or logging when the request completes. You should use **OH_ArkWebResourceRequest_Destroy** to destroy the **resourceRequest** and use **OH_ArkWebResourceHandler_Destroy** to destroy the **ArkWeb_ResourceHandler** received in **ArkWeb_OnRequestStart**. |
| [typedef void (\*ArkWeb_HttpBodyStreamReadCallback)(const ArkWeb_HttpBodyStream* httpBodyStream, uint8_t* buffer, int bytesRead)](#arkweb_httpbodystreamreadcallback) | ArkWeb_HttpBodyStreamReadCallback | Called when the **OH_ArkWebHttpBodyStream_Read** read operation is complete. This callback runs on the ArkWeb worker thread. |
| [typedef void (\*ArkWeb_HttpBodyStreamAsyncReadCallback)(const ArkWeb_HttpBodyStream *httpBodyStream, uint8_t *buffer, int bytesRead)](#arkweb_httpbodystreamasyncreadcallback) | ArkWeb_HttpBodyStreamAsyncReadCallback | Called when the **OH_ArkWebHttpBodyStream_AsyncRead** read operation is complete. This callback runs on the ArkWeb worker thread. |
| [typedef void (\*ArkWeb_HttpBodyStreamInitCallback)(const ArkWeb_HttpBodyStream* httpBodyStream, ArkWeb_NetError result)](#arkweb_httpbodystreaminitcallback) | ArkWeb_HttpBodyStreamInitCallback | Called when **ArkWeb_HttpBodyStream** initialization is complete. |
| [void OH_ArkWebRequestHeaderList_Destroy(ArkWeb_RequestHeaderList* requestHeaderList)](#oh_arkwebrequestheaderlist_destroy) | - | Destroys an **ArkWeb_RequestHeaderList** object. |
| [int32_t OH_ArkWebRequestHeaderList_GetSize(const ArkWeb_RequestHeaderList* requestHeaderList)](#oh_arkwebrequestheaderlist_getsize) | - | Obtains the size of a request header list. |
| [void OH_ArkWebRequestHeaderList_GetHeader(const ArkWeb_RequestHeaderList* requestHeaderList, int32_t index, char** key, char** value)](#oh_arkwebrequestheaderlist_getheader) | - | Obtains a specified request header. |
| [int32_t OH_ArkWebResourceRequest_SetUserData(ArkWeb_ResourceRequest* resourceRequest, void* userData)](#oh_arkwebresourcerequest_setuserdata) | - | Sets user data to the **ArkWeb_ResourceRequest** object. It is used to pass context information between different request callbacks or store request-associated state, which can later be retrieved through [OH_ArkWebResourceRequest_GetUserData()](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcerequest_getuserdata()). |
| [void* OH_ArkWebResourceRequest_GetUserData(const ArkWeb_ResourceRequest* resourceRequest)](#oh_arkwebresourcerequest_getuserdata) | - | Obtains user data from **ArkWeb_ResourceRequest**. |
| [void OH_ArkWebResourceRequest_GetMethod(const ArkWeb_ResourceRequest* resourceRequest, char** method)](#oh_arkwebresourcerequest_getmethod) | - | Obtains the method of a request. |
| [void OH_ArkWebResourceRequest_GetUrl(const ArkWeb_ResourceRequest* resourceRequest, char** url)](#oh_arkwebresourcerequest_geturl) | - | Obtains the URL of a request. |
| [void OH_ArkWebResourceRequest_GetHttpBodyStream(const ArkWeb_ResourceRequest* resourceRequest, ArkWeb_HttpBodyStream** httpBodyStream)](#oh_arkwebresourcerequest_gethttpbodystream) | - | Creates an **ArkWeb_HttpBodyStream** to read the uploaded data of the request. |
| [void OH_ArkWebResourceRequest_DestroyHttpBodyStream(ArkWeb_HttpBodyStream* httpBodyStream)](#oh_arkwebresourcerequest_destroyhttpbodystream) | - | Destroys an **ArkWeb_HttpBodyStream** object. |
| [int32_t OH_ArkWebResourceRequest_GetResourceType(const ArkWeb_ResourceRequest* resourceRequest)](#oh_arkwebresourcerequest_getresourcetype) | - | Obtains the resource type of a request. |
| [void OH_ArkWebResourceRequest_GetFrameUrl(const ArkWeb_ResourceRequest* resourceRequest, char** frameUrl)](#oh_arkwebresourcerequest_getframeurl) | - | Obtains the URL of the frame that triggers this request. |
| [int32_t OH_ArkWebHttpBodyStream_SetUserData(ArkWeb_HttpBodyStream* httpBodyStream, void* userData)](#oh_arkwebhttpbodystream_setuserdata) | - | Sets user data to the **ArkWeb_HttpBodyStream** object. |
| [void* OH_ArkWebHttpBodyStream_GetUserData(const ArkWeb_HttpBodyStream* httpBodyStream)](#oh_arkwebhttpbodystream_getuserdata) | - | Obtains user data from **ArkWeb_HttpBodyStream**. |
| [int32_t OH_ArkWebHttpBodyStream_SetReadCallback(ArkWeb_HttpBodyStream* httpBodyStream, ArkWeb_HttpBodyStreamReadCallback readCallback)](#oh_arkwebhttpbodystream_setreadcallback) | - | Sets a callback for **OH_ArkWebHttpBodyStream_Read**. The result of **OH_ArkWebHttpBodyStream_Read** is notified to the caller through **readCallback**, <br>which will run in the same thread as **OH_ArkWebHttpBodyStream_Read**. |
| [int32_t OH_ArkWebHttpBodyStream_SetAsyncReadCallback(ArkWeb_HttpBodyStream* httpBodyStream, ArkWeb_HttpBodyStreamAsyncReadCallback readCallback)](#oh_arkwebhttpbodystream_setasyncreadcallback) | - | Sets a callback for **OH_ArkWebHttpBodyStream_AsyncRead**. The result of **OH_ArkWebHttpBodyStream_AsyncRead**<br>is notified to the caller through **readCallback**, which runs in the ArkWeb worker thread. |
| [int32_t OH_ArkWebHttpBodyStream_Init(ArkWeb_HttpBodyStream* httpBodyStream, ArkWeb_HttpBodyStreamInitCallback initCallback)](#oh_arkwebhttpbodystream_init) | - | Initializes **ArkWeb_HttpBodyStream**. This function establishes the internal data structures and connections of **httpBodyStream** in preparation for subsequent read operations. During initialization, it allocates necessary resources and establishes a communication mechanism with the worker thread. This function must be called before any other function; otherwise, other operations will not execute properly. This API needs to be called on the IO thread to ensure thread safety and correct initialization order. |
| [void OH_ArkWebHttpBodyStream_Read(const ArkWeb_HttpBodyStream* httpBodyStream, uint8_t* buffer, int bufLen)](#oh_arkwebhttpbodystream_read) | - | Reads the upload data of a request into the buffer. This function uses an asynchronous read mechanism, submitting the read task to the worker thread for execution and returning the result through a callback. The buffer size must be greater than or equal to **bufLen** to accommodate the data to be read. Data is read from the worker thread into the buffer, so the buffer should not be used in other threads before the callback returns, to avoid concurrency issues. After the read operation completes, the caller is notified through the previously set callback, which returns the actual number of bytes read. |
| [void OH_ArkWebHttpBodyStream_AsyncRead(const ArkWeb_HttpBodyStream* httpBodyStream, uint8_t* buffer, int bufLen)](#oh_arkwebhttpbodystream_asyncread) | - | Exports the uploaded data of a request to the buffer. The buffer size must be greater than **bufLen**. The data from the worker thread is exported to the buffer. Therefore, before the callback returns the data, the buffer should not be used in other threads to avoid concurrency problems. |
| [uint64_t OH_ArkWebHttpBodyStream_GetSize(const ArkWeb_HttpBodyStream* httpBodyStream)](#oh_arkwebhttpbodystream_getsize) | - | Obtains the size of **httpBodyStream**. When data is chunked or **httpBodyStream** is invalid, **0** is always returned. |
| [uint64_t OH_ArkWebHttpBodyStream_GetPosition(const ArkWeb_HttpBodyStream* httpBodyStream)](#oh_arkwebhttpbodystream_getposition) | - | Obtains the position of **httpBodyStream**. |
| [bool OH_ArkWebHttpBodyStream_IsChunked(const ArkWeb_HttpBodyStream* httpBodyStream)](#oh_arkwebhttpbodystream_ischunked) | - | Determines whether **httpBodyStream** is chunked. |
| [bool OH_ArkWebHttpBodyStream_IsEof(const ArkWeb_HttpBodyStream* httpBodyStream)](#oh_arkwebhttpbodystream_iseof) | - | Determines whether all data in **httpBodyStream** has been read. **true** is returned if all data in **httpBodyStream** has been read. **false** is returned before the chunked **httpBodyStream** is read for the first time. |
| [bool OH_ArkWebHttpBodyStream_IsInMemory(const ArkWeb_HttpBodyStream* httpBodyStream)](#oh_arkwebhttpbodystream_isinmemory) | - | Determines whether all the uploaded data in **httpBodyStream** is in memory and all read requests are synchronized successfully. If yes, **true** is returned. **false** is returned if the data is chunked. |
| [int32_t OH_ArkWebResourceRequest_Destroy(const ArkWeb_ResourceRequest* resourceRequest)](#oh_arkwebresourcerequest_destroy) | - | Destroys an **ArkWeb_ResourceRequest** object. |
| [void OH_ArkWebResourceRequest_GetReferrer(const ArkWeb_ResourceRequest* resourceRequest, char** referrer)](#oh_arkwebresourcerequest_getreferrer) | - | Obtains the referrer of a request. |
| [void OH_ArkWebResourceRequest_GetRequestHeaders(const ArkWeb_ResourceRequest* resourceRequest, ArkWeb_RequestHeaderList** requestHeaderList)](#oh_arkwebresourcerequest_getrequestheaders) | - | Obtains the request header list **ArkWeb_RequestHeaderList** of the request. This function allocates memory for **requestHeaderList**, and the caller must use **OH_ArkWebRequestHeaderList_Destroy** to release **requestHeaderList**. |
| [bool OH_ArkWebResourceRequest_IsRedirect(const ArkWeb_ResourceRequest* resourceRequest)](#oh_arkwebresourcerequest_isredirect) | - | Determines whether a request is redirected. |
| [bool OH_ArkWebResourceRequest_IsMainFrame(const ArkWeb_ResourceRequest* resourceRequest)](#oh_arkwebresourcerequest_ismainframe) | - | Determines whether a request is from main frame. |
| [bool OH_ArkWebResourceRequest_HasGesture(const ArkWeb_ResourceRequest* resourceRequest)](#oh_arkwebresourcerequest_hasgesture) | - | Determines whether a request is triggered by a user gesture. |
| [int32_t OH_ArkWeb_RegisterCustomSchemes(const char* scheme, int32_t option)](#oh_arkweb_registercustomschemes) | - | Registers a custom scheme with **ArkWeb**. This function should not be called for built-in HTTP, HTTPS, FILE, FTP, ABOUT, and DATA protocols. This function should be called on the main thread before kernel initialization. |
| [bool OH_ArkWebServiceWorker_SetSchemeHandler(const char* scheme, ArkWeb_SchemeHandler* schemeHandler)](#oh_arkwebserviceworker_setschemehandler) | - | Sets an **ArkWeb_SchemeHandler** for a specified scheme to intercept requests of the scheme type triggered by **ServiceWorker**. **SchemeHandler** should be set after **BrowserContext** is created. <br>You can use **WebviewController.initializeWebEngine** to initialize **BrowserContext** without creating the **Web** component. |
| [bool OH_ArkWeb_SetSchemeHandler(const char* scheme, const char* webTag, ArkWeb_SchemeHandler* schemeHandler)](#oh_arkweb_setschemehandler) | - | Sets an **ArkWeb_SchemeHandler** to intercept requests of a specified scheme type. **SchemeHandler** should be set after **BrowserContext** is created. <br>You can use **WebviewController.initializeWebEngine** to initialize **BrowserContext** without creating the **Web** component. |
| [int32_t OH_ArkWebServiceWorker_ClearSchemeHandlers()](#oh_arkwebserviceworker_clearschemehandlers) | - | Clears the **SchemeHandler** registered for **ServiceWorker**. |
| [int32_t OH_ArkWeb_ClearSchemeHandlers(const char* webTag)](#oh_arkweb_clearschemehandlers) | - | Clears the **SchemeHandler** registered for the specified **Web** component. |
| [void OH_ArkWeb_CreateSchemeHandler(ArkWeb_SchemeHandler** schemeHandler)](#oh_arkweb_createschemehandler) | - | Creates an **ArkWeb_SchemeHandler** object. |
| [void OH_ArkWeb_DestroySchemeHandler(ArkWeb_SchemeHandler* schemeHandler)](#oh_arkweb_destroyschemehandler) | - | Destroys an **ArkWeb_SchemeHandler** object. |
| [int32_t OH_ArkWebSchemeHandler_SetUserData(ArkWeb_SchemeHandler* schemeHandler, void* userData)](#oh_arkwebschemehandler_setuserdata) | - | Sets user data to the **ArkWeb_SchemeHandler** object. |
| [void* OH_ArkWebSchemeHandler_GetUserData(const ArkWeb_SchemeHandler* schemeHandler)](#oh_arkwebschemehandler_getuserdata) | - | Obtains the user data from **ArkWeb_SchemeHandler**. |
| [int32_t OH_ArkWebSchemeHandler_SetOnRequestStart(ArkWeb_SchemeHandler* schemeHandler, ArkWeb_OnRequestStart onRequestStart)](#oh_arkwebschemehandler_setonrequeststart) | - | Sets an **OnRequestStart** callback for **SchemeHandler**. |
| [int32_t OH_ArkWebSchemeHandler_SetOnRequestStop(ArkWeb_SchemeHandler* schemeHandler, ArkWeb_OnRequestStop onRequestStop)](#oh_arkwebschemehandler_setonrequeststop) | - | Sets an **OnRequestStop** callback for **SchemeHandler**. |
| [void OH_ArkWeb_CreateResponse(ArkWeb_Response** response)](#oh_arkweb_createresponse) | - | Creates an **ArkWeb_Response** object for the intercepted request. |
| [void OH_ArkWeb_DestroyResponse(ArkWeb_Response* response)](#oh_arkweb_destroyresponse) | - | Destroys an **ArkWeb_Response** object. |
| [int32_t OH_ArkWebResponse_SetUrl(ArkWeb_Response* response, const char* url)](#oh_arkwebresponse_seturl) | - | Sets the resolved URL after redirection or HSTS changes. After setting, a navigation is triggered. It is used to implement URL redirection in custom responses, such as URL normalization, domain redirection, and HTTP-to-HTTPS upgrade. |
| [void OH_ArkWebResponse_GetUrl(const ArkWeb_Response* response, char** url)](#oh_arkwebresponse_geturl) | - | Obtains the parsed URL that has been redirected or changed due to HSTS. |
| [int32_t OH_ArkWebResponse_SetError(ArkWeb_Response* response, ArkWeb_NetError errorCode)](#oh_arkwebresponse_seterror) | - | Sets an error code for the **ArkWeb_Response** object. It is used together with **DidFailWithError** to inform the client of the specific reason for the request failure through the error code, such as permission errors or resource not found. |
| [ArkWeb_NetError OH_ArkWebResponse_GetError(const ArkWeb_Response* response)](#oh_arkwebresponse_geterror) | - | Obtains the error code of **ArkWeb_Response**. |
| [int32_t OH_ArkWebResponse_SetStatus(ArkWeb_Response* response, int status)](#oh_arkwebresponse_setstatus) | - | Sets an HTTP status code for **ArkWeb_Response**. |
| [int OH_ArkWebResponse_GetStatus(const ArkWeb_Response* response)](#oh_arkwebresponse_getstatus) | - | Obtains the HTTP status code of **ArkWeb_Response**. |
| [int32_t OH_ArkWebResponse_SetStatusText(ArkWeb_Response* response, const char* statusText)](#oh_arkwebresponse_setstatustext) | - | Sets a status text for **ArkWeb_Response**. |
| [void OH_ArkWebResponse_GetStatusText(const ArkWeb_Response* response, char** statusText)](#oh_arkwebresponse_getstatustext) | - | Obtains the status text of **ArkWeb_Response**. |
| [int32_t OH_ArkWebResponse_SetMimeType(ArkWeb_Response* response, const char* mimeType)](#oh_arkwebresponse_setmimetype) | - | Sets a mime type for **ArkWeb_Response**. |
| [void OH_ArkWebResponse_GetMimeType(const ArkWeb_Response* response, char** mimeType)](#oh_arkwebresponse_getmimetype) | - | Obtains the mime type of **ArkWeb_Response**. |
| [int32_t OH_ArkWebResponse_SetCharset(ArkWeb_Response* response, const char* charset)](#oh_arkwebresponse_setcharset) | - | Sets a character set for **ArkWeb_Response**. |
| [void OH_ArkWebResponse_GetCharset(const ArkWeb_Response* response, char** charset)](#oh_arkwebresponse_getcharset) | - | Obtains the character set of **ArkWeb_Response**. |
| [int32_t OH_ArkWebResponse_SetHeaderByName(ArkWeb_Response* response, const char* name, const char* value, bool overwrite)](#oh_arkwebresponse_setheaderbyname) | - | Sets a header for **ArkWeb_Response**. |
| [void OH_ArkWebResponse_GetHeaderByName(const ArkWeb_Response* response, const char* name, char** value)](#oh_arkwebresponse_getheaderbyname) | - | Obtains the header from **ArkWeb_Response**. |
| [int32_t OH_ArkWebResourceHandler_Destroy(const ArkWeb_ResourceHandler* resourceHandler)](#oh_arkwebresourcehandler_destroy) | - | Destroys an **ArkWeb_ResourceHandler** object. |
| [int32_t OH_ArkWebResourceHandler_DidReceiveResponse(const ArkWeb_ResourceHandler* resourceHandler, const ArkWeb_Response* response)](#oh_arkwebresourcehandler_didreceiveresponse) | - | Passes the constructed response header to the intercepted request. Called when intercepting a request and preparing to return a custom response, it is used to set response header information such as the HTTP response status code, media type, and character set. |
| [int32_t OH_ArkWebResourceHandler_DidReceiveData(const ArkWeb_ResourceHandler* resourceHandler, const uint8_t* buffer, int64_t bufLen)](#oh_arkwebresourcehandler_didreceivedata) | - | Passes the constructed response body to the intercepted request. Called after setting the response header, it is used to send response data. It can be called multiple times for chunked transfer of data. After the transfer is complete, **OH_ArkWebResourceHandler_DidFinish** must be called to notify the end of the request. |
| [int32_t OH_ArkWebResourceHandler_DidFinish(const ArkWeb_ResourceHandler* resourceHandler)](#oh_arkwebresourcehandler_didfinish) | - | Notifies the ArkWeb kernel that the intercepted request is complete and no more data is available. This function sends a completion signal to the kernel, which will end the processing of the request and clean up related internal resources. After calling this function, no other processing functions can be called for this request. If an error occurs during the request, use **OH_ArkWebResourceHandler_DidFailWithError** to notify the kernel. |
| [int32_t OH_ArkWebResourceHandler_DidFailWithError(const ArkWeb_ResourceHandler* resourceHandler, ArkWeb_NetError errorCode)](#oh_arkwebresourcehandler_didfailwitherror) | - | Notifies the ArkWeb kernel that the intercepted request should fail. Called in scenarios such as permission verification failure, resource not found, or network errors, it is used to mark the request as failed and inform the client of the specific failure reason through an error code. |
| [int32_t OH_ArkWebResourceHandler_DidFailWithErrorV2(const ArkWeb_ResourceHandler* resourceHandler, ArkWeb_NetError errorCode, bool completeIfNoResponse)](#oh_arkwebresourcehandler_didfailwitherrorv2) | - | Notifies the ArkWeb kernel that the intercepted request fails. Compared with the [OH_ArkWebResourceHandler_DidFailWithError](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didfailwitherror) API, the **completeIfNoResponse** parameter is added. With this parameter set to **true**, if [OH_ArkWebResourceHandler_DidReceiveResponse](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didreceiveresponse) has not been called, a response is automatically generated to complete the network request and the network error code is **-104**. With this parameter set to **false**, the system waits for the application to call [OH_ArkWebResourceHandler_DidReceiveResponse](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didreceiveresponse) and pass the response. |
| [void OH_ArkWeb_CreateErrorInfo(ArkWeb_ErrorInfo** errorInfo)](#oh_arkweb_createerrorinfo) | - | Creates an ArkWeb_ErrorInfo object. |
| [void OH_ArkWeb_DestroyErrorInfo(ArkWeb_ErrorInfo* errorInfo)](#oh_arkweb_destroyerrorinfo) | - | Destroys the ArkWeb_ErrorInfo. |
| [int32_t OH_ArkWebErrorInfo_SetCompleteIfNoResponse(ArkWeb_ErrorInfo* errorInfo, bool completeIfNoResponse)](#oh_arkweberrorinfo_setcompleteifnoresponse) | - | Sets whether to automatically generate a response if no response has been received. |
| [bool OH_ArkWebErrorInfo_GetCompleteIfNoResponse(const ArkWeb_ErrorInfo* errorInfo)](#oh_arkweberrorinfo_getcompleteifnoresponse) | - | Gets whether to automatically generate a response if no response has been received. |
| [int32_t OH_ArkWebErrorInfo_SetCustomErrorCode(ArkWeb_ErrorInfo* errorInfo, int32_t errorCode)](#oh_arkweberrorinfo_setcustomerrorcode) | - | Sets the custom error code for ArkWeb_ErrorInfo. |
| [int32_t OH_ArkWebErrorInfo_GetCustomErrorCode(const ArkWeb_ErrorInfo* errorInfo)](#oh_arkweberrorinfo_getcustomerrorcode) | - | Gets the custom error code from the ArkWeb_ErrorInfo. |
| [int32_t OH_ArkWebErrorInfo_SetErrorCode(ArkWeb_ErrorInfo* errorInfo, ArkWeb_NetError errorCode)](#oh_arkweberrorinfo_seterrorcode) | - | Sets the error code for ArkWeb_ErrorInfo. |
| [ArkWeb_NetError OH_ArkWebErrorInfo_GetErrorCode(const ArkWeb_ErrorInfo* errorInfo)](#oh_arkweberrorinfo_geterrorcode) | - | Gets the error code from the ArkWeb_ErrorInfo. Refer to arkweb_net_error_list.h. |
| [int32_t OH_ArkWebResponse_SetErrorInfo(ArkWeb_Response* response, ArkWeb_ErrorInfo* errorInfo)](#oh_arkwebresponse_seterrorinfo) | - | Sets the error info for the ArkWeb_Response. |
| [ArkWeb_ErrorInfo* OH_ArkWebResponse_GetErrorInfo(const ArkWeb_Response* response)](#oh_arkwebresponse_geterrorinfo) | - | Gets the error info from the ArkWeb_Response. |
| [int32_t OH_ArkWebResourceHandler_DidFailWithErrorInfo(const ArkWeb_ResourceHandler* resourceHandler, const ArkWeb_ErrorInfo* errorInfo)](#oh_arkwebresourcehandler_didfailwitherrorinfo) | - | Notify the web engine that this request should fail with error info. |
| [void OH_ArkWeb_ReleaseString(char* string)](#oh_arkweb_releasestring) | - | Releases the string created by NDK APIs. |
| [void OH_ArkWeb_ReleaseByteArray(uint8_t* byteArray)](#oh_arkweb_releasebytearray) | - | Releases the byte array created by NDK APIs. |

### Variable

| Name | Description |
| -- | -- |
| void (*ArkWeb_OnRequestStart)(const ArkWeb_SchemeHandler* schemeHandler, ArkWeb_ResourceRequest* resourceRequest, const ArkWeb_ResourceHandler* resourceHandler, bool* intercept) | Called when a request starts. This callback is used on the IO thread. It intercepts and handles network requests of a specified scheme at the start of the request. Developers can use this callback to implement custom protocol handling, local resource replacement, encrypted data transmission, and other features.<br>**Since**: 12<br>**System capability**: SystemCapability.Web.Webview.Core |
| void (*ArkWeb_OnRequestStop)(const ArkWeb_SchemeHandler* schemeHandler, const ArkWeb_ResourceRequest* resourceRequest) | Called when the request stops. This callback is used on the IO thread. It is used to perform resource cleanup, status updates, or logging when the request completes. You should use **OH_ArkWebResourceRequest_Destroy** to destroy the **resourceRequest** and use **OH_ArkWebResourceHandler_Destroy** to destroy the **ArkWeb_ResourceHandler** received in **ArkWeb_OnRequestStart**.<br>**Since**: 12 |
| void (*ArkWeb_HttpBodyStreamReadCallback)(const ArkWeb_HttpBodyStream* httpBodyStream, uint8_t* buffer, int bytesRead) | Called when the **OH_ArkWebHttpBodyStream_Read** read operation is complete. This callback runs on the ArkWeb worker thread.<br>**Since**: 12<br>**System capability**: SystemCapability.Web.Webview.Core |
| void (*ArkWeb_HttpBodyStreamAsyncReadCallback)(const ArkWeb_HttpBodyStream *httpBodyStream, uint8_t *buffer, int bytesRead) | Called when the **OH_ArkWebHttpBodyStream_AsyncRead** read operation is complete. This callback runs on the ArkWeb worker thread.<br>**Since**: 20 |
| void (*ArkWeb_HttpBodyStreamInitCallback)(const ArkWeb_HttpBodyStream* httpBodyStream, ArkWeb_NetError result) | Called when **ArkWeb_HttpBodyStream** initialization is complete.<br>**Since**: 12<br>**System capability**: SystemCapability.Web.Webview.Core |

## Enum type description

### ArkWeb_CustomSchemeOption

```c
enum ArkWeb_CustomSchemeOption
```

**Description**

Enumerates the custom scheme options.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKWEB_SCHEME_OPTION_STANDARD = 1 << 0 | The scheme is processed as a standard scheme. The standard schemes need to comply with the URL normalization and parsing rules defined in Section 3.1 of RFC 1738, which can be found in the http://www.ietf.org/rfc/rfc1738.txt. |
| ARKWEB_SCHEME_OPTION_LOCAL = 1 << 1 | The scheme is processed using the same security rule as the file URL. |
| ARKWEB_SCHEME_OPTION_DISPLAY_ISOLATED = 1 << 2 | The request of the scheme can be initiated only by the page that is loaded using the same scheme. |
| ARKWEB_SCHEME_OPTION_SECURE = 1 << 3 | The scheme is processed using the same security rule as the HTTPS URL. |
| ARKWEB_SCHEME_OPTION_CORS_ENABLED = 1 << 4 | The scheme can send CORS requests. In most cases, this value should be set when **ARKWEB_SCHEME_OPTION_STANDARD**<br>is set. |
| ARKWEB_SCHEME_OPTION_CSP_BYPASSING = 1 << 5 | The scheme can bypass the Content Security Policy (CSP) check. In most cases, this value should not be set when ARKWEB_SCHEME_OPTION_STANDARD is set. |
| ARKWEB_SCHEME_OPTION_FETCH_ENABLED = 1 << 6 | The FETCH API request of the scheme can be initiated. |
| ARKWEB_SCHEME_OPTION_CODE_CACHE_ENABLED = 1 << 7 | The JS resources of the scheme support code cache generation. |

### ArkWeb_ResourceType

```c
enum ArkWeb_ResourceType
```

**Description**

Enumerates the resource types of the request. The resource types match the corresponding items of **ResourceType** in Chromium and should not be renumbered.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| MAIN_FRAME = 0 | Main frame. |
| SUB_FRAME = 1 | Frame or iframe. |
| STYLE_SHEET = 2 | Cascading Style Sheets (CSS). |
| SCRIPT = 3 | External script. |
| IMAGE = 4 | Image (JPG, GIF, PNG, or other format). |
| FONT_RESOURCE = 5 | Font. |
| SUB_RESOURCE = 6 | Other sub-resource. If the type is unknown, the default type is used. |
| OBJECT = 7 | The **Object** (or **embed**) tag of the plug-in, or the resource requested by the plug-in. |
| MEDIA = 8 | Media resource. |
| WORKER = 9 | Main resource of the dedicated worker thread. |
| SHARED_WORKER = 10 | Main resource of a shared worker thread. |
| PREFETCH = 11 | Explicit prefetch request. |
| FAVICON = 12 | Website icon. |
| XHR = 13 | XMLHttpRequest. |
| PING = 14 | Ping request for <a ping>/sendBeacon. |
| SERVICE_WORKER = 15 | Main resource of a service worker. |
| CSP_REPORT = 16 | Report of Content Security Policy violation. |
| PLUGIN_RESOURCE = 17 | Resource requested by the plug-in. |
| NAVIGATION_PRELOAD_MAIN_FRAME = 19 | Main frame redirection request that triggers service worker preloading. |
| NAVIGATION_PRELOAD_SUB_FRAME = 20 | Subframe redirection request that triggers service worker preloading. |


## Function description

### ArkWeb_OnRequestStart()

```c
typedef void (*ArkWeb_OnRequestStart)(const ArkWeb_SchemeHandler* schemeHandler, ArkWeb_ResourceRequest* resourceRequest, const ArkWeb_ResourceHandler* resourceHandler, bool* intercept)
```

**Description**

Called when a request starts. This callback is used on the IO thread. It intercepts and handles network requests of a specified scheme at the start of the request. Developers can use this callback to implement custom protocol handling, local resource replacement, encrypted data transmission, and other features.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)\* schemeHandler | **ArkWeb_SchemeHandler**. |
| [ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)\* resourceRequest | Object used to obtain the request information. |
| [const ArkWeb_ResourceHandler](capi-web-arkweb-resourcehandler-.md)\* resourceHandler | **ArkWeb_ResourceHandler** of the request. If **intercept** is set to **false**, this parameter should not be used. |
| bool\* intercept | Whether to intercept the request. If the value is **true**, the request will be intercepted. Otherwise, the request will not be intercepted. |

### ArkWeb_OnRequestStop()

```c
typedef void (*ArkWeb_OnRequestStop)(const ArkWeb_SchemeHandler* schemeHandler, const ArkWeb_ResourceRequest* resourceRequest)
```

**Description**

Called when the request stops. This callback is used on the IO thread. It is used to perform resource cleanup, status updates, or logging when the request completes. You should use **OH_ArkWebResourceRequest_Destroy** to destroy the **resourceRequest** and use **OH_ArkWebResourceHandler_Destroy** to destroy the **ArkWeb_ResourceHandler** received in **ArkWeb_OnRequestStart**.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)\* schemeHandler | **ArkWeb_SchemeHandler**. |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)\* resourceRequest | **ArkWeb_ResourceRequest**. |

### ArkWeb_HttpBodyStreamReadCallback()

```c
typedef void (*ArkWeb_HttpBodyStreamReadCallback)(const ArkWeb_HttpBodyStream* httpBodyStream, uint8_t* buffer, int bytesRead)
```

**Description**

Called when the **OH_ArkWebHttpBodyStream_Read** read operation is complete. This callback runs on the ArkWeb worker thread.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)\* httpBodyStream | **ArkWeb_HttpBodyStream**. |
| uint8_t\* buffer | Buffer for receiving data. |
| int bytesRead | Number of bytes read. If bytesRead is greater than 0, the buffer has been filled with bytesRead bytes of data. The developer can read data from the buffer. If the return value of OH_ArkWebHttpBodyStream_IsEof is false, the developer can continue to read the remaining data. |

### ArkWeb_HttpBodyStreamAsyncReadCallback()

```c
typedef void (*ArkWeb_HttpBodyStreamAsyncReadCallback)(const ArkWeb_HttpBodyStream *httpBodyStream, uint8_t *buffer, int bytesRead)
```

**Description**

Called when the **OH_ArkWebHttpBodyStream_AsyncRead** read operation is complete. This callback runs on the ArkWeb worker thread.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md) \*httpBodyStream | **ArkWeb_HttpBodyStream**. |
| uint8_t \*buffer | Pointer to the buffer for receiving data. |
| int bytesRead | Byte count representing the result of the asynchronous read operation. If bytesRead is greater than 0, the buffer has been filled with bytesRead bytes of data. The developer can read data from the buffer. If OH_ArkWebHttpBodyStream_IsEof returns false, the developer can continue reading the remaining data. |

### ArkWeb_HttpBodyStreamInitCallback()

```c
typedef void (*ArkWeb_HttpBodyStreamInitCallback)(const ArkWeb_HttpBodyStream* httpBodyStream, ArkWeb_NetError result)
```

**Description**

Called when **ArkWeb_HttpBodyStream** initialization is complete.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)\* httpBodyStream | **ArkWeb_HttpBodyStream**. |
| ArkWeb_NetError result | Operation result. If the operation is successful, **ARKWEB_NET_OK** is returned. Otherwise, see {@link arkweb_net_error_list.h}. |

### OH_ArkWebRequestHeaderList_Destroy()

```c
void OH_ArkWebRequestHeaderList_Destroy(ArkWeb_RequestHeaderList* requestHeaderList)
```

**Description**

Destroys an **ArkWeb_RequestHeaderList** object.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_RequestHeaderList](capi-web-arkweb-requestheaderlist-.md)* requestHeaderList | The **ArkWeb_RequestHeaderList** to be destroyed. |

### OH_ArkWebRequestHeaderList_GetSize()

```c
int32_t OH_ArkWebRequestHeaderList_GetSize(const ArkWeb_RequestHeaderList* requestHeaderList)
```

**Description**

Obtains the size of a request header list.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_RequestHeaderList](capi-web-arkweb-requestheaderlist-.md)* requestHeaderList | Request header list. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Size of the request header. If requestHeaderList is invalid, the value is -1. |

### OH_ArkWebRequestHeaderList_GetHeader()

```c
void OH_ArkWebRequestHeaderList_GetHeader(const ArkWeb_RequestHeaderList* requestHeaderList, int32_t index, char** key, char** value)
```

**Description**

Obtains a specified request header.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_RequestHeaderList](capi-web-arkweb-requestheaderlist-.md)* requestHeaderList | Request header list. |
| int32_t index | Index of the request header. The value ranges from [0, size-1], where size is the size of the request header list. The behavior is undefined when the value is out of range. |
| char** key | Key of the request header. You should use the **OH_ArkWeb_ReleaseString** function to release this string. |
| char** value | Value of the request header. You should use the **OH_ArkWeb_ReleaseString** function to release this string. |

### OH_ArkWebResourceRequest_SetUserData()

```c
int32_t OH_ArkWebResourceRequest_SetUserData(ArkWeb_ResourceRequest* resourceRequest, void* userData)
```

**Description**

Sets user data to the **ArkWeb_ResourceRequest** object. It is used to pass context information between different request callbacks or store request-associated state, which can later be retrieved through [OH_ArkWebResourceRequest_GetUserData()](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcerequest_getuserdata()).

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |
| void* userData | User data to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResourceRequest_GetUserData()

```c
void* OH_ArkWebResourceRequest_GetUserData(const ArkWeb_ResourceRequest* resourceRequest)
```

**Description**

Obtains user data from **ArkWeb_ResourceRequest**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to the user data. This pointer is set by the developer through      [OH_ArkWebResourceRequest_SetUserData](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcerequest_setuserdata) and can be used to pass custom context information in the callback. |

### OH_ArkWebResourceRequest_GetMethod()

```c
void OH_ArkWebResourceRequest_GetMethod(const ArkWeb_ResourceRequest* resourceRequest, char** method)
```

**Description**

Obtains the method of a request.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |
| char** method | HTTP request method. This function allocates memory for the **method** string. You should use **OH_ArkWeb_ReleaseString** to release the string. |

### OH_ArkWebResourceRequest_GetUrl()

```c
void OH_ArkWebResourceRequest_GetUrl(const ArkWeb_ResourceRequest* resourceRequest, char** url)
```

**Description**

Obtains the URL of a request.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |
| char** url | URL of a request. This function allocates memory for the **url** string. You should release the string using **OH_ArkWeb_ReleaseString**. |

### OH_ArkWebResourceRequest_GetHttpBodyStream()

```c
void OH_ArkWebResourceRequest_GetHttpBodyStream(const ArkWeb_ResourceRequest* resourceRequest, ArkWeb_HttpBodyStream** httpBodyStream)
```

**Description**

Creates an **ArkWeb_HttpBodyStream** to read the uploaded data of the request.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |
| [ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)** httpBodyStream | Uploaded data of the request. This function allocates memory for **httpBodyStream**. You should use **OH_ArkWebResourceRequest_DestroyHttpBodyStream** to release **httpBodyStream**. |

### OH_ArkWebResourceRequest_DestroyHttpBodyStream()

```c
void OH_ArkWebResourceRequest_DestroyHttpBodyStream(ArkWeb_HttpBodyStream* httpBodyStream)
```

**Description**

Destroys an **ArkWeb_HttpBodyStream** object.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | The **httpBodyStream** to be destroyed. |

### OH_ArkWebResourceRequest_GetResourceType()

```c
int32_t OH_ArkWebResourceRequest_GetResourceType(const ArkWeb_ResourceRequest* resourceRequest)
```

**Description**

Obtains the resource type of a request.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Resource type of the request. If resourceRequest is invalid, the value is -1, indicating that the      request object is null or invalid. For other values, see [ArkWeb_ResourceType](capi-arkweb-scheme-handler-h.md#arkweb_resourcetype). |

### OH_ArkWebResourceRequest_GetFrameUrl()

```c
void OH_ArkWebResourceRequest_GetFrameUrl(const ArkWeb_ResourceRequest* resourceRequest, char** frameUrl)
```

**Description**

Obtains the URL of the frame that triggers this request.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |
| char** frameUrl | URL of the frame that triggers the request. This function allocates memory for the URL string. You should release the string using **OH_ArkWeb_ReleaseString**. |

### OH_ArkWebHttpBodyStream_SetUserData()

```c
int32_t OH_ArkWebHttpBodyStream_SetUserData(ArkWeb_HttpBodyStream* httpBodyStream, void* userData)
```

**Description**

Sets user data to the **ArkWeb_HttpBodyStream** object.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |
| void* userData | User data to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebHttpBodyStream_GetUserData()

```c
void* OH_ArkWebHttpBodyStream_GetUserData(const ArkWeb_HttpBodyStream* httpBodyStream)
```

**Description**

Obtains user data from **ArkWeb_HttpBodyStream**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to the user data. This pointer is set by the developer through OH_ArkWebHttpBodyStream_SetUserData      and can be used to pass custom context information in the callback. |

### OH_ArkWebHttpBodyStream_SetReadCallback()

```c
int32_t OH_ArkWebHttpBodyStream_SetReadCallback(ArkWeb_HttpBodyStream* httpBodyStream, ArkWeb_HttpBodyStreamReadCallback readCallback)
```

**Description**

Sets a callback for **OH_ArkWebHttpBodyStream_Read**. The result of **OH_ArkWebHttpBodyStream_Read** is notified to the caller through **readCallback**, <br>which will run in the same thread as **OH_ArkWebHttpBodyStream_Read**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |
| [ArkWeb_HttpBodyStreamReadCallback](capi-arkweb-scheme-handler-h.md#arkweb_httpbodystreamreadcallback) readCallback | Callback of **OH_ArkWebHttpBodyStream_Read**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebHttpBodyStream_SetAsyncReadCallback()

```c
int32_t OH_ArkWebHttpBodyStream_SetAsyncReadCallback(ArkWeb_HttpBodyStream* httpBodyStream, ArkWeb_HttpBodyStreamAsyncReadCallback readCallback)
```

**Description**

Sets a callback for **OH_ArkWebHttpBodyStream_AsyncRead**. The result of **OH_ArkWebHttpBodyStream_AsyncRead**<br>is notified to the caller through **readCallback**, which runs in the ArkWeb worker thread.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |
| [ArkWeb_HttpBodyStreamAsyncReadCallback](capi-arkweb-scheme-handler-h.md#arkweb_httpbodystreamasyncreadcallback) readCallback | Callback of **OH_ArkWebHttpBodyStream_AsyncRead**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebHttpBodyStream_Init()

```c
int32_t OH_ArkWebHttpBodyStream_Init(ArkWeb_HttpBodyStream* httpBodyStream, ArkWeb_HttpBodyStreamInitCallback initCallback)
```

**Description**

Initializes **ArkWeb_HttpBodyStream**. This function establishes the internal data structures and connections of **httpBodyStream** in preparation for subsequent read operations. During initialization, it allocates necessary resources and establishes a communication mechanism with the worker thread. This function must be called before any other function; otherwise, other operations will not execute properly. This API needs to be called on the IO thread to ensure thread safety and correct initialization order.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |
| [ArkWeb_HttpBodyStreamInitCallback](capi-arkweb-scheme-handler-h.md#arkweb_httpbodystreaminitcallback) initCallback | Callback of the initialization. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebHttpBodyStream_Read()

```c
void OH_ArkWebHttpBodyStream_Read(const ArkWeb_HttpBodyStream* httpBodyStream, uint8_t* buffer, int bufLen)
```

**Description**

Reads the upload data of a request into the buffer. This function uses an asynchronous read mechanism, submitting the read task to the worker thread for execution and returning the result through a callback. The buffer size must be greater than or equal to **bufLen** to accommodate the data to be read. Data is read from the worker thread into the buffer, so the buffer should not be used in other threads before the callback returns, to avoid concurrency issues. After the read operation completes, the caller is notified through the previously set callback, which returns the actual number of bytes read.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |
| uint8_t* buffer | Buffer for receiving data. The buffer size must be greater than bufLen. |
| int bufLen | Number of bytes to read. The value must be a positive integer. The behavior is undefined if a negative number is passed. |

### OH_ArkWebHttpBodyStream_AsyncRead()

```c
void OH_ArkWebHttpBodyStream_AsyncRead(const ArkWeb_HttpBodyStream* httpBodyStream, uint8_t* buffer, int bufLen)
```

**Description**

Exports the uploaded data of a request to the buffer. The buffer size must be greater than **bufLen**. The data from the worker thread is exported to the buffer. Therefore, before the callback returns the data, the buffer should not be used in other threads to avoid concurrency problems.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |
| uint8_t* buffer | Buffer that receives data. |
| int bufLen | Number of bytes to read. |

### OH_ArkWebHttpBodyStream_GetSize()

```c
uint64_t OH_ArkWebHttpBodyStream_GetSize(const ArkWeb_HttpBodyStream* httpBodyStream)
```

**Description**

Obtains the size of **httpBodyStream**. When data is chunked or **httpBodyStream** is invalid, **0** is always returned.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |

**Returns**:

| Type | Description |
| -- | -- |
| uint64_t | Size of httpBodyStream. |

### OH_ArkWebHttpBodyStream_GetPosition()

```c
uint64_t OH_ArkWebHttpBodyStream_GetPosition(const ArkWeb_HttpBodyStream* httpBodyStream)
```

**Description**

Obtains the position of **httpBodyStream**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |

**Returns**:

| Type | Description |
| -- | -- |
| uint64_t | Current read position of httpBodyStream. The value is 0 if httpBodyStream is invalid. |

### OH_ArkWebHttpBodyStream_IsChunked()

```c
bool OH_ArkWebHttpBodyStream_IsChunked(const ArkWeb_HttpBodyStream* httpBodyStream)
```

**Description**

Determines whether **httpBodyStream** is chunked.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if chunked transfer is used; returns false otherwise. |

### OH_ArkWebHttpBodyStream_IsEof()

```c
bool OH_ArkWebHttpBodyStream_IsEof(const ArkWeb_HttpBodyStream* httpBodyStream)
```

**Description**

Determines whether all data in **httpBodyStream** has been read. **true** is returned if all data in **httpBodyStream** has been read. **false** is returned before the chunked **httpBodyStream** is read for the first time.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true is returned if all data has been read. Otherwise, false is returned. |

### OH_ArkWebHttpBodyStream_IsInMemory()

```c
bool OH_ArkWebHttpBodyStream_IsInMemory(const ArkWeb_HttpBodyStream* httpBodyStream)
```

**Description**

Determines whether all the uploaded data in **httpBodyStream** is in memory and all read requests are synchronized successfully. If yes, **true** is returned. **false** is returned if the data is chunked.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_HttpBodyStream](capi-web-arkweb-httpbodystream-.md)* httpBodyStream | **ArkWeb_HttpBodyStream**. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true is returned if all the uploaded data is stored in the memory. Otherwise, false is returned. |

### OH_ArkWebResourceRequest_Destroy()

```c
int32_t OH_ArkWebResourceRequest_Destroy(const ArkWeb_ResourceRequest* resourceRequest)
```

**Description**

Destroys an **ArkWeb_ResourceRequest** object.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResourceRequest_GetReferrer()

```c
void OH_ArkWebResourceRequest_GetReferrer(const ArkWeb_ResourceRequest* resourceRequest, char** referrer)
```

**Description**

Obtains the referrer of a request.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |
| char** referrer | Referrer of the request. This function allocates memory for the referrer string. The caller must release the string using OH_ArkWeb_ReleaseString. |

### OH_ArkWebResourceRequest_GetRequestHeaders()

```c
void OH_ArkWebResourceRequest_GetRequestHeaders(const ArkWeb_ResourceRequest* resourceRequest, ArkWeb_RequestHeaderList** requestHeaderList)
```

**Description**

Obtains the request header list **ArkWeb_RequestHeaderList** of the request. This function allocates memory for **requestHeaderList**, and the caller must use **OH_ArkWebRequestHeaderList_Destroy** to release **requestHeaderList**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |
| [ArkWeb_RequestHeaderList](capi-web-arkweb-requestheaderlist-.md)** requestHeaderList | List of request headers. |

### OH_ArkWebResourceRequest_IsRedirect()

```c
bool OH_ArkWebResourceRequest_IsRedirect(const ArkWeb_ResourceRequest* resourceRequest)
```

**Description**

Determines whether a request is redirected.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether this is a redirect. The value true indicates it is a redirect, and false indicates it is not. |

### OH_ArkWebResourceRequest_IsMainFrame()

```c
bool OH_ArkWebResourceRequest_IsMainFrame(const ArkWeb_ResourceRequest* resourceRequest)
```

**Description**

Determines whether a request is from main frame.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if this is from the main frame; false otherwise. |

### OH_ArkWebResourceRequest_HasGesture()

```c
bool OH_ArkWebResourceRequest_HasGesture(const ArkWeb_ResourceRequest* resourceRequest)
```

**Description**

Determines whether a request is triggered by a user gesture.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceRequest](capi-web-arkweb-resourcerequest-.md)* resourceRequest | **ArkWeb_ResourceRequest**. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true if triggered by a user gesture; false otherwise. |

### OH_ArkWeb_RegisterCustomSchemes()

```c
int32_t OH_ArkWeb_RegisterCustomSchemes(const char* scheme, int32_t option)
```

**Description**

Registers a custom scheme with **ArkWeb**. This function should not be called for built-in HTTP, HTTPS, FILE, FTP, ABOUT, and DATA protocols. This function should be called on the main thread before kernel initialization.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* scheme | Scheme to be registered, which must comply with RFC 3986. |
| int32_t option | Configuration (behavior) of the scheme. The value is obtained from the [ArkWeb_CustomSchemeOption](capi-arkweb-scheme-handler-h.md#arkweb_customschemeoption) enum. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Result code. Returns 0 if successful; returns 17100100 if an unknown error occurs, in which case check the      call timing and parameter configuration; returns 17100101 if the parameter is invalid; returns 17100102 if the      scheme configuration fails to be registered, in which case register before creating ArkWeb. |

### OH_ArkWebServiceWorker_SetSchemeHandler()

```c
bool OH_ArkWebServiceWorker_SetSchemeHandler(const char* scheme, ArkWeb_SchemeHandler* schemeHandler)
```

**Description**

Sets an **ArkWeb_SchemeHandler** for a specified scheme to intercept requests of the scheme type triggered by **ServiceWorker**. **SchemeHandler** should be set after **BrowserContext** is created. <br>You can use **WebviewController.initializeWebEngine** to initialize **BrowserContext** without creating the **Web** component.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* scheme | Scheme to be intercepted, which must comply with RFC 3986. |
| [ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)* schemeHandler | **ArkWeb_SchemeHandler** of the scheme. Only requests triggered by **ServiceWorker** are notified through this **schemeHandler**. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true is returned if the SchemeHandler is successfully set for the specified scheme. Otherwise,      false is returned. |

### OH_ArkWeb_SetSchemeHandler()

```c
bool OH_ArkWeb_SetSchemeHandler(const char* scheme, const char* webTag, ArkWeb_SchemeHandler* schemeHandler)
```

**Description**

Sets an **ArkWeb_SchemeHandler** to intercept requests of a specified scheme type. **SchemeHandler** should be set after **BrowserContext** is created. <br>You can use **WebviewController.initializeWebEngine** to initialize **BrowserContext** without creating the **Web** component.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* scheme | Scheme to be intercepted. |
| const char* webTag | Tag name of the Web component, used to identify a unique component. The developer must ensure the uniqueness of the name. The recommended length does not exceed 256 characters. |
| [ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)* schemeHandler | **ArkWeb_SchemeHandler** of the scheme. Only requests triggered from the specified web are notified through this **SchemeHandler**. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true is returned if the SchemeHandler is successfully set for the specified scheme. Otherwise,      false is returned. |

### OH_ArkWebServiceWorker_ClearSchemeHandlers()

```c
int32_t OH_ArkWebServiceWorker_ClearSchemeHandlers()
```

**Description**

Clears the **SchemeHandler** registered for **ServiceWorker**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned if the operation is successful. |

### OH_ArkWeb_ClearSchemeHandlers()

```c
int32_t OH_ArkWeb_ClearSchemeHandlers(const char* webTag)
```

**Description**

Clears the **SchemeHandler** registered for the specified **Web** component.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* webTag | Tag that uniquely identifies a **Web** component. Ensure that it is unique. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWeb_CreateSchemeHandler()

```c
void OH_ArkWeb_CreateSchemeHandler(ArkWeb_SchemeHandler** schemeHandler)
```

**Description**

Creates an **ArkWeb_SchemeHandler** object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)** schemeHandler | Created ArkWeb_SchemeHandler. Destroy it using [OH_ArkWeb_DestroySchemeHandler](capi-arkweb-scheme-handler-h.md#oh_arkweb_destroyschemehandler) when it is no longer needed. |

### OH_ArkWeb_DestroySchemeHandler()

```c
void OH_ArkWeb_DestroySchemeHandler(ArkWeb_SchemeHandler* schemeHandler)
```

**Description**

Destroys an **ArkWeb_SchemeHandler** object.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)* schemeHandler | The **ArkWeb_SchemeHandler** to be destroyed. |

### OH_ArkWebSchemeHandler_SetUserData()

```c
int32_t OH_ArkWebSchemeHandler_SetUserData(ArkWeb_SchemeHandler* schemeHandler, void* userData)
```

**Description**

Sets user data to the **ArkWeb_SchemeHandler** object.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)* schemeHandler | **ArkWeb_SchemeHandler**. |
| void* userData | User data to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebSchemeHandler_GetUserData()

```c
void* OH_ArkWebSchemeHandler_GetUserData(const ArkWeb_SchemeHandler* schemeHandler)
```

**Description**

Obtains the user data from **ArkWeb_SchemeHandler**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)* schemeHandler | **ArkWeb_SchemeHandler**. |

**Returns**:

| Type | Description |
| -- | -- |
| void* | Pointer to user data. This pointer is set by the developer through OH_ArkWebSchemeHandler_SetUserData and      can be used to pass custom context information in callbacks. |

### OH_ArkWebSchemeHandler_SetOnRequestStart()

```c
int32_t OH_ArkWebSchemeHandler_SetOnRequestStart(ArkWeb_SchemeHandler* schemeHandler, ArkWeb_OnRequestStart onRequestStart)
```

**Description**

Sets an **OnRequestStart** callback for **SchemeHandler**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)* schemeHandler | **SchemeHandler** of the scheme. |
| [ArkWeb_OnRequestStart](capi-arkweb-scheme-handler-h.md#arkweb_onrequeststart) onRequestStart | The callback function **OnRequestStart**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebSchemeHandler_SetOnRequestStop()

```c
int32_t OH_ArkWebSchemeHandler_SetOnRequestStop(ArkWeb_SchemeHandler* schemeHandler, ArkWeb_OnRequestStop onRequestStop)
```

**Description**

Sets an **OnRequestStop** callback for **SchemeHandler**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_SchemeHandler](capi-web-arkweb-schemehandler-.md)* schemeHandler | **SchemeHandler** of the scheme. |
| [ArkWeb_OnRequestStop](capi-arkweb-scheme-handler-h.md#arkweb_onrequeststop) onRequestStop | The callback function **OnRequestStop**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWeb_CreateResponse()

```c
void OH_ArkWeb_CreateResponse(ArkWeb_Response** response)
```

**Description**

Creates an **ArkWeb_Response** object for the intercepted request.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)** response | A created **ArkWeb_Response**. Use **OH_ArkWeb_DestroyResponse** to destroy it when it is not required. |

### OH_ArkWeb_DestroyResponse()

```c
void OH_ArkWeb_DestroyResponse(ArkWeb_Response* response)
```

**Description**

Destroys an **ArkWeb_Response** object.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)* response | The **ArkWeb_Response** to be destroyed. |

### OH_ArkWebResponse_SetUrl()

```c
int32_t OH_ArkWebResponse_SetUrl(ArkWeb_Response* response, const char* url)
```

**Description**

Sets the resolved URL after redirection or HSTS changes. After setting, a navigation is triggered. It is used to implement URL redirection in custom responses, such as URL normalization, domain redirection, and HTTP-to-HTTPS upgrade.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| const char* url | Parsed URL. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResponse_GetUrl()

```c
void OH_ArkWebResponse_GetUrl(const ArkWeb_Response* response, char** url)
```

**Description**

Obtains the parsed URL that has been redirected or changed due to HSTS.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| char** url | Parsed URL. This function allocates memory for the URL string. The caller must release the string using OH_ArkWeb_ReleaseString. |

### OH_ArkWebResponse_SetError()

```c
int32_t OH_ArkWebResponse_SetError(ArkWeb_Response* response, ArkWeb_NetError errorCode)
```

**Description**

Sets an error code for the **ArkWeb_Response** object. It is used together with **DidFailWithError** to inform the client of the specific reason for the request failure through the error code, such as permission errors or resource not found.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| ArkWeb_NetError errorCode | Error code of the failed request. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResponse_GetError()

```c
ArkWeb_NetError OH_ArkWebResponse_GetError(const ArkWeb_Response* response)
```

**Description**

Obtains the error code of **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkWeb_NetError | Error code of ArkWeb_Response. |

### OH_ArkWebResponse_SetStatus()

```c
int32_t OH_ArkWebResponse_SetStatus(ArkWeb_Response* response, int status)
```

**Description**

Sets an HTTP status code for **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| int status | HTTP status code of the response. The value ranges from 100 to 599 and must comply with HTTP standard status code specifications (informational 100-199, success 200-299, redirection 300-399, client error 400-499, server error 500-599). The behavior is undefined when the value is out of range. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResponse_GetStatus()

```c
int OH_ArkWebResponse_GetStatus(const ArkWeb_Response* response)
```

**Description**

Obtains the HTTP status code of **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |

**Returns**:

| Type | Description |
| -- | -- |
| int | HTTP status code of ArkWeb_Response. If ArkWeb_Response is invalid, the value is -1. |

### OH_ArkWebResponse_SetStatusText()

```c
int32_t OH_ArkWebResponse_SetStatusText(ArkWeb_Response* response, const char* statusText)
```

**Description**

Sets a status text for **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| const char* statusText | Status text of the response. Setting the status text provides a more detailed description for the HTTP status code. For example, status code 200 can correspond to "OK", status code 404 can correspond to "Not Found", etc., helping the client better understand the request result. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResponse_GetStatusText()

```c
void OH_ArkWebResponse_GetStatusText(const ArkWeb_Response* response, char** statusText)
```

**Description**

Obtains the status text of **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| char** statusText | Status text of **ArkWeb_Response**. This function allocates memory for the **statusText** string. You need to release the string using **OH_ArkWeb_ReleaseString**. |

### OH_ArkWebResponse_SetMimeType()

```c
int32_t OH_ArkWebResponse_SetMimeType(ArkWeb_Response* response, const char* mimeType)
```

**Description**

Sets a mime type for **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| const char* mimeType | Media type of the response. Setting the media type tells the client the type of the response content, for example, text/html indicates an HTML document, application/json indicates JSON data, image/png indicates a PNG image, etc. The browser selects an appropriate rendering mode based on the media type. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResponse_GetMimeType()

```c
void OH_ArkWebResponse_GetMimeType(const ArkWeb_Response* response, char** mimeType)
```

**Description**

Obtains the mime type of **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| char** mimeType | Mime type of **ArkWeb_Response**. This function allocates memory for the **mimeType** string. You need to release the string using **OH_ArkWeb_ReleaseString**. |

### OH_ArkWebResponse_SetCharset()

```c
int32_t OH_ArkWebResponse_SetCharset(ArkWeb_Response* response, const char* charset)
```

**Description**

Sets a character set for **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| const char* charset | Character set of the response. Setting the character set tells the client the character encoding used for the response content. For example, UTF-8 indicates that UTF-8 encoding is used, GBK indicates that GBK encoding is used, and so on. The browser correctly parses and displays the text content based on the character set. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResponse_GetCharset()

```c
void OH_ArkWebResponse_GetCharset(const ArkWeb_Response* response, char** charset)
```

**Description**

Obtains the character set of **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| char** charset | Character set of **ArkWeb_Response**. This function allocates memory for the **charset** string. You need to release the string using **OH_ArkWeb_ReleaseString**. |

### OH_ArkWebResponse_SetHeaderByName()

```c
int32_t OH_ArkWebResponse_SetHeaderByName(ArkWeb_Response* response, const char* name, const char* value, bool overwrite)
```

**Description**

Sets a header for **ArkWeb_Response**.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| const char* name | Name of the header. Specifies the name of the HTTP response header to set, for example, Content-Type, Content-Length, or Cache-Control. Different headers affect how the browser processes the response. |
| const char* value | Value of the header. Specifies the value of the HTTP response header, for example, text/html for Content-Type or no-cache for Cache-Control. The actual effect depends on the combination of the header name and value. |
| bool overwrite | Whether to overwrite the existing header. The value **true** means to overwrite the existing header, and **false** means the opposite. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResponse_GetHeaderByName()

```c
void OH_ArkWebResponse_GetHeaderByName(const ArkWeb_Response* response, const char* name, char** value)
```

**Description**

Obtains the header from **ArkWeb_Response**.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response**. |
| const char* name | Name of the header. |
| char** value | Value of the header. This function allocates memory for the **value **string. You need to release the string using **OH_ArkWeb_ReleaseString**. |

### OH_ArkWebResourceHandler_Destroy()

```c
int32_t OH_ArkWebResourceHandler_Destroy(const ArkWeb_ResourceHandler* resourceHandler)
```

**Description**

Destroys an **ArkWeb_ResourceHandler** object.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceHandler](capi-web-arkweb-resourcehandler-.md)* resourceHandler | **ArkWeb_ResourceHandler**. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResourceHandler_DidReceiveResponse()

```c
int32_t OH_ArkWebResourceHandler_DidReceiveResponse(const ArkWeb_ResourceHandler* resourceHandler, const ArkWeb_Response* response)
```

**Description**

Passes the constructed response header to the intercepted request. Called when intercepting a request and preparing to return a custom response, it is used to set response header information such as the HTTP response status code, media type, and character set.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceHandler](capi-web-arkweb-resourcehandler-.md)* resourceHandler | **ArkWeb_ResourceHandler** of the request. |
| [const ArkWeb_Response](capi-web-arkweb-response-.md)* response | **ArkWeb_Response** of the intercepted request. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResourceHandler_DidReceiveData()

```c
int32_t OH_ArkWebResourceHandler_DidReceiveData(const ArkWeb_ResourceHandler* resourceHandler, const uint8_t* buffer, int64_t bufLen)
```

**Description**

Passes the constructed response body to the intercepted request. Called after setting the response header, it is used to send response data. It can be called multiple times for chunked transfer of data. After the transfer is complete, **OH_ArkWebResourceHandler_DidFinish** must be called to notify the end of the request.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceHandler](capi-web-arkweb-resourcehandler-.md)* resourceHandler | **ArkWeb_ResourceHandler** of the request. |
| const uint8_t* buffer | Buffer data to be sent. |
| int64_t bufLen | Size of the buffer, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResourceHandler_DidFinish()

```c
int32_t OH_ArkWebResourceHandler_DidFinish(const ArkWeb_ResourceHandler* resourceHandler)
```

**Description**

Notifies the ArkWeb kernel that the intercepted request is complete and no more data is available. This function sends a completion signal to the kernel, which will end the processing of the request and clean up related internal resources. After calling this function, no other processing functions can be called for this request. If an error occurs during the request, use **OH_ArkWebResourceHandler_DidFailWithError** to notify the kernel.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceHandler](capi-web-arkweb-resourcehandler-.md)* resourceHandler | **ArkWeb_ResourceHandler** of the request. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResourceHandler_DidFailWithError()

```c
int32_t OH_ArkWebResourceHandler_DidFailWithError(const ArkWeb_ResourceHandler* resourceHandler, ArkWeb_NetError errorCode)
```

**Description**

Notifies the ArkWeb kernel that the intercepted request should fail. Called in scenarios such as permission verification failure, resource not found, or network errors, it is used to mark the request as failed and inform the client of the specific failure reason through an error code.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceHandler](capi-web-arkweb-resourcehandler-.md)* resourceHandler | Handler for intercepted URL requests. You can use **ArkWeb_ResourceHandler** to send custom request headers and bodies. |
| ArkWeb_NetError errorCode | Error code of the request. For details, see {@link arkweb_net_error_list.h}. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWebResourceHandler_DidFailWithErrorV2()

```c
int32_t OH_ArkWebResourceHandler_DidFailWithErrorV2(const ArkWeb_ResourceHandler* resourceHandler, ArkWeb_NetError errorCode, bool completeIfNoResponse)
```

**Description**

Notifies the ArkWeb kernel that the intercepted request fails. Compared with the [OH_ArkWebResourceHandler_DidFailWithError](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didfailwitherror) API, the **completeIfNoResponse** parameter is added. With this parameter set to **true**, if [OH_ArkWebResourceHandler_DidReceiveResponse](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didreceiveresponse) has not been called, a response is automatically generated to complete the network request and the network error code is **-104**. With this parameter set to **false**, the system waits for the application to call [OH_ArkWebResourceHandler_DidReceiveResponse](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didreceiveresponse) and pass the response.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceHandler](capi-web-arkweb-resourcehandler-.md)* resourceHandler | Handler for intercepted URL requests. You can use **ArkWeb_ResourceHandler** to send custom request headers and bodies. |
| ArkWeb_NetError errorCode | Error code of the request. For details, see {@link arkweb_net_error_list.h}. |
| bool completeIfNoResponse | Whether the network request is complete when [OH_ArkWebResourceHandler_DidFailWithErrorV2](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didfailwitherrorv2) is called if [OH_ArkWebResourceHandler_DidReceiveResponse](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didreceiveresponse) is not called before. If the value is **true** and [OH_ArkWebResourceHandler_DidReceiveResponse](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didreceiveresponse) is not called before, a response is automatically generated to complete the network request, and the network error code is **-104**. If the value is **false**, the system waits for the application to call [OH_ArkWebResourceHandler_DidReceiveResponse](capi-arkweb-scheme-handler-h.md#oh_arkwebresourcehandler_didreceiveresponse) and pass the response. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | 0 is returned when the operation is successful; 17100101 is returned when the parameter is invalid. |

### OH_ArkWeb_CreateErrorInfo()

```c
void OH_ArkWeb_CreateErrorInfo(ArkWeb_ErrorInfo** errorInfo)
```

**Description**

Creates an ArkWeb_ErrorInfo object.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)** errorInfo | The created ArkWeb_ErrorInfo object. If errorInfo is nullptr, this function does nothing. If the creation succeeds, *errorInfo points to the newly created object, which must be destroyed using [OH_ArkWeb_DestroyErrorInfo](capi-arkweb-scheme-handler-h.md#oh_arkweb_destroyerrorinfo) when no longer needed. If the creation fails, *errorInfo is set to NULL. |

### OH_ArkWeb_DestroyErrorInfo()

```c
void OH_ArkWeb_DestroyErrorInfo(ArkWeb_ErrorInfo* errorInfo)
```

**Description**

Destroys the ArkWeb_ErrorInfo.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)* errorInfo | The ArkWeb_ErrorInfo to be destroyed. |

### OH_ArkWebErrorInfo_SetCompleteIfNoResponse()

```c
int32_t OH_ArkWebErrorInfo_SetCompleteIfNoResponse(ArkWeb_ErrorInfo* errorInfo, bool completeIfNoResponse)
```

**Description**

Sets whether to automatically generate a response if no response has been received.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)* errorInfo | The ArkWeb_ErrorInfo. |
| bool completeIfNoResponse | If true, a response will be automatically constructed when no response has been received. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ARKWEB_NET_OK} 0 - Success.<br>        {@link ARKWEB_INVALID_PARAM} 17100101 - Invalid param, errorInfo is nullptr. |

### OH_ArkWebErrorInfo_GetCompleteIfNoResponse()

```c
bool OH_ArkWebErrorInfo_GetCompleteIfNoResponse(const ArkWeb_ErrorInfo* errorInfo)
```

**Description**

Gets whether to automatically generate a response if no response has been received.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)* errorInfo | The ArkWeb_ErrorInfo. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if automatically generating a response when no response has been received is enabled,          returns false otherwise. |

### OH_ArkWebErrorInfo_SetCustomErrorCode()

```c
int32_t OH_ArkWebErrorInfo_SetCustomErrorCode(ArkWeb_ErrorInfo* errorInfo, int32_t errorCode)
```

**Description**

Sets the custom error code for ArkWeb_ErrorInfo.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)* errorInfo | The ArkWeb_ErrorInfo. |
| int32_t errorCode | The custom error code, the web engine will pass the custom error code directly to the application through onErrorReceive. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ARKWEB_NET_OK} 0 - Success.<br>        {@link ARKWEB_INVALID_PARAM} 17100101 - Invalid param, errorInfo is nullptr. |

### OH_ArkWebErrorInfo_GetCustomErrorCode()

```c
int32_t OH_ArkWebErrorInfo_GetCustomErrorCode(const ArkWeb_ErrorInfo* errorInfo)
```

**Description**

Gets the custom error code from the ArkWeb_ErrorInfo.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)* errorInfo | The ArkWeb_ErrorInfo. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | The custom error code. |

### OH_ArkWebErrorInfo_SetErrorCode()

```c
int32_t OH_ArkWebErrorInfo_SetErrorCode(ArkWeb_ErrorInfo* errorInfo, ArkWeb_NetError errorCode)
```

**Description**

Sets the error code for ArkWeb_ErrorInfo.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)* errorInfo | The ArkWeb_ErrorInfo. |
| ArkWeb_NetError errorCode | The error code for this request. Refer to arkweb_net_error_list.h. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ARKWEB_NET_OK} 0 - Success.<br>        {@link ARKWEB_INVALID_PARAM} 17100101 - Invalid param, errorInfo is nullptr. |

### OH_ArkWebErrorInfo_GetErrorCode()

```c
ArkWeb_NetError OH_ArkWebErrorInfo_GetErrorCode(const ArkWeb_ErrorInfo* errorInfo)
```

**Description**

Gets the error code from the ArkWeb_ErrorInfo. Refer to arkweb_net_error_list.h.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)* errorInfo | The ArkWeb_ErrorInfo. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkWeb_NetError | The error code. |

### OH_ArkWebResponse_SetErrorInfo()

```c
int32_t OH_ArkWebResponse_SetErrorInfo(ArkWeb_Response* response, ArkWeb_ErrorInfo* errorInfo)
```

**Description**

Sets the error info for the ArkWeb_Response.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_Response](capi-web-arkweb-response-.md)* response | The ArkWeb_Response. |
| [ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)* errorInfo | The ArkWeb_ErrorInfo to set. Ownership is not transferred; the caller must keep errorInfo valid until [ArkWeb_OnRequestStop](capi-arkweb-scheme-handler-h.md#arkweb_onrequeststop) is triggered. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ARKWEB_NET_OK} 0 - Success.<br>        {@link ARKWEB_INVALID_PARAM} 17100101 - Invalid param, response or errorInfo is nullptr. |

### OH_ArkWebResponse_GetErrorInfo()

```c
ArkWeb_ErrorInfo* OH_ArkWebResponse_GetErrorInfo(const ArkWeb_Response* response)
```

**Description**

Gets the error info from the ArkWeb_Response.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_Response](capi-web-arkweb-response-.md)* response | The ArkWeb_Response. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkWeb_ErrorInfo*](capi-web-arkweb-errorinfo-.md) | The pointer to the ArkWeb_ErrorInfo if set; NULL otherwise. |

### OH_ArkWebResourceHandler_DidFailWithErrorInfo()

```c
int32_t OH_ArkWebResourceHandler_DidFailWithErrorInfo(const ArkWeb_ResourceHandler* resourceHandler, const ArkWeb_ErrorInfo* errorInfo)
```

**Description**

Notify the web engine that this request should fail with error info.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const ArkWeb_ResourceHandler](capi-web-arkweb-resourcehandler-.md)* resourceHandler | The ArkWeb_ResourceHandler for the request. |
| [const ArkWeb_ErrorInfo](capi-web-arkweb-errorinfo-.md)* errorInfo | The error info for this request. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ARKWEB_NET_OK} 0 - Success.<br>        {@link ARKWEB_INVALID_PARAM} 17100101 - Invalid param, resourceHandler or errorInfo is nullptr. |

### OH_ArkWeb_ReleaseString()

```c
void OH_ArkWeb_ReleaseString(char* string)
```

**Description**

Releases the string created by NDK APIs.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* string | String to be released. |

### OH_ArkWeb_ReleaseByteArray()

```c
void OH_ArkWeb_ReleaseByteArray(uint8_t* byteArray)
```

**Description**

Releases the byte array created by NDK APIs.

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint8_t* byteArray | Byte array to be released. |


