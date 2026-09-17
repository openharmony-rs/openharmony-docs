# WebMessagePort

WebMessagePort is a message port interface in the Web component used for bidirectional communication between the app side (ArkTS) and the HTML5 side (JavaScript). A pair of associated ports is created through createWebMessagePorts, with one port sent to the HTML5 side and the other retained on the app side, enabling cross- runtime message passing. WebMessagePort supports two message protocols: the basic protocol uses WebMessage as the message carrier (postMessageEvent/onMessageEvent), and the extended protocol uses WebMessageExt to support richer data types (postMessageEventExt/onMessageEventExt).

@interface WebMessagePort [since 9 - 11]

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## close

```TypeScript
close(): void
```

Closes this message port when messages do not need to be sent. Before calling this method, call [createWebMessagePorts](arkts-arkweb-webview-webviewcontroller-c.md#createwebmessageports) to create a message port.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## onMessageEvent

```TypeScript
onMessageEvent(callback: (result: WebMessage) => void): void
```

Registers a callback on the application message port to receive messages of the [WebMessage](arkts-arkweb-webview-webmessage-t.md) type from the HTML5 side. For details about the sample code, see [postMessage](arkts-arkweb-webview-webviewcontroller-c.md#postmessage).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (result: WebMessage) =&gt; void | Yes | Message received. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100006](../errorcode-webview.md#17100006-message-port-callback-cannot-be-registered) | Failed to register a message event for the port. |

## onMessageEventExt

```TypeScript
onMessageEventExt(callback: (result: WebMessageExt) => void): void
```

Registers a callback on the application message port to receive messages of the [WebMessageType](arkts-arkweb-webview-webmessagetype-e.md) type from the HTML5 side.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (result: WebMessageExt) =&gt; void | Yes | Message received. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100006](../errorcode-webview.md#17100006-message-port-callback-cannot-be-registered) | Failed to register a message event for the port. |

## postMessageEvent

```TypeScript
postMessageEvent(message: WebMessage): void
```

Sends a message of the [WebMessage](arkts-arkweb-webview-webmessage-t.md) type to the HTML5 side. The [onMessageEvent](#onmessageevent) API must be invoked first. Otherwise, the message fails to be sent. For details about the sample code, see [postMessage](arkts-arkweb-webview-webviewcontroller-c.md#postmessage).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | [WebMessage](arkts-arkweb-webview-webmessage-t.md) | Yes | Message to send. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100010](../errorcode-webview.md#17100010-failure-to-send-messages-through-a-port) | Failed to post messages through the port. |

## postMessageEventExt

```TypeScript
postMessageEventExt(message: WebMessageExt): void
```

Sends a message of the [WebMessageType](arkts-arkweb-webview-webmessagetype-e.md) type to the HTML5 side. You must call [onMessageEventExt](#onmessageeventext) first. Otherwise, the message fails to be sent. For the complete sample code, see [onMessageEventExt](#onmessageeventext).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | [WebMessageExt](arkts-arkweb-webview-webmessageext-c.md) | Yes | Message to send. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100010](../errorcode-webview.md#17100010-failure-to-send-messages-through-a-port) | Failed to post messages through the port. |

## isExtentionType

```TypeScript
isExtentionType?: boolean
```

Whether to use the extended interface such as postMessageEventExt and onMessageEventExt when creating a WebMessagePort.

The value true means to use the extended interface, and false means the opposite.

Default value: false.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
