# WebController

Defines the Web controller.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** WebviewController

**系统能力：** SystemCapability.Web.Webview.Core

## accessBackward

```TypeScript
accessBackward(): boolean
```

Checks whether the web page can go back.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessBackward

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

**系统能力：** SystemCapability.Web.Webview.Core

## clearHistory

```TypeScript
clearHistory(): void
```

Clears the history in the Web.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** clearHistory

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructor.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

**系统能力：** SystemCapability.Web.Webview.Core

## deleteJavaScriptRegister

```TypeScript
deleteJavaScriptRegister(name: string)
```

Deletes a registered JavaScript object with given name.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteJavaScriptRegister

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

**系统能力：** SystemCapability.Web.Webview.Core

## getCookieManager

```TypeScript
getCookieManager(): WebCookie
```

Gets network cookie manager

**起始版本：** 9

**废弃版本：** 9

**替代接口：** WebCookieManager

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WebCookie | @syscap SystemCapability.Web.Webview.Core |

## getHitTest

```TypeScript
getHitTest(): HitTestType
```

获取点击测试类型。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getHitTest

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HitTestType | 点击测试类型。 |

## loadData

```TypeScript
loadData(options: { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string })
```

Loads the data or URL.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** loadData

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

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { url: string \| Resource, headers?: Array&lt;Header&gt; } | 是 | The options with the URL and other information. |

## onActive

```TypeScript
onActive(): void
```

Let the Web active.
It is no longer maintained since API version 9, and it is recommended to use {@link onActive} instead.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onActive

**系统能力：** SystemCapability.Web.Webview.Core

## onInactive

```TypeScript
onInactive(): void
```

Let the Web inactive.
It is no longer maintained since API version 9, and it is recommended to use {@link onInactive} instead.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onInactive

**系统能力：** SystemCapability.Web.Webview.Core

## refresh

```TypeScript
refresh()
```

refreshes the current URL.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** refresh

**系统能力：** SystemCapability.Web.Webview.Core

## registerJavaScriptProxy

```TypeScript
registerJavaScriptProxy(options: { object: object, name: string, methodList: Array<string> })
```

Registers the JavaScript object and method list.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** registerJavaScriptProxy

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { object: object, name: string, methodList: Array&lt;string&gt; } | 是 | The option with the JavaScript object and method list. |

## requestFocus

```TypeScript
requestFocus()
```

Gets the request focus.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** requestFocus

**系统能力：** SystemCapability.Web.Webview.Core

## runJavaScript

```TypeScript
runJavaScript(options: { script: string, callback?: (result: string) => void })
```

Asynchronously execute JavaScript in the context of the currently displayed page.
The result of the script execution will be returned through an asynchronous callback.
This method must be used on the UI thread, and the callback will also be invoked on the UI thread.
<p><strong>API Note</strong>:<br>
The state of JavaScript is no longer persisted across navigations like loadUrl.
For example, global variables and functions defined before calling loadUrl will not exist in the loaded page.
It is recommended that applications use registerJavaScriptProxy to ensure that the JavaScript state can be persisted across page navigations.
<p>

**起始版本：** 8

**废弃版本：** 9

**替代接口：** runJavaScript

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { script: string, callback?: (result: string) =&gt; void } | 是 | The options with a piece of code and a callback. |

## stop

```TypeScript
stop()
```

Stops the current load.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** stop

**系统能力：** SystemCapability.Web.Webview.Core

## zoom

```TypeScript
zoom(factor: number): void
```

对网页进行缩放。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** zoom

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factor | number | 是 | 缩放系数。 |

