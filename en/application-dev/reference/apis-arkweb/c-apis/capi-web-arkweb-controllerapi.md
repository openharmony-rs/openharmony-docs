# ArkWeb_ControllerAPI

```c
typedef struct ArkWeb_ControllerAPI {...} ArkWeb_ControllerAPI
```

## Overview

ArkWeb_ControllerAPI is a native API struct related to the controller. This struct provides features such as JavaScript injection, synchronous and asynchronous JavaScript proxy registration, proxy deletion, page refresh, Web Message Port creation and management, and Frame URL query. It supports the coexistence of synchronous and asynchronous proxies and unified management and control of WebView behavior. It is suitable for scenarios where JavaScript needs to be injected and called from native code and bidirectional communication between native and pages is required. It resolves JSBridge intercommunication and secure injection issues, improving development efficiency and controllability. This is the primary interface for controlling WebView behavior from native code.<br>Controller- related APIs must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Before calling, you are advised to use {@link ARKWEB_MEMBER_MISSING} to check the availability of the function pointer to avoid crashes caused by mismatches between the SDK and the device ROM.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t size | Size of the struct. |


### Member functions

| Name | Description |
| -- | -- |
| [void (\*runJavaScript)(const char* webTag, const ArkWeb_JavaScriptObject* javascriptObject)](#runjavascript) | Injects a JavaScript script. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. This method injects a JavaScript script into the execution context of the **Web** component and executes it after the page is loaded. |
| [void (\*registerJavaScriptProxy)(const char* webTag, const ArkWeb_ProxyObject* proxyObject)](#registerjavascriptproxy) | Injects a JavaScript object into the window object and calls the synchronous methods of this object in the window object. This method maps native objects to the JavaScript environment through a bridging mechanism to implement bidirectional communication. Use Cases: for example, JS calls native capabilities to obtain device information or execute native business logic. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Compared with registerAsyncJavaScriptProxy, this method is suitable for scenarios where a synchronous return value is required. If a synchronous return value is not needed or the operation is time-consuming, you are advised to use registerAsyncJavaScriptProxy to avoid blocking the UI thread. |
| [void (\*deleteJavaScriptRegister)(const char* webTag, const char* objName)](#deletejavascriptregister) | Deletes the app-side JavaScript object with the specified name that is registered with the window through registerJavaScriptProxy. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. This method unbinds the JavaScript object from the native object and releases related resources. Use Cases: for example, cleaning up registered objects to avoid residue when a component is destroyed, a module is unloaded, or services are switched. |
| [void (\*refresh)(const char* webTag)](#refresh) | Refreshes the current web page. The page stack is cleared during the refresh, as a result, the current page cannot be navigated forward or backward. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. |
| [void (\*registerAsyncJavaScriptProxy)(const char* webTag, const ArkWeb_ProxyObject* proxyObject)](#registerasyncjavascriptproxy) | Injects a JavaScript object into the window object and calls the asynchronous methods of this object in the window object. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. This method implements asynchronous calls through a message queue mechanism to avoid blocking the main thread. Compared with registerJavaScriptProxy, this method is suitable for time-consuming operations or scenarios where a synchronous return value is not needed. If a synchronous return value is needed, you are advised to use registerJavaScriptProxy. |
| [ArkWeb_WebMessagePortPtr* (\*createWebMessagePorts)(const char* webTag, size_t* size)](#createwebmessageports) | Creates a Post Message port. The Post Message port provides a bidirectional communication mechanism, allowing the native layer and the web layer to securely exchange data messages. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Use Cases: for example, implementing cross-context message channels to support data transfer between iframes and the main page, and between Web and Worker. |
| [void (\*destroyWebMessagePorts)(ArkWeb_WebMessagePortPtr** ports, size_t size)](#destroywebmessageports) | Destroys a port. This method closes the port connection, releases related system resources, and stops message transmission. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Use Cases: for example, releasing port resources to avoid leaks when communication ends or the component lifecycle ends. |
| [ArkWeb_ErrorCode (\*postWebMessage)(const char* webTag, const char* name, ArkWeb_WebMessagePortPtr* webMessagePorts, size_t size, const char* url)](#postwebmessage) | Sends ports to the HTML main page. This method passes Post Message ports to the specified HTML page through a message delivery mechanism to establish a cross-origin communication channel. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Use Cases: for example, establishing a bidirectional message channel between the main page and an iframe, or pushing messages across frames. |
| [const char* (\*getLastJavascriptProxyCallingFrameUrl)()](#getlastjavascriptproxycallingframeurl) | Obtains the URL of the last frame that calls JavaScriptProxy. This method records the frame context of the last JavaScript call through a frame stack tracing mechanism. It is called on the thread where JavaScriptProxy is called. A JavaScript object is injected into the window object through registerJavaScriptProxy or JavaScriptProxy. This API can obtain the URL of the frame that last called the injected object. If the injected object has never been called, the return value is undefined. The correct URL can be obtained only when this API is called inside the called function. You can obtain the URL inside the function and save it. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. |
| [void (\*registerJavaScriptProxyEx)(const char* webTag, const ArkWeb_ProxyObjectWithResult* proxyObject,const char* permission)](#registerjavascriptproxyex) | Injects a JavaScript object into the window object and calls the synchronous methods of this object in the window object. The synchronous methods of this object can carry return values. This method implements bidirectional data transfer and synchronous calls between JavaScript and native through a synchronous bridging mechanism. Compared with registerJavaScriptProxy, this method adds a permission parameter for configuring JSBridge permission restrictions, and is suitable for scenarios that require permission control or synchronous return values. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Use Cases: for example, business scenarios where synchronous return results are needed when JS calls native. |
| [void (\*registerAsyncJavaScriptProxyEx)(const char* webTag, const ArkWeb_ProxyObject* proxyObject,const char* permission)](#registerasyncjavascriptproxyex) | Injects a JavaScript object into the window object and calls the asynchronous methods of this object in the window object. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. This method implements asynchronous calls through a message queue mechanism to avoid blocking the main thread. Compared with registerAsyncJavaScriptProxy, this method adds a permission parameter for configuring JSBridge permission restrictions, and is suitable for asynchronous operation scenarios that require permission control. |

## Member function description

### runJavaScript()

```c
void (*runJavaScript)(const char* webTag, const ArkWeb_JavaScriptObject* javascriptObject)
```

**Description**

Injects a JavaScript script. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. This method injects a JavaScript script into the execution context of the **Web** component and executes it after the page is loaded.

### registerJavaScriptProxy()

```c
void (*registerJavaScriptProxy)(const char* webTag, const ArkWeb_ProxyObject* proxyObject)
```

**Description**

Injects a JavaScript object into the window object and calls the synchronous methods of this object in the window object. This method maps native objects to the JavaScript environment through a bridging mechanism to implement bidirectional communication. Use Cases: for example, JS calls native capabilities to obtain device information or execute native business logic. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Compared with registerAsyncJavaScriptProxy, this method is suitable for scenarios where a synchronous return value is required. If a synchronous return value is not needed or the operation is time-consuming, you are advised to use registerAsyncJavaScriptProxy to avoid blocking the UI thread.

### deleteJavaScriptRegister()

```c
void (*deleteJavaScriptRegister)(const char* webTag, const char* objName)
```

**Description**

Deletes the app-side JavaScript object with the specified name that is registered with the window through registerJavaScriptProxy. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. This method unbinds the JavaScript object from the native object and releases related resources. Use Cases: for example, cleaning up registered objects to avoid residue when a component is destroyed, a module is unloaded, or services are switched.

### refresh()

```c
void (*refresh)(const char* webTag)
```

**Description**

Refreshes the current web page. The page stack is cleared during the refresh, as a result, the current page cannot be navigated forward or backward. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method.

### registerAsyncJavaScriptProxy()

```c
void (*registerAsyncJavaScriptProxy)(const char* webTag, const ArkWeb_ProxyObject* proxyObject)
```

**Description**

Injects a JavaScript object into the window object and calls the asynchronous methods of this object in the window object. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. This method implements asynchronous calls through a message queue mechanism to avoid blocking the main thread. Compared with registerJavaScriptProxy, this method is suitable for time-consuming operations or scenarios where a synchronous return value is not needed. If a synchronous return value is needed, you are advised to use registerJavaScriptProxy.

### createWebMessagePorts()

```c
ArkWeb_WebMessagePortPtr* (*createWebMessagePorts)(const char* webTag, size_t* size)
```

**Description**

Creates a Post Message port. The Post Message port provides a bidirectional communication mechanism, allowing the native layer and the web layer to securely exchange data messages. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Use Cases: for example, implementing cross-context message channels to support data transfer between iframes and the main page, and between Web and Worker.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* webTag | Name of the **Web** component. |
|  size_t* size | Number of ports, which is an output parameter. |

### destroyWebMessagePorts()

```c
void (*destroyWebMessagePorts)(ArkWeb_WebMessagePortPtr** ports, size_t size)
```

**Description**

Destroys a port. This method closes the port connection, releases related system resources, and stops message transmission. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Use Cases: for example, releasing port resources to avoid leaks when communication ends or the component lifecycle ends.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md)** ports | Array of pointers to the Post Message port struct. |
|  size_t size | Number of ports. Must be equal to the number of ports in the ports array. |

### postWebMessage()

```c
ArkWeb_ErrorCode (*postWebMessage)(const char* webTag, const char* name, ArkWeb_WebMessagePortPtr* webMessagePorts, size_t size, const char* url)
```

**Description**

Sends ports to the HTML main page. This method passes Post Message ports to the specified HTML page through a message delivery mechanism to establish a cross-origin communication channel. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Use Cases: for example, establishing a bidirectional message channel between the main page and an iframe, or pushing messages across frames.

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* webTag | Name of the Web component. It must match the bound Web component; otherwise, ARKWEB_INIT_ERROR is returned. |
|  const char* name | Name of the message sent to the HTML page. |
|  size_t size | Number of ports. |
|  const char* url | URL of the page that receives the message. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkWeb_ErrorCode | Result code.          <br>{@link ARKWEB_SUCCESS}: success.<br>    <br>{@link ARKWEB_INVALID_PARAM}: invalid parameter.<br>    <br>{@link ARKWEB_INIT_ERROR}: initialization failed; no Web component bound to the webTag is found. |

### getLastJavascriptProxyCallingFrameUrl()

```c
const char* (*getLastJavascriptProxyCallingFrameUrl)()
```

**Description**

Obtains the URL of the last frame that calls JavaScriptProxy. This method records the frame context of the last JavaScript call through a frame stack tracing mechanism. It is called on the thread where JavaScriptProxy is called. A JavaScript object is injected into the window object through registerJavaScriptProxy or JavaScriptProxy. This API can obtain the URL of the frame that last called the injected object. If the injected object has never been called, the return value is undefined. The correct URL can be obtained only when this API is called inside the called function. You can obtain the URL inside the function and save it. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method.

**Since**: 14

**Returns**:

| Type | Description |
| -- | -- |
| const char* | URL of the last frame that calls JavaScriptProxy. |

### registerJavaScriptProxyEx()

```c
void (*registerJavaScriptProxyEx)(const char* webTag, const ArkWeb_ProxyObjectWithResult* proxyObject,const char* permission)
```

**Description**

Injects a JavaScript object into the window object and calls the synchronous methods of this object in the window object. The synchronous methods of this object can carry return values. This method implements bidirectional data transfer and synchronous calls between JavaScript and native through a synchronous bridging mechanism. Compared with registerJavaScriptProxy, this method adds a permission parameter for configuring JSBridge permission restrictions, and is suitable for scenarios that require permission control or synchronous return values. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Use Cases: for example, business scenarios where synchronous return results are needed when JS calls native.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* webTag | Name of the **Web** component. |
|  const [ArkWeb_ProxyObjectWithResult](capi-web-arkweb-proxyobjectwithresult.md)* proxyObject | Pointer to the proxy object to be registered. The object is injected into the window object, and its synchronous methods can be called through JavaScript with returnable execution results. |
| const char* permission | Pointer to a JSON format string, which defaults to an empty string. This string is used to configure the permission restrictions of JSBridge at the object and method levels. |

### registerAsyncJavaScriptProxyEx()

```c
void (*registerAsyncJavaScriptProxyEx)(const char* webTag, const ArkWeb_ProxyObject* proxyObject,const char* permission)
```

**Description**

Injects a JavaScript object into the window object and calls the asynchronous methods of this object in the window object. This API must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. This method implements asynchronous calls through a message queue mechanism to avoid blocking the main thread. Compared with registerAsyncJavaScriptProxy, this method adds a permission parameter for configuring JSBridge permission restrictions, and is suitable for asynchronous operation scenarios that require permission control.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* webTag | Name of the **Web** component. |
|  const [ArkWeb_ProxyObject](capi-web-arkweb-proxyobject.md)* proxyObject | Object to be registered. |
| const char* permission | JSON format string, which defaults to an empty value. It is used to configure the permission restrictions of JSBridge at the object and method levels. |


