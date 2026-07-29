# ArkWeb_WebMessagePortAPI
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

```c
typedef struct {...} ArkWeb_WebMessagePortAPI
```

## 概述

ArkWeb_WebMessagePortAPI是Web消息端口相关Native API结构体。该结构体提供了消息端口的创建、关闭、消息发送和消息接收回调注册等功能。此API是postMessage桥接的核心组件，支持在Native代码和Web页面之间建立持久的双向通信通道。

Web消息端口相关接口需在UI线程中调用OH_ArkWeb_GetNativeAPI方法获取，调用前建议通过[ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#宏定义)校验函数指针的可用性，避免SDK与设备ROM不匹配导致崩溃。

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_type.h](capi-arkweb-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| size_t size | 结构体的大小。 |


### 成员函数

| 名称                                                                                                                                                                                              | 描述         |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| [ArkWeb_ErrorCode (\*postMessage)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag, const ArkWeb_WebMessagePtr webMessage)](#postmessage)                                      | 发送消息到HTML。 |
| [void (\*close)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag)](#close)                                                                                                     | 关闭消息端口。    |
| [void (\*setMessageEventHandler)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag, ArkWeb_OnMessageEventHandler messageEventHandler, void* userData)](#setmessageeventhandler) | 设置接收HTML消息的回调。           |

## 成员函数说明

### postMessage()

```c
ArkWeb_ErrorCode (*postMessage)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag, const ArkWeb_WebMessagePtr webMessage)
```

**描述：**

发送消息到HTML。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) webMessagePort | Post Message端口结构体指针。 |
| const char* webTag | Web组件名称。 |
| const [ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md) webMessage | 需要发送的消息。 |

**返回：**

| 类型                                                               | 说明                                                                                   |
|------------------------------------------------------------------|--------------------------------------------------------------------------------------|
| [ArkWeb_ErrorCode](capi-arkweb-error-code-h.md#arkweb_errorcode) | [ARKWEB_SUCCESS](capi-arkweb-error-code-h.md#arkweb_errorcode) 执行成功。<br>[ARKWEB_INVALID_PARAM](capi-arkweb-error-code-h.md#arkweb_errorcode) 参数无效。<br>[ARKWEB_INIT_ERROR](capi-arkweb-error-code-h.md#arkweb_errorcode) 初始化失败，没有找到与webTag绑定的Web组件。 |

### close()

```c
void (*close)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag)
```

**描述：**

关闭消息端口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) webMessagePort | Post Message端口结构体指针。 |
| const char* webTag                                                                   |  Web组件名称。              |

### setMessageEventHandler()

```c
void (*setMessageEventHandler)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag,
        ArkWeb_OnMessageEventHandler messageEventHandler, void* userData)
```

**描述：**

设置接收HTML消息的回调。

**参数：**

| 参数项                                                                                                    | 描述                   |
|--------------------------------------------------------------------------------------------------------|----------------------|
| const [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) webMessagePort                       | Post Message端口结构体指针。 |
| const char* webTag                                                                                     |  Web组件名称。                     |
| [ArkWeb_OnMessageEventHandler](capi-arkweb-type-h.md#arkweb_onmessageeventhandler) messageEventHandler | 处理消息的回调。                     |
| void* userData                                                                                         | 用户自定义数据。                     |

