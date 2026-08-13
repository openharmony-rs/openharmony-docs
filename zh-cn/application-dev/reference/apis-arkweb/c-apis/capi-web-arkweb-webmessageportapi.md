# ArkWeb_WebMessagePortAPI

```c
typedef struct ArkWeb_WebMessagePortAPI {...} ArkWeb_WebMessagePortAPI
```

## 概述

ArkWeb_WebMessagePortAPI是Web消息端口相关Native API结构体。该结构体提供了消息端口的创建、关闭、消息发送和消息接收回调注册等功能。此API是postMessage桥接的核心组件，支持在Native代码和Web页面之间建立持久的双向通信通道。适用于需要在原生应用与Web页面之间进行数据交互的场景，解决了跨语言通信的难题，提升了应用的扩展能力和开发效率。<br>Web消息端口相关接口需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取，调用前建议通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#arkweb_member_missing)校验函数指针的可用性，避免SDK与设备ROM不匹配导致崩溃。

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_type.h](capi-arkweb-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t size | 结构体的大小（字节）。 |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [ArkWeb_ErrorCode (\*postMessage)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag, const ArkWeb_WebMessagePtr webMessage)](#postmessage) | Post message to HTML. |
| [void (\*close)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag)](#close) | 关闭消息端口。 |
| [void (\*setMessageEventHandler)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag,ArkWeb_OnMessageEventHandler messageEventHandler, void* userData)](#setmessageeventhandler) | Set a callback to receive message from HTML. |

## 成员函数说明

### postMessage()

```c
ArkWeb_ErrorCode (*postMessage)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag, const ArkWeb_WebMessagePtr webMessage)
```

**描述**

Post message to HTML.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) webMessagePort | The ArkWeb_WebMessagePort. |
|  const char* webTag | The name of the web component. |
|  const [ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md) webMessage | The ArkWeb_WebMessage to send. |

**返回：**

| 类型 | 说明 |
| -- | -- |
| ArkWeb_ErrorCode | Post message result code.<br>             {@link ARKWEB_SUCCESS} post message success.<br>             {@link ARKWEB_INVALID_PARAM} the parameter verification fails.<br>             {@link ARKWEB_INIT_ERROR} no web associated with this webTag. |

### close()

```c
void (*close)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag)
```

**描述**

关闭消息端口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) webMessagePort | Post Message端口结构体指针。 |

### setMessageEventHandler()

```c
void (*setMessageEventHandler)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag,ArkWeb_OnMessageEventHandler messageEventHandler, void* userData)
```

**描述**

Set a callback to receive message from HTML.

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) webMessagePort | The ArkWeb_WebMessagePort. |
|  const char* webTag | The name of the web component. |
| [ArkWeb_OnMessageEventHandler](capi-arkweb-type-h.md#arkweb_onmessageeventhandler) messageEventHandler | The handler to receive message from HTML. |


