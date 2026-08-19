# WebMessagePort

Define html web message port.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-interface WebMessagePort--><!--Device-webview-interface WebMessagePort-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## close

```TypeScript
close(): void
```

Close port.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebMessagePort-close(): void--><!--Device-WebMessagePort-close(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onMessageEvent

```TypeScript
onMessageEvent(callback: (result: WebMessage) => void): void
```

Receive message from other port.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebMessagePort-onMessageEvent(callback: (result: WebMessage) => void): void--><!--Device-WebMessagePort-onMessageEvent(callback: (result: WebMessage) => void): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (result: WebMessage) =&gt; void | 是 | Callback function for receiving messages. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100006](../../apis-arkweb/errorcode-webview.md#17100006-无法注册message-port回调) | Failed to register a message event for the port. |

## onMessageEventExt

```TypeScript
onMessageEventExt(callback: (result: WebMessageExt) => void): void
```

Receive message from other port.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebMessagePort-onMessageEventExt(callback: (result: WebMessageExt) => void): void--><!--Device-WebMessagePort-onMessageEventExt(callback: (result: WebMessageExt) => void): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (result: WebMessageExt) =&gt; void | 是 | Callback function for receiving messages. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100006](../../apis-arkweb/errorcode-webview.md#17100006-无法注册message-port回调) | Failed to register a message event for the port. |

## postMessageEvent

```TypeScript
postMessageEvent(message: WebMessage): void
```

Post a message to other port.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebMessagePort-postMessageEvent(message: WebMessage): void--><!--Device-WebMessagePort-postMessageEvent(message: WebMessage): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | [WebMessage](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webmessage-t.md) | 是 | Message to send. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100010](../../apis-arkweb/errorcode-webview.md#17100010-无法使用该端口发送消息) | Failed to post messages through the port. |

## postMessageEventExt

```TypeScript
postMessageEventExt(message: WebMessageExt): void
```

Post a message to other port.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebMessagePort-postMessageEventExt(message: WebMessageExt): void--><!--Device-WebMessagePort-postMessageEventExt(message: WebMessageExt): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | [WebMessageExt](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webmessageext-c.md) | 是 | Message to send. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100010](../../apis-arkweb/errorcode-webview.md#17100010-无法使用该端口发送消息) | Failed to post messages through the port. |

## isExtentionType

```TypeScript
isExtentionType?: boolean
```

The flag indicates whether more formats are supported than string and array buffers.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-WebMessagePort-isExtentionType?: boolean--><!--Device-WebMessagePort-isExtentionType?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

