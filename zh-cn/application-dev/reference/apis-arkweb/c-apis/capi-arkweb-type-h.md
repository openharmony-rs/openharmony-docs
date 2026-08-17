# arkweb_type.h

## 概述

提供ArkWeb在Native侧的公共类型定义。

**库：** libohweb.so

**系统能力：** SystemCapability.Web.Webview.Core

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkWeb_JavaScriptBridgeData](capi-web-arkweb-javascriptbridgedata.md) | ArkWeb_JavaScriptBridgeData | ArkWeb_JavaScriptBridgeData是JavaScript桥接数据定义结构体，用于在Native代码和Web页面之间传递JavaScript桥接相关的数据。该结构体封装了桥接调用中的参数数据，是JavaScript桥接子系统中的基本数据单元，配合ArkWeb_ControllerAPI中的JavaScript Proxy注册接口使用。 |
| [ArkWeb_JavaScriptObject](capi-web-arkweb-javascriptobject.md) | ArkWeb_JavaScriptObject | ArkWeb_JavaScriptObject结构体用于向Web页面注入JavaScript代码并获取执行结果。适用于需要从原生应用主动调用Web页面中的JavaScript函数、读取Web页面状态或调用Web页面API的场景，可简化Web与原生应用间的数据交互流程。开发者可通过该结构体指定待注入的JavaScript脚本内容及长度，注册执行完成回调，并通过userData传递自定义上下文数据，实现Web与原生应用之间的数据交互。 |
| [ArkWeb_ProxyMethod](capi-web-arkweb-proxymethod.md) | ArkWeb_ProxyMethod | ArkWeb_ProxyMethod是用于定义JavaScript代理方法的结构体，支持实现JavaScript与Native代码之间的安全通信，适用于需要从Web页面调用Native能力的场景。该结构体指定了一个可以从JavaScript调用的Native方法的基本信息，包含方法名称和对应的Native回调函数指针和需要携带的自定义数据三个字段。多个ArkWeb_ProxyMethod可以组合成ArkWeb_ProxyObject，以对象的形式整体注入到Web页面中，从而让Web应用能够方便地访问设备原生能力。 |
| [ArkWeb_ProxyMethodWithResult](capi-web-arkweb-proxymethodwithresult.md) | ArkWeb_ProxyMethodWithResult | ArkWeb_ProxyMethodWithResult是带返回值的JavaScript代理方法结构体，扩展了ArkWeb_ProxyMethod的能力，支持在JavaScript调用Native方法后获取返回值。该结构体在方法名称和回调函数的基础上，增加了返回值处理能力，适用于需要向Web前端返回执行结果的调用场景。 |
| [ArkWeb_ProxyObject](capi-web-arkweb-proxyobject.md) | ArkWeb_ProxyObject | ArkWeb_ProxyObject是注入到Web页面的JavaScript代理对象结构体，用于将一组相关的ArkWeb_ProxyMethod方法组织成对象整体暴露给Web前端。该结构体指定了对象在JavaScript中的名称（objName）、方法数组（methodList）和方法数量（size），使得Native应用可以向Web页面暴露结构化的API集合。代理对象通过方法映射机制将Native侧的ArkWeb_ProxyMethod与JavaScript侧的方法调用进行关联，支持方法参数和返回值的自动转换。 |
| [ArkWeb_ProxyObjectWithResult](capi-web-arkweb-proxyobjectwithresult.md) | ArkWeb_ProxyObjectWithResult | ArkWeb_ProxyObjectWithResult是带返回值的JavaScript代理对象结构体，扩展了ArkWeb_ProxyObject的能力。该结构体将多个ArkWeb_ProxyMethodWithResult组织成对象注入到Web页面中，支持JavaScript调用Native方法后获取返回值。解决了ArkWeb_ProxyObject无法返回执行结果的问题，简化了开发流程，提升了开发效率。适用于需要向Web前端返回结构化执行结果的API场景。 |
| [ArkWeb_ControllerAPI](capi-web-arkweb-controllerapi.md) | ArkWeb_ControllerAPI | ArkWeb_ControllerAPI是Controller相关Native API结构体。该结构体提供了JavaScript注入、同步和异步JavaScript代理注册、代理删除、页面刷新、Web MessagePort创建和管理、Frame URL查询等功能，特点包括支持同步与异步代理并存、统一管理控制WebView行为。适用于需要从Native代码注入并调用JavaScript、实现Native与页面双向通信的场景，可解决JSBridge互通与安全注入问题，提升开发效率与可控性。这是从Native代码控制WebView行为的主要接口。<br>Controller相关接口需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取，调用前建议通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#arkweb_member_missing)校验函数指针的可用性，避免SDK与设备ROM不匹配导致崩溃。 |
| [ArkWeb_ComponentAPI](capi-web-arkweb-componentapi.md) | ArkWeb_ComponentAPI | ArkWeb_ComponentAPI是ArkWeb在Native侧提供的用于监听Web组件生命周期事件的API结构体，继承自基础Native API类型{@link ArkWeb_AnyNativeAPI}。开发者通过{@link OH_ArkWeb_GetNativeAPI}并指定`ARKWEB_NATIVE_COMPONENT`类型获取该结构体，进而注册Web组件的Controller绑定、页面开始加载、页面加载完成以及组件销毁等事件回调。该结构体适用于需要在Native代码（C/C++）中感知Web组件关键状态变化的场景，例如初始化Native资源、同步页面加载状态、统计埋点或在组件销毁时释放关联资源；相关接口需在UI线程中调用，并建议在调用具体成员函数前通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#arkweb_member_missing)宏校验函数指针是否存在。 |
| [ArkWeb_WebMessagePortAPI](capi-web-arkweb-webmessageportapi.md) | ArkWeb_WebMessagePortAPI | ArkWeb_WebMessagePortAPI是Web消息端口相关Native API结构体。该结构体提供了消息端口的创建、关闭、消息发送和消息接收回调注册等功能。此API是postMessage桥接的核心组件，支持在Native代码和Web页面之间建立持久的双向通信通道。适用于需要在原生应用与Web页面之间进行数据交互的场景，解决了跨语言通信的难题，提升了应用的扩展能力和开发效率。<br>Web消息端口相关接口需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取，调用前建议通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#arkweb_member_missing)校验函数指针的可用性，避免SDK与设备ROM不匹配导致崩溃。 |
| [ArkWeb_WebMessageAPI](capi-web-arkweb-webmessageapi.md) | ArkWeb_WebMessageAPI | ArkWeb_WebMessageAPI是Web消息相关Native API结构体。该结构体提供了创建和销毁消息、设置和获取消息类型、管理消息数据缓冲区等函数。此API是postMessage桥接的一部分，支持Native代码与HTML页面之间的双向通信。<br>Web消息相关接口需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取，调用前建议通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#arkweb_member_missing)校验函数指针的可用性，避免SDK与设备ROM不匹配导致崩溃。 |
| [ArkWeb_CookieManagerAPI](capi-web-arkweb-cookiemanagerapi.md) | ArkWeb_CookieManagerAPI | ArkWeb_CookieManagerAPI是Cookie管理相关Native API结构体。该结构体提供了Cookie的读取、设置、清除和同步等操作能力，适用于需要在WebView组件中管理用户会话、跟踪用户首选项等场景，能够帮助开发者便捷地实现数据持久化和状态同步。<br>CookieManager相关接口需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取，调用前建议通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#arkweb_member_missing)校验函数指针的可用性，避免SDK与设备ROM不匹配导致崩溃。 |
| [ArkWeb_JavaScriptValueAPI](capi-web-arkweb-javascriptvalueapi.md) | ArkWeb_JavaScriptValueAPI | ArkWeb_JavaScriptValueAPI是JavaScript相关Native API结构体。该结构体提供了创建JavaScript值的函数，支持将Native数据转换为JavaScript可识别的格式并返回给HTML。该转换机制根据指定的JavaScript值类型对Native数据缓冲区进行解析和封装，生成对应的JavaScript值对象。适用于需要从Native层向Web层传递数据的应用场景，能够实现Native与Web之间的双向数据交互，提升应用开发灵活性。<br>在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取JavaScript相关接口。调用前建议通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#arkweb_member_missing)校验函数指针的可用性，避免SDK与设备ROM不匹配导致崩溃。 |
| [ArkWeb_WebMessage*](capi-web-arkweb-webmessage8h.md) | ArkWeb_WebMessagePtr | ArkWeb_WebMessage是用于跨上下文消息通信的Web消息结构体，定义了消息的基本格式和数据承载能力。该结构体是Web消息通信的基础数据单元，支持在Native代码和Web页面之间传递字符串和二进制数据。 |
| [ArkWeb_JavaScriptValue*](capi-web-arkweb-javascriptvalue8h.md) | ArkWeb_JavaScriptValuePtr | ArkWeb_JavaScriptValue是用于在Native代码中封装JavaScript值的结构体，提供了JavaScript值的基本创建和操作能力。该结构体支持将Native数据转换为JavaScript可识别的格式，解决Native与JavaScript双向数据传递的类型安全与格式兼容问题，是JavaScript桥接通信中的数据传递基础类型，有助于减少手动转换成本、提升桥接通信效率并增强可维护性。 |
| [ArkWeb_WebMessagePort*](capi-web-arkweb-webmessageport8h.md) | ArkWeb_WebMessagePortPtr | ArkWeb_WebMessagePort是Web消息端口结构体，表示MessageChannel的两个端口之一，用于发送和接收消息。该结构体支持在Native代码和Web页面之间进行双向消息通信。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkWeb_WebMessageType](#arkweb_webmessagetype) | ArkWeb_WebMessageType | Post Message数据类型。 |
| [ArkWeb_JavaScriptValueType](#arkweb_javascriptvaluetype) | ArkWeb_JavaScriptValueType | JavaScript数据类型。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*ArkWeb_OnJavaScriptCallback)(const char* webTag, const ArkWeb_JavaScriptBridgeData* data, void* userData)](#arkweb_onjavascriptcallback) | ArkWeb_OnJavaScriptCallback | 注入的JavaScript执行完成的回调。用于获取JavaScript代码在Web组件中的执行结果，例如在需要根据JavaScript返回的数据更新原生UI或执行后续逻辑的场景中使用。 |
| [typedef void (\*ArkWeb_OnJavaScriptProxyCallback)(const char* webTag, const ArkWeb_JavaScriptBridgeData* dataArray, size_t arraySize, void* userData)](#arkweb_onjavascriptproxycallback) | ArkWeb_OnJavaScriptProxyCallback | Proxy方法被执行的回调。Proxy方法用于Native侧与JavaScript侧的对象交互和自定义操作。 |
| [typedef ArkWeb_JavaScriptValuePtr (\*ArkWeb_OnJavaScriptProxyCallbackWithResult)(const char* webTag, const ArkWeb_JavaScriptBridgeData* dataArray, size_t arraySize, void* userData)](#arkweb_onjavascriptproxycallbackwithresult) | ArkWeb_OnJavaScriptProxyCallbackWithResult | Proxy方法被执行的回调（有返回值）。用于在JavaScript调用注入的Proxy方法时接收通知并返回执行结果，适用于实现JavaScript与原生代码的桥接通信场景，例如拦截JavaScript调用、执行原生逻辑、计算结果并将结果返回给JavaScript。 |
| [typedef void (\*ArkWeb_OnComponentCallback)(const char* webTag, void* userData)](#arkweb_oncomponentcallback) | ArkWeb_OnComponentCallback | 接收Web组件事件通知的回调。用于接收Web组件生命周期事件通知，例如页面加载完成、页面销毁、组件可见性变化等场景下的状态变更通知。 |
| [typedef void (\*ArkWeb_OnScrollCallback)(const char* webTag, void* userData, double x, double y)](#arkweb_onscrollcallback) | ArkWeb_OnScrollCallback | Web组件滚动时的回调函数。 |
| [typedef void (\*ArkWeb_OnMessageEventHandler)(const char* webTag, const ArkWeb_WebMessagePortPtr port, const ArkWeb_WebMessagePtr message, void* userData)](#arkweb_onmessageeventhandler) | ArkWeb_OnMessageEventHandler | 处理HTML发送过来的Post Message数据。 |
| [ARKWEB_MEMBER_EXISTS(s, f) \((intptr_t) & ((s)->f) - (intptr_t)(s) + sizeof((s)->f) <= *(size_t *)(s))](#arkweb_member_exists) | - | 检查结构体中是否存在该成员变量。 |
| [ARKWEB_MEMBER_MISSING(s, f)(!ARKWEB_MEMBER_EXISTS(s, f) \|\| !((s)->f))](#arkweb_member_missing) | - | 当前结构体存在该成员变量则返回false，否则返回true。 |

## 枚举类型说明

### ArkWeb_WebMessageType

```c
enum ArkWeb_WebMessageType
```

**描述**

Post Message数据类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKWEB_NONE = 0 | 错误数据。 |
| ARKWEB_STRING | 字符串数据类型。 |
| ARKWEB_BUFFER | 字节流数据类型。 |

### ArkWeb_JavaScriptValueType

```c
enum ArkWeb_JavaScriptValueType
```

**描述**

JavaScript数据类型。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKWEB_JAVASCRIPT_NONE = 0 | 错误数据。 |
| ARKWEB_JAVASCRIPT_STRING | 字符串数据类型。 |
| ARKWEB_JAVASCRIPT_BOOL | boolean数据类型。 |


## 函数说明

### ArkWeb_OnJavaScriptCallback()

```c
typedef void (*ArkWeb_OnJavaScriptCallback)(const char* webTag, const ArkWeb_JavaScriptBridgeData* data, void* userData)
```

**描述**

注入的JavaScript执行完成的回调。用于获取JavaScript代码在Web组件中的执行结果，例如在需要根据JavaScript返回的数据更新原生UI或执行后续逻辑的场景中使用。

**起始版本：** 12

### ArkWeb_OnJavaScriptProxyCallback()

```c
typedef void (*ArkWeb_OnJavaScriptProxyCallback)(const char* webTag, const ArkWeb_JavaScriptBridgeData* dataArray, size_t arraySize, void* userData)
```

**描述**

Proxy方法被执行的回调。Proxy方法用于Native侧与JavaScript侧的对象交互和自定义操作。

**起始版本：** 12

### ArkWeb_OnJavaScriptProxyCallbackWithResult()

```c
typedef ArkWeb_JavaScriptValuePtr (*ArkWeb_OnJavaScriptProxyCallbackWithResult)(const char* webTag, const ArkWeb_JavaScriptBridgeData* dataArray, size_t arraySize, void* userData)
```

**描述**

Proxy方法被执行的回调（有返回值）。用于在JavaScript调用注入的Proxy方法时接收通知并返回执行结果，适用于实现JavaScript与原生代码的桥接通信场景，例如拦截JavaScript调用、执行原生逻辑、计算结果并将结果返回给JavaScript。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (const char\* webTag | Web组件名称。 |
| [const ArkWeb_JavaScriptBridgeData](capi-web-arkweb-javascriptbridgedata.md)\* dataArray | 数组数据。 |
| size_t arraySize | 数组大小。 |
| void\* userData | 用户自定义的数据。 |

### ArkWeb_OnComponentCallback()

```c
typedef void (*ArkWeb_OnComponentCallback)(const char* webTag, void* userData)
```

**描述**

接收Web组件事件通知的回调。用于接收Web组件生命周期事件通知，例如页面加载完成、页面销毁、组件可见性变化等场景下的状态变更通知。

**起始版本：** 12

### ArkWeb_OnScrollCallback()

```c
typedef void (*ArkWeb_OnScrollCallback)(const char* webTag, void* userData, double x, double y)
```

**描述**

Web组件滚动时的回调函数。

**起始版本：** 18

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (const char\* webTag | Web组件名称。 |
| void\* userData | 用户自定义的数据。 |
| double x | X轴滚动偏移。单位：vp。 |
| double y | Y轴滚动偏移。单位：vp。 |

### ArkWeb_OnMessageEventHandler()

```c
typedef void (*ArkWeb_OnMessageEventHandler)(const char* webTag, const ArkWeb_WebMessagePortPtr port, const ArkWeb_WebMessagePtr message, void* userData)
```

**描述**

处理HTML发送过来的Post Message数据。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| (const char\* webTag | Web组件名称。 |
| [const ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) port | Post Message端口。 |
| [const ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md) message | Post Message数据。 |
| void\* userData | 用户自定义的数据。 |

### ARKWEB_MEMBER_EXISTS()

```c
ARKWEB_MEMBER_EXISTS(s, f) \((intptr_t) & ((s)->f) - (intptr_t)(s) + sizeof((s)->f) <= *(size_t *)(s))
```

**描述**

检查结构体中是否存在该成员变量。

**起始版本：** 12

### ARKWEB_MEMBER_MISSING()

```c
ARKWEB_MEMBER_MISSING(s, f)(!ARKWEB_MEMBER_EXISTS(s, f) || !((s)->f))
```

**描述**

当前结构体存在该成员变量则返回false，否则返回true。

**起始版本：** 12


