# WebController

Defines the Web controller.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** WebviewController

<!--Device-unnamed-declare class WebController--><!--Device-unnamed-declare class WebController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## accessBackward

```TypeScript
accessBackward(): boolean
```

Checks whether the web page can go back.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessBackward

<!--Device-WebController-accessBackward(): boolean--><!--Device-WebController-accessBackward(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Whether the web page can go back. |

## accessForward

```TypeScript
accessForward(): boolean
```

Checks whether the web page can go forward.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessForward

<!--Device-WebController-accessForward(): boolean--><!--Device-WebController-accessForward(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | @syscap SystemCapability.Web.Webview.Core |

## accessStep

```TypeScript
accessStep(step: number): boolean
```

Checks whether the web page can go back or forward the given number of steps.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessStep

<!--Device-WebController-accessStep(step: number): boolean--><!--Device-WebController-accessStep(step: number): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| step | number | 是 | The number of steps. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | @syscap SystemCapability.Web.Webview.Core |

## backward

```TypeScript
backward()
```

Goes back in the history of the web page.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** backward

<!--Device-WebController-backward()--><!--Device-WebController-backward()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## clearHistory

```TypeScript
clearHistory(): void
```

Clears the history in the Web.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** clearHistory

<!--Device-WebController-clearHistory(): void--><!--Device-WebController-clearHistory(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

<!--Device-WebController-constructor()--><!--Device-WebController-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deleteJavaScriptRegister

```TypeScript
deleteJavaScriptRegister(name: string)
```

Deletes a registered JavaScript object with given name.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteJavaScriptRegister

<!--Device-WebController-deleteJavaScriptRegister(name: string)--><!--Device-WebController-deleteJavaScriptRegister(name: string)-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | The name of a registered JavaScript object to be deleted. |

## forward

```TypeScript
forward()
```

Goes forward in the history of the web page.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** forward

<!--Device-WebController-forward()--><!--Device-WebController-forward()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getCookieManager

```TypeScript
getCookieManager(): WebCookie
```

Gets network cookie manager

**起始版本：** 9

**废弃版本：** 9

**替代接口：** WebCookieManager

<!--Device-WebController-getCookieManager(): WebCookie--><!--Device-WebController-getCookieManager(): WebCookie-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebCookie](arkts-arkweb-web-webcookie-c.md) | @syscap SystemCapability.Web.Webview.Core |

## getHitTest

```TypeScript
getHitTest(): HitTestType
```

获取点击测试类型。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getHitTest

<!--Device-WebController-getHitTest(): HitTestType--><!--Device-WebController-getHitTest(): HitTestType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HitTestType](arkts-arkweb-web-hittesttype-e.md) | 点击测试类型。 |

## loadData

```TypeScript
loadData(options: { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string })
```

Loads the data or URL.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** loadData

<!--Device-WebController-loadData(options: { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string })--><!--Device-WebController-loadData(options: { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string })-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string } | 是 | The options with the data or URL and other information. |

## loadUrl

```TypeScript
loadUrl(options: { url: string | Resource, headers?: Array<Header> })
```

Loads the given URL.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** loadUrl

<!--Device-WebController-loadUrl(options: { url: string | Resource, headers?: Array<Header> })--><!--Device-WebController-loadUrl(options: { url: string | Resource, headers?: Array<Header> })-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { url: string \| Resource, headers?: Array<Header> } | 是 | The options with the URL and other information. |

## onActive

```TypeScript
onActive(): void
```

Let the Web active.It is no longer maintained since API version 9, and it is recommended to use {@link onActive} instead.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onActive

<!--Device-WebController-onActive(): void--><!--Device-WebController-onActive(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onInactive

```TypeScript
onInactive(): void
```

Let the Web inactive.It is no longer maintained since API version 9, and it is recommended to use {@link onInactive} instead.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onInactive

<!--Device-WebController-onInactive(): void--><!--Device-WebController-onInactive(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## refresh

```TypeScript
refresh()
```

refreshes the current URL.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** refresh

<!--Device-WebController-refresh()--><!--Device-WebController-refresh()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## registerJavaScriptProxy

```TypeScript
registerJavaScriptProxy(options: { object: object, name: string, methodList: Array<string> })
```

Registers the JavaScript object and method list.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** registerJavaScriptProxy

<!--Device-WebController-registerJavaScriptProxy(options: { object: object, name: string, methodList: Array<string> })--><!--Device-WebController-registerJavaScriptProxy(options: { object: object, name: string, methodList: Array<string> })-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { object: object, name: string, methodList: Array<string> } | 是 | The option with the JavaScript object and method list. |

## requestFocus

```TypeScript
requestFocus()
```

Gets the request focus.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** requestFocus

<!--Device-WebController-requestFocus()--><!--Device-WebController-requestFocus()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## runJavaScript

```TypeScript
runJavaScript(options: { script: string, callback?: (result: string) => void })
```

Asynchronously execute JavaScript in the context of the currently displayed page.The result of the script execution will be returned through an asynchronous callback.This method must be used on the UI thread, and the callback will also be invoked on the UI thread.<p><strong>API Note</strong>:<br>The state of JavaScript is no longer persisted across navigations like loadUrl.For example, global variables and functions defined before calling loadUrl will not exist in the loaded page.It is recommended that applications use registerJavaScriptProxy to ensure that the JavaScript state can be persisted across page navigations.<p>

**起始版本：** 8

**废弃版本：** 9

**替代接口：** runJavaScript

<!--Device-WebController-runJavaScript(options: { script: string, callback?: (result: string) => void })--><!--Device-WebController-runJavaScript(options: { script: string, callback?: (result: string) => void })-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { script: string, callback?: (result: string) => void } | 是 | The options with a piece of code and a callback. |

## stop

```TypeScript
stop()
```

Stops the current load.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** stop

<!--Device-WebController-stop()--><!--Device-WebController-stop()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## zoom

```TypeScript
zoom(factor: number): void
```

对网页进行缩放。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** zoom

<!--Device-WebController-zoom(factor: number): void--><!--Device-WebController-zoom(factor: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factor | number | 是 | 缩放系数。 |

