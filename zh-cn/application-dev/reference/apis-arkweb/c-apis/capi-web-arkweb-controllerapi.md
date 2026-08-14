# ArkWeb_ControllerAPI

```c
typedef struct ArkWeb_ControllerAPI {...} ArkWeb_ControllerAPI
```

## 概述

ArkWeb_ControllerAPI是Controller相关Native API结构体。该结构体提供了JavaScript注入、同步和异步JavaScript代理注册、代理删除、页面刷新、Web MessagePort创建和管理、Frame URL查询等功能，特点包括支持同步与异步代理并存、统一管理控制WebView行为。适用于需要从Native代码注入并调用JavaScript、实现Native与页面双向通信的场景，可解决JSBridge互通与安全注入问题，提升开发效率与可控性。这是从Native代码控制WebView行为的主要接口。<br>Controller相关接口需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取，调用前建议通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#arkweb_member_missing)校验函数指针的可用性，避免SDK与设备ROM不匹配导致崩溃。

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_type.h](capi-arkweb-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t size | 结构体的大小。 |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [void (\*runJavaScript)(const char* webTag, const ArkWeb_JavaScriptObject* javascriptObject)](#runjavascript) | 注入JavaScript脚本。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。该方法将JavaScript脚本注入到Web组件的执行上下文中，在页面加载完成后执行。 |
| [void (\*registerJavaScriptProxy)(const char* webTag, const ArkWeb_ProxyObject* proxyObject)](#registerjavascriptproxy) | 注入JavaScript对象到window对象中，并在window对象中调用该对象的同步方法。该方法通过桥接机制将Native对象映射到JavaScript环境，实现双向通信。使用场景：例如JS调用Native能力以获取设备信息、执行 Native 业务逻辑等。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。与registerAsyncJavaScriptProxy相比，此方法适用于需要同步获取返回值的场景。若不需要同步返回值或耗时操作，建议使用registerAsyncJavaScriptProxy以避免阻塞UI线程。 |
| [void (\*deleteJavaScriptRegister)(const char* webTag, const char* objName)](#deletejavascriptregister) | 删除通过registerJavaScriptProxy注册到window上的指定name的应用侧JavaScript对象。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。该方法会解除JavaScript对象与Native对象的绑定，并释放相关资源。使用场景：例如组件销毁、模块卸载或切换业务时清理注册对象以避免残留。 |
| [void (\*refresh)(const char* webTag)](#refresh) | 刷新当前网页。刷新的同时会清理页面栈，导致当前页面无法前进后退。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。 |
| [void (\*registerAsyncJavaScriptProxy)(const char* webTag, const ArkWeb_ProxyObject* proxyObject)](#registerasyncjavascriptproxy) | 注入JavaScript对象到window对象中，并在window对象中调用该对象的异步方法。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。该方法通过消息队列机制实现异步调用，避免阻塞主线程。与registerJavaScriptProxy相比，此方法适用于耗时操作或不需要同步获取返回值的场景，若需要同步获取返回值，建议使用registerJavaScriptProxy。 |
| [ArkWeb_WebMessagePortPtr* (\*createWebMessagePorts)(const char* webTag, size_t* size)](#createwebmessageports) | 创建Post Message端口。Post Message端口提供双向通信机制，允许Native层与Web层安全地交换数据消息。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。使用场景：例如实现跨上下文消息通道，支持iframe与主页面、Web与Worker之间的数据传递。 |
| [void (\*destroyWebMessagePorts)(ArkWeb_WebMessagePortPtr** ports, size_t size)](#destroywebmessageports) | 销毁端口。该方法会关闭端口连接，释放相关系统资源，停止消息传输。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。使用场景：例如通信结束、组件生命周期结束时释放端口资源以避免泄漏。 |
| [ArkWeb_ErrorCode (\*postWebMessage)(const char* webTag, const char* name, ArkWeb_WebMessagePortPtr* webMessagePorts, size_t size, const char* url)](#postwebmessage) | Post message ports to main frame. |
| [const char* (\*getLastJavascriptProxyCallingFrameUrl)()](#getlastjavascriptproxycallingframeurl) | 获取调用JavaScriptProxy最后一帧的url。该方法通过帧栈追踪机制，记录最后一次JavaScript调用的frame上下文。在JavaScriptProxy调用的线程上调用。通过registerJavaScriptProxy或者JavaScriptProxy注入JavaScript对象到window对象中。该接口可以获取最后一次调用注入对象frame的url，如果从未调用过注入对象，返回值未定义。在被调用函数内部获取url才能获取到正确值，可以在函数内部获取url后保存下来。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。 |
| [void (\*registerJavaScriptProxyEx)(const char* webTag, const ArkWeb_ProxyObjectWithResult* proxyObject,const char* permission)](#registerjavascriptproxyex) | Register the JavaScript object and method list, the method is callback function that has a return value. |
| [void (\*registerAsyncJavaScriptProxyEx)(const char* webTag, const ArkWeb_ProxyObject* proxyObject,const char* permission)](#registerasyncjavascriptproxyex) | Register the JavaScript object and async method list. |

## 成员函数说明

### runJavaScript()

```c
void (*runJavaScript)(const char* webTag, const ArkWeb_JavaScriptObject* javascriptObject)
```

**描述**

注入JavaScript脚本。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。该方法将JavaScript脚本注入到Web组件的执行上下文中，在页面加载完成后执行。

### registerJavaScriptProxy()

```c
void (*registerJavaScriptProxy)(const char* webTag, const ArkWeb_ProxyObject* proxyObject)
```

**描述**

注入JavaScript对象到window对象中，并在window对象中调用该对象的同步方法。该方法通过桥接机制将Native对象映射到JavaScript环境，实现双向通信。使用场景：例如JS调用Native能力以获取设备信息、执行 Native 业务逻辑等。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。与registerAsyncJavaScriptProxy相比，此方法适用于需要同步获取返回值的场景。若不需要同步返回值或耗时操作，建议使用registerAsyncJavaScriptProxy以避免阻塞UI线程。

### deleteJavaScriptRegister()

```c
void (*deleteJavaScriptRegister)(const char* webTag, const char* objName)
```

**描述**

删除通过registerJavaScriptProxy注册到window上的指定name的应用侧JavaScript对象。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。该方法会解除JavaScript对象与Native对象的绑定，并释放相关资源。使用场景：例如组件销毁、模块卸载或切换业务时清理注册对象以避免残留。

### refresh()

```c
void (*refresh)(const char* webTag)
```

**描述**

刷新当前网页。刷新的同时会清理页面栈，导致当前页面无法前进后退。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。

### registerAsyncJavaScriptProxy()

```c
void (*registerAsyncJavaScriptProxy)(const char* webTag, const ArkWeb_ProxyObject* proxyObject)
```

**描述**

注入JavaScript对象到window对象中，并在window对象中调用该对象的异步方法。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。该方法通过消息队列机制实现异步调用，避免阻塞主线程。与registerJavaScriptProxy相比，此方法适用于耗时操作或不需要同步获取返回值的场景，若需要同步获取返回值，建议使用registerJavaScriptProxy。

### createWebMessagePorts()

```c
ArkWeb_WebMessagePortPtr* (*createWebMessagePorts)(const char* webTag, size_t* size)
```

**描述**

创建Post Message端口。Post Message端口提供双向通信机制，允许Native层与Web层安全地交换数据消息。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。使用场景：例如实现跨上下文消息通道，支持iframe与主页面、Web与Worker之间的数据传递。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | Web组件名称。 |

### destroyWebMessagePorts()

```c
void (*destroyWebMessagePorts)(ArkWeb_WebMessagePortPtr** ports, size_t size)
```

**描述**

销毁端口。该方法会关闭端口连接，释放相关系统资源，停止消息传输。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。使用场景：例如通信结束、组件生命周期结束时释放端口资源以避免泄漏。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md)** ports | Post Message端口结构体指针数组。 |

### postWebMessage()

```c
ArkWeb_ErrorCode (*postWebMessage)(const char* webTag, const char* name, ArkWeb_WebMessagePortPtr* webMessagePorts, size_t size, const char* url)
```

**描述**

Post message ports to main frame.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |
|  const char* name | Name of the message to be sent. |
|  size_t size | The quantity of message ports. |
|  const char* url | Indicates the URI for receiving the message. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkWeb_ErrorCode | Post web message result code.<br>             {@link ARKWEB_SUCCESS} post web message success.<br>             {@link ARKWEB_INVALID_PARAM} the parameter verification fails.<br>             {@link ARKWEB_INIT_ERROR} no web associated with this webTag. |

### getLastJavascriptProxyCallingFrameUrl()

```c
const char* (*getLastJavascriptProxyCallingFrameUrl)()
```

**描述**

获取调用JavaScriptProxy最后一帧的url。该方法通过帧栈追踪机制，记录最后一次JavaScript调用的frame上下文。在JavaScriptProxy调用的线程上调用。通过registerJavaScriptProxy或者JavaScriptProxy注入JavaScript对象到window对象中。该接口可以获取最后一次调用注入对象frame的url，如果从未调用过注入对象，返回值未定义。在被调用函数内部获取url才能获取到正确值，可以在函数内部获取url后保存下来。需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取该接口。

**起始版本：** 14

**返回：**

| 类型 | 说明 |
| -- | -- |
| const char* | 调用JavaScriptProxy最后一帧的url。 |

### registerJavaScriptProxyEx()

```c
void (*registerJavaScriptProxyEx)(const char* webTag, const ArkWeb_ProxyObjectWithResult* proxyObject,const char* permission)
```

**描述**

Register the JavaScript object and method list, the method is callback function that has a return value.

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |
|  const [ArkWeb_ProxyObjectWithResult](capi-web-arkweb-proxyobjectwithresult.md)* proxyObject | The JavaScript object to register, the object has callback functions with return value. |
| const char* permission | The JSON string, which defaults to null, is used to configure the permission control forJSBridge, allowing for the definition of URL whitelists at the object and method levels. |

### registerAsyncJavaScriptProxyEx()

```c
void (*registerAsyncJavaScriptProxyEx)(const char* webTag, const ArkWeb_ProxyObject* proxyObject,const char* permission)
```

**描述**

Register the JavaScript object and async method list.

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char* webTag | The name of the web component. |
|  const [ArkWeb_ProxyObject](capi-web-arkweb-proxyobject.md)* proxyObject | The JavaScript object to register. |
| const char* permission | The JSON string, which defaults to null, is used to configure the permission controlfor JSBridge, allowing for the definition of URL whitelists at the object and method levels. |


