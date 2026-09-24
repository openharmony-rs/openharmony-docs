# AtomicServiceWebController

```TypeScript
export declare class AtomicServiceWebController
```

Implements an **AtomicServiceWebController** object for controlling the behavior of the **AtomicServiceWeb** component. An **AtomicServiceWebController** can control only one **AtomicServiceWeb** component, and the APIs on the **AtomicServiceWebController** can be called only after it has been bound to the target **AtomicServiceWeb** component.

**Since:** 12

**Decorator:** @Observed

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## accessBackward

```TypeScript
accessBackward(): boolean
```

Checks whether going to the previous page can be performed on this page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if going to the previous page can be performed on the current page; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

## accessForward

```TypeScript
accessForward(): boolean
```

Checks whether going to the next page can be performed on this page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if going to the next page can be performed on the current page; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

## accessStep

```TypeScript
accessStep(step: number): boolean
```

Checks whether this page can navigate forward or backward by the specified number of steps.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| step | number | Yes | Number of the steps to take. A positive number means to go forward, and a negative number means to go backward. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the page can navigate forward or backward by the specified number of steps. Returns **true** if navigation can be performed on the current page; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

## backward

```TypeScript
backward(): void
```

Moves to the previous page based on the history stack. This API is generally used together with [accessBackward](#accessbackward).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

## forward

```TypeScript
forward(): void
```

Moves to the next page based on the history stack. This API is generally used together with [accessForward](#accessforward).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

## getCustomUserAgent

```TypeScript
getCustomUserAgent(): string
```

Obtains a custom user agent.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Information about the custom user agent. For details about the specifications and usage scenarios, see [Developing User-Agent](../../../web/web-default-userAgent.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

## getUserAgent

```TypeScript
getUserAgent(): string
```

Obtains the default user agent of this web page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Default user agent. For details about the specifications and usage scenarios, see [Developing User-Agent](../../../web/web-default-userAgent.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

## loadUrl

```TypeScript
loadUrl(url: string | Resource, headers?: Array<WebHeader>): void
```

Loads a specified URL.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string &#124; [Resource](arkts-arkui-resource-t.md) | Yes | URL to load. |
| headers | Array&lt;[WebHeader](arkts-arkui-atomicservice-atomicserviceweb-webheader-i.md)&gt; | No | Additional HTTP request header of the URL. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |
| [17100002](../../apis-arkweb/errorcode-webview.md#17100002-incorrect-url-format) | Invalid url. |
| [17100003](../../apis-arkweb/errorcode-webview.md#17100003-incorrect-resource-path) | Invalid resource path or file type. |

## refresh

```TypeScript
refresh(): void
```

Refreshes the web page.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |

## setCustomUserAgent

```TypeScript
setCustomUserAgent(userAgent: string): void
```

Sets a custom user agent, which will override the default user agent.

Set the user agent in the **onControllerAttached** callback to ensure that it takes effect. For details about the setting, see the example. Avoid setting the user agent in **onLoadIntercept**. Otherwise, the setting may fail occasionally.

> **NOTE:** 
> 
> If a URL is set for the **Web** component **src** and **UserAgent** is not set in the **onControllerAttached**
> callback, calling **setCustomUserAgent** may cause mismatches between the loaded page and the intended user
> agent.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userAgent | string | Yes | Information about the custom user agent. It is recommended that you obtain the current default user agent through [getUserAgent](#getuseragent) and then customize the obtained user agent. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. |
| [17100001](../../apis-arkweb/errorcode-webview.md#17100001-webviewcontroller-not-associated-with-a-web-component) | Init error. The AtomicServiceWebController must be associated with a AtomicServiceWeb component. |
