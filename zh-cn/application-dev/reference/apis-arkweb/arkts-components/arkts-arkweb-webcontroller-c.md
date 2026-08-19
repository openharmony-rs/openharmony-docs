# WebController

* WebController是ArkWeb组件的控制器类，用于控制Web组件的各种行为。一个WebController对象只能与一个Web组件绑定，绑定后开发者可通过该控制器对Web组件进行页面导航（前进/后退/加载）、焦点控制、缩放调 整、页面刷新与停止、Cookie管理、JavaScript注入与执行等操作。 WebController适用于需要在应用侧对嵌入式Web组件进行主动控制的场景，例如实现浏览器式的前进后退导航、在应用侧与网页侧之间建立JavaScript交互通道、动态加载网页内容或管理Cookie数据。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** WebviewController

<!--Device-unnamed-declare class WebController--><!--Device-unnamed-declare class WebController-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## accessBackward

```TypeScript
accessBackward(): boolean
```

当前页面是否可后退，即当前页面是否有返回历史记录。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessBackward

<!--Device-WebController-accessBackward(): boolean--><!--Device-WebController-accessBackward(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 可以后退返回true，否则返回false。 |

## accessForward

```TypeScript
accessForward(): boolean
```

当前页面是否可前进，即当前页面是否有前进历史记录。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessForward

<!--Device-WebController-accessForward(): boolean--><!--Device-WebController-accessForward(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示当前页面可以前进，返回false表示当前页面不可以前进。 |

## accessStep

```TypeScript
accessStep(step: number): boolean
```

检查当前页面是否可前进或者后退给定的step步。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** accessStep

<!--Device-WebController-accessStep(step: number): boolean--><!--Device-WebController-accessStep(step: number): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| step | number | 是 | 要跳转的步数，正数代表前进，负数代表后退。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 页面是否可以前进或后退给定的step步。true表示可以，false为不可以。 |

## backward

```TypeScript
backward()
```

按照历史栈，后退一个页面。建议在调用backward前先调用 [accessBackward&lt;sup&gt;9+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#accessbackward)检查当前页面是否可后退。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** backward

<!--Device-WebController-backward()--><!--Device-WebController-backward()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## clearHistory

```TypeScript
clearHistory(): void
```

删除所有前进后退记录。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** clearHistory

<!--Device-WebController-clearHistory(): void--><!--Device-WebController-clearHistory(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

WebController的构造函数。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** constructor

<!--Device-WebController-constructor()--><!--Device-WebController-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## deleteJavaScriptRegister

```TypeScript
deleteJavaScriptRegister(name: string)
```

删除通过registerJavaScriptProxy注册到window上的指定name的应用侧JavaScript对象。删除后立即生效，无须调用[refresh](#refresh)接口。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteJavaScriptRegister

<!--Device-WebController-deleteJavaScriptRegister(name: string)--><!--Device-WebController-deleteJavaScriptRegister(name: string)-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 注册对象的名称，可在网页侧JavaScript中通过此名称调用应用侧JavaScript对象。 |

## forward

```TypeScript
forward()
```

按照历史栈，前进一个页面。建议在调用forward前先调用 [accessForward&lt;sup&gt;9+&lt;/sup&gt;](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#accessforward)检查当前页面是否可前进。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** forward

<!--Device-WebController-forward()--><!--Device-WebController-forward()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getCookieManager

```TypeScript
getCookieManager(): WebCookie
```

获取Web组件cookie管理对象。

**起始版本：** 9

**废弃版本：** 9

**替代接口：** [WebCookieManager](../arkts-apis/arkts-arkweb-webview-webcookiemanager-c.md)

<!--Device-WebController-getCookieManager(): WebCookie--><!--Device-WebController-getCookieManager(): WebCookie-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WebCookie](arkts-arkweb-webcookie-c.md) | Web组件cookie管理对象，参考[WebCookie]{ |

## getHitTest

```TypeScript
getHitTest(): HitTestType
```

获取当前被点击区域的元素类型。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getHitTest](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#gethittest)

<!--Device-WebController-getHitTest(): HitTestType--><!--Device-WebController-getHitTest(): HitTestType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HitTestType](arkts-arkweb-hittesttype-e.md) | 被点击区域的元素类型。 |

## loadData

```TypeScript
loadData(options: { data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string })
```

baseUrl为空时，通过“data”协议加载指定的一段字符串。 当baseUrl为“data”协议时，编码后的data字符串将被Web组件作为“data”协议加载。 当baseUrl为“http/https”协议时，编码后的data字符串将被Web组件以类似loadUrl的方式以非编码字符串处理。

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

使用指定的HTTP头加载指定的URL。 通过loadUrl注入的对象只在当前document有效，即通过loadUrl导航到新的页面会无效。 而通过registerJavaScriptProxy注入的对象，在loadUrl导航到新的页面也会有效。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** loadUrl

<!--Device-WebController-loadUrl(options: { url: string | Resource, headers?: Array<Header> })--><!--Device-WebController-loadUrl(options: { url: string | Resource, headers?: Array<Header> })-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { url: string \| Resource, headers?: Array&lt;[Header](arkts-arkweb-header-i.md)&gt; } | 是 | The options with the URL and other information. |

## onActive

```TypeScript
onActive(): void
```

调用此接口通知Web组件进入前台激活状态。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onActive

<!--Device-WebController-onActive(): void--><!--Device-WebController-onActive(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## onInactive

```TypeScript
onInactive(): void
```

调用此接口通知Web组件进入未激活状态。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** onInactive

<!--Device-WebController-onInactive(): void--><!--Device-WebController-onInactive(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## refresh

```TypeScript
refresh()
```

调用此接口通知Web组件刷新网页。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** refresh

<!--Device-WebController-refresh()--><!--Device-WebController-refresh()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## registerJavaScriptProxy

```TypeScript
registerJavaScriptProxy(options: { object: object, name: string, methodList: Array<string> })
```

注入JavaScript对象到window对象中，并在window对象中调用该对象的方法。注入的对象在页面下一次（重新）加载前不会出现在JavaScript中。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** registerJavaScriptProxy

<!--Device-WebController-registerJavaScriptProxy(options: { object: object, name: string, methodList: Array<string> })--><!--Device-WebController-registerJavaScriptProxy(options: { object: object, name: string, methodList: Array<string> })-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { object: object, name: string, methodList: Array&lt;string&gt; } | 是 | The option with the JavaScript object and method list. |

## requestFocus

```TypeScript
requestFocus()
```

使当前Web页面获取焦点。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** requestFocus

<!--Device-WebController-requestFocus()--><!--Device-WebController-requestFocus()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## runJavaScript

```TypeScript
runJavaScript(options: { script: string, callback?: (result: string) => void })
```

异步执行JavaScript脚本，并通过回调方式返回脚本执行的结果。runJavaScript需要在loadUrl完成后，比如onPageEnd中调用。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** runJavaScript

<!--Device-WebController-runJavaScript(options: { script: string, callback?: (result: string) => void })--><!--Device-WebController-runJavaScript(options: { script: string, callback?: (result: string) => void })-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | { script: string, callback?: (result: string) =&gt; void } | 是 | The options with a piece of code and a callback. |

## stop

```TypeScript
stop()
```

停止页面加载。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** stop

<!--Device-WebController-stop()--><!--Device-WebController-stop()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## zoom

```TypeScript
zoom(factor: number): void
```

调整当前网页的缩放比例。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [zoom](../arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#zoom)

<!--Device-WebController-zoom(factor: number): void--><!--Device-WebController-zoom(factor: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factor | number | 是 | The zoom factor. |

