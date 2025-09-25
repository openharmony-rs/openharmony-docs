# ArkWeb_ControllerAPI


## Overview

Defines a native API struct of the Web controller. Before calling the API, you are advised to use **ARKWEB_MEMBER_MISSING** to check whether the function struct has the corresponding pointer to avoid crash caused by mismatch between the SDK and the device ROM.

**Since**: 12

**Related module**: [Web](_web.md)

**Header file**: [arkweb_type.h](arkweb__type_8h.md)

## Summary


### Member Variables

| Name| Description|
| -------- | -------- |
| size_t [size](#size) | Size of the struct. |
| void(\* [runJavaScript](#runjavascript) )(const char \*webTag, const [ArkWeb_JavaScriptObject](_ark_web___java_script_object.md) \*javascriptObject) | Pointer to the function used to inject a JavaScript script. |
| void(\* [registerJavaScriptProxy](#registerjavascriptproxy) )(const char \*webTag, const [ArkWeb_ProxyObject](_ark_web___proxy_object.md) \*proxyObject) | Pointer to the function used to register a JavaScript proxy with the window. APIs of this object can then be invoked in the window. |
| void(\* [deleteJavaScriptRegister](#deletejavascriptregister) )(const char \*webTag, const char \*objName) | Pointer to the function used to delete a specific application JavaScript object that is registered with the window using **registerJavaScriptProxy**. |
| void(\* [refresh](#refresh) )(const char \*webTag) | Pointer to the function used to refresh the web page. |
| void(\* [registerAsyncJavaScriptProxy](#registerasyncjavascriptproxy) )(const char \*webTag, const [ArkWeb_ProxyObject](_ark_web___proxy_object.md) \*proxyObject) | Pointer to the function used to register a JavaScript proxy with the window. Asynchronous APIs of this object can then be invoked in the window. |
| [ArkWeb_WebMessagePortPtr](_web.md#arkweb_webmessageportptr) \*(\* [createWebMessagePorts](#createwebmessageports) )(const char \*webTag, size_t \*[size](#size)) | Pointer to the function used to create message ports. |
| void(\* [destroyWebMessagePorts](#destroywebmessageports) )([ArkWeb_WebMessagePortPtr](_web.md#arkweb_webmessageportptr) \*\*ports, size_t [size](#size)) | Pointer to the function used to destroy message ports. |
| [ArkWeb_ErrorCode](_web.md#arkweb_errorcode)(\* [postWebMessage](#postwebmessage) )(const char \*webTag, const char \*name, [ArkWeb_WebMessagePortPtr](_web.md#arkweb_webmessageportptr) \*webMessagePorts, size_t [size](#size), const char \*url) | Pointer to the function used to send the message port to the HTML page. |
| const char \*(\* [getLastJavascriptProxyCallingFrameUrl](#getlastjavascriptproxycallingframeurl) )() | Pointer to the function used to obtain the URL of the last frame that calls **JavaScriptProxy**. This function is invoked on the thread invoked by the **JavaScriptProxy**. You can use **registerJavaScriptProxy** or **JavaScriptProxy** to inject a JavaScript object to a window object.   You need to save the URL obtained from the invoked function. |
| void(\* [registerJavaScriptProxyEx](#registerjavascriptproxyex) )(const char \*webTag, const [ArkWeb_ProxyObjectWithResult](_ark_web___proxy_object_with_result.md) \*proxyObject, const char \*permission) | Pointer to the function used to register a JavaScript object with the window. APIs of this object can then be invoked in the window. The synchronization method of this object can contain return values. |
| void(\* [registerAsyncJavaScriptProxyEx](#registerasyncjavascriptproxyex) )(const char \*webTag, const [ArkWeb_ProxyObject](_ark_web___proxy_object.md) \*proxyObject, const char \*permission) | Pointer to the function used to register a JavaScript proxy with the window. Asynchronous APIs of this object can then be invoked in the window. |


## Member Variable Description


### createWebMessagePorts

```
ArkWeb_WebMessagePortPtr*(* ArkWeb_ControllerAPI::createWebMessagePorts) (const char *webTag, size_t *size)
```
**Description**

Pointer to the function used to create message ports.

**Parameters**

| Name| Description|
| -------- | -------- |
| webTag | Name of a **Web** component. |
| size | Number of ports, which is an output parameter. |

**Returns**

Pointer to the message port struct.


### deleteJavaScriptRegister

```
void(* ArkWeb_ControllerAPI::deleteJavaScriptRegister) (const char *webTag, const char *objName)
```
**Description**

Pointer to the function used to delete a specific application JavaScript object that is registered with the window using **registerJavaScriptProxy**.

**Parameters**

| Name| Description|
| -------- | -------- |
| webTag | Name of a **Web** component. |
| objName | Name of a JavaScript object. |

### destroyWebMessagePorts

```
void(* ArkWeb_ControllerAPI::destroyWebMessagePorts) (ArkWeb_WebMessagePortPtr **ports, size_t size)
```
**Description**

Pointer to the function used to destroy message ports.

**Parameters**

| Name| Description|
| -------- | -------- |
| ports | Pointer array of the message port struct. |
| size | Number of ports.|


### getLastJavascriptProxyCallingFrameUrl

```
const char*(* ArkWeb_ControllerAPI::getLastJavascriptProxyCallingFrameUrl) ()
```
**Description**

Pointer to the function used to obtain the URL of the last frame that calls **JavaScriptProxy**. This function is invoked on the thread invoked by the **JavaScriptProxy**. You can use **registerJavaScriptProxy** or **JavaScriptProxy** to inject a JavaScript object to a window object.   You need to save the URL obtained from the invoked function.

**Since**: 14

**Returns**

URL of the last frame that invokes the **JavaScriptProxy**.


### postWebMessage

```
ArkWeb_ErrorCode(* ArkWeb_ControllerAPI::postWebMessage) (const char *webTag, const char *name, ArkWeb_WebMessagePortPtr *webMessagePorts, size_t size, const char *url)
```
**Description**

Pointer to the function used to send the message port to the HTML page.

**Parameters**

| Name| Description|
| -------- | -------- |
| webTag | Name of a **Web** component. |
| name | Name of the message sent to the HTML page. |
| webMessagePorts | Pointer to the message port struct. |
| size | Number of ports. |
| url | URL of the page that receives the message. |

**Returns**

  [ARKWEB_SUCCESS](_web.md#arkweb_errorcode-1) is returned if the operation is successful. [ARKWEB_INVALID_PARAM](_web.md#arkweb_errorcode-1) is returned if the parameter is invalid. [ARKWEB_INIT_ERROR](_web.md#arkweb_errorcode-1) is returned if the initialization fails, that is, the **Web** component bound to the **webTag** is not found.


### refresh

```
void(* ArkWeb_ControllerAPI::refresh) (const char *webTag)
```
**Description**

Pointer to the function used to refresh the web page. The page stack is cleared during the refresh. As a result, the current page cannot be navigated forward or backward.


### registerAsyncJavaScriptProxy

```
void(* ArkWeb_ControllerAPI::registerAsyncJavaScriptProxy) (const char *webTag, const ArkWeb_ProxyObject *proxyObject)
```
**Description**

Pointer to the function used to register a JavaScript proxy with the window. Asynchronous APIs of this object can then be invoked in the window.


### registerAsyncJavaScriptProxyEx

```
void(* ArkWeb_ControllerAPI::registerAsyncJavaScriptProxyEx) (const char *webTag, const ArkWeb_ProxyObject *proxyObject, const char *permission)
```
**Description**

Pointer to the function used to register a JavaScript proxy with the window. Asynchronous APIs of this object can then be invoked in the window.

**Since**: 18

**Parameters**

| Name| Description|
| -------- | -------- |
| webTag | Name of a **Web** component. |
| proxyObject | The proxy object to be registered. |
| permission |  A JSON string used to configure the object and method levels of the JSBridge permission. This value is empty by default.|


### registerJavaScriptProxy

```
void(* ArkWeb_ControllerAPI::registerJavaScriptProxy) (const char *webTag, const ArkWeb_ProxyObject *proxyObject)
```
**Description**

Pointer to the function used to register a JavaScript object with the window. APIs of this object can then be invoked in the window.


### registerJavaScriptProxyEx

```
void(* ArkWeb_ControllerAPI::registerJavaScriptProxyEx) (const char *webTag, const ArkWeb_ProxyObjectWithResult *proxyObject, const char *permission)
```
**Description**

Pointer to the function used to register a JavaScript object with the window. APIs of this object can then be invoked in the window. The synchronization method of this object can contain return values.

**Since**: 18

**Parameters**

| Name| Description|
| -------- | -------- |
| webTag | Name of a **Web** component. |
| proxyObject | The proxy object to be registered. |
| permission |  A JSON string used to configure the object and method levels of the JSBridge permission. This value is empty by default.|


### runJavaScript

```
void(* ArkWeb_ControllerAPI::runJavaScript) (const char *webTag, const ArkWeb_JavaScriptObject *javascriptObject)
```
**Description**

Pointer to the function used to inject a JavaScript script.


### size

```
size_t ArkWeb_ControllerAPI::size
```
**Description**

Size of the struct.
