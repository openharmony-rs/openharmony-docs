# WebMessagePort

Define html web message port.

**起始版本：** 9

<!--Device-webview-interface WebMessagePort--><!--Device-webview-interface WebMessagePort-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

<a id="close"></a>
## close

```TypeScript
close(): void
```

不需要发送消息时关闭该消息端口。在使用close前，请先使用createWebMessagePorts创建消息端口。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessagePort-close(): void--><!--Device-WebMessagePort-close(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="onmessageevent"></a>
## onMessageEvent

```TypeScript
onMessageEvent(callback: (result: WebMessage) => void): void
```

在应用侧的消息端口上注册回调函数，接收HTML5侧发送过来的WebMessage类型消息。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessagePort-onMessageEvent(callback: (result: WebMessage) => void): void--><!--Device-WebMessagePort-onMessageEvent(callback: (result: WebMessage) => void): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (result: WebMessage) =&gt; void | 是 | 用于接收消息的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100006](../errorcode-webview.md#17100006-无法注册message-port回调) | Failed to register a message event for the port. |

<a id="onmessageeventext"></a>
## onMessageEventExt

```TypeScript
onMessageEventExt(callback: (result: WebMessageExt) => void): void
```

在应用侧的消息端口上注册回调函数，接收HTML5侧发送过来的[WebMessageType](arkts-arkweb-webview-webmessagetype-e.md)类型消息。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessagePort-onMessageEventExt(callback: (result: WebMessageExt) => void): void--><!--Device-WebMessagePort-onMessageEventExt(callback: (result: WebMessageExt) => void): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (result: WebMessageExt) =&gt; void | 是 | 接收到的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100006](../errorcode-webview.md#17100006-无法注册message-port回调) | Failed to register a message event for the port. |

<a id="postmessageevent"></a>
## postMessageEvent

```TypeScript
postMessageEvent(message: WebMessage): void
```

发送WebMessage类型消息给HTML5侧，必须先调用onMessageEvent，否则会发送失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessagePort-postMessageEvent(message: WebMessage): void--><!--Device-WebMessagePort-postMessageEvent(message: WebMessage): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | [WebMessage](arkts-arkweb-webview-webmessage-t.md) | 是 | 要发送的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100010](../errorcode-webview.md#17100010-无法使用该端口发送消息) | Failed to post messages through the port. |

<a id="postmessageeventext"></a>
## postMessageEventExt

```TypeScript
postMessageEventExt(message: WebMessageExt): void
```

发送WebMessageType类型消息给HTML5侧，必须先调用onMessageEventExt，否则会发送失败。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessagePort-postMessageEventExt(message: WebMessageExt): void--><!--Device-WebMessagePort-postMessageEventExt(message: WebMessageExt): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | [WebMessageExt](arkts-arkweb-webview-webmessageext-c.md) | 是 | 要发送的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100010](../errorcode-webview.md#17100010-无法使用该端口发送消息) | Failed to post messages through the port. |

## isExtentionType

```TypeScript
isExtentionType?: boolean
```

创建WebMessagePort时是否指定使用扩展增强接口（如 postMessageEventExt 和 onMessageEventExt）。

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessagePort-isExtentionType?: boolean--><!--Device-WebMessagePort-isExtentionType?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

