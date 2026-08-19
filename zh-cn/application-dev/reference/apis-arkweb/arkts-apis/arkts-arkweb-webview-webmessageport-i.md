# WebMessagePort

WebMessagePort是Web组件中用于应用侧（ArkTS）与HTML5侧（JavaScript）之间双向通信的消息端口接口。通过createWebMessagePorts创建一对关联的端口，将一个端口发送到HTML5侧，另 一个保留在应用侧，实现跨运行时消息传递。WebMessagePort支持两种消息协议：基础协议使用WebMessage作为消息载体（postMessageEvent/onMessageEvent），扩展协议使用 WebMessageExt支持更丰富的数据类型（postMessageEventExt/onMessageEventExt）。

**起始版本：** 9

<!--Device-webview-interface WebMessagePort--><!--Device-webview-interface WebMessagePort-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## close

```TypeScript
close(): void
```

不需要发送消息时关闭该消息端口。在使用close前，请先使用[createWebMessagePorts](arkts-arkweb-webview-webviewcontroller-c.md#createwebmessageports)创建消息端 口。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessagePort-close(): void--><!--Device-WebMessagePort-close(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onMessageEvent

```TypeScript
onMessageEvent(callback: (result: WebMessage) => void): void
```

在应用侧的消息端口上注册回调函数，接收HTML5侧发送过来的[WebMessage](arkts-arkweb-webview-webmessage-t.md)类型消息。完整示例代码参考 [postMessage](arkts-arkweb-webview-webviewcontroller-c.md#postmessage)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessagePort-onMessageEvent(callback: (result: WebMessage) => void): void--><!--Device-WebMessagePort-onMessageEvent(callback: (result: WebMessage) => void): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (result: WebMessage) =&gt; void | 是 | 接收到的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100006](../errorcode-webview.md#17100006-无法注册message-port回调) | Failed to register a message event for the port. |

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100006](../errorcode-webview.md#17100006-无法注册message-port回调) | Failed to register a message event for the port. |

## postMessageEvent

```TypeScript
postMessageEvent(message: WebMessage): void
```

发送[WebMessage](arkts-arkweb-webview-webmessage-t.md)类型消息给HTML5侧，必须先调用 onMessageEvent，否则会发送失败。完整示 例代码参考[postMessage](arkts-arkweb-webview-webviewcontroller-c.md#postmessage)。

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100010](../errorcode-webview.md#17100010-无法使用该端口发送消息) | Failed to post messages through the port. |

## postMessageEventExt

```TypeScript
postMessageEventExt(message: WebMessageExt): void
```

发送[WebMessageType](arkts-arkweb-webview-webmessagetype-e.md)类型消息给HTML5侧，必须先调用 onMessageEventExt，否则 会发送失败。完整示例代码参考 onMessageEventExt。

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
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100010](../errorcode-webview.md#17100010-无法使用该端口发送消息) | Failed to post messages through the port. |

## isExtentionType

```TypeScript
isExtentionType?: boolean
```

创建WebMessagePort时是否指定使用扩展增强接口，[postMessageEventExt](#postmessageeventext)、 onMessageEventExt。 true表示使用扩展增强接口，false表示不使用扩展增强接口。 默认值：false。

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebMessagePort-isExtentionType?: boolean--><!--Device-WebMessagePort-isExtentionType?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

