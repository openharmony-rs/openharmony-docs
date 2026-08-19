# WebResourceRequest

WebResourceRequest是Web组件中表示网络资源请求的类，提供了关于请求资源的详细元数据。该对象在`onErrorReceive`、`onHttpErrorReceive`以及请求拦截等事件回调中使用，用于帮助开发者诊断 网络错误、监控请求状态和实现资源拦截控制。通过使用该类，应用可以提升错误处理能力、增强请求可控性和优化用户体验。示例代码参考[onErrorReceive事件](arkts-arkweb-web-attribute.md#onerrorreceive)。

**起始版本：** 8

<!--Device-unnamed-declare class WebResourceRequest--><!--Device-unnamed-declare class WebResourceRequest-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

WebResourceRequest的构造函数。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceRequest-constructor()--><!--Device-WebResourceRequest-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getRequestHeader

```TypeScript
getRequestHeader(): Array<Header>
```

获取资源请求头信息。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceRequest-getRequestHeader(): Array<Header>--><!--Device-WebResourceRequest-getRequestHeader(): Array<Header>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[Header](arkts-arkweb-header-i.md)&gt; | 返回包含请求头键值对信息的数组，每个Header对象包含请求头的名称和对应的值，例如User-Agent、Content-Type等。 |

## getRequestMethod

```TypeScript
getRequestMethod(): string
```

获取请求方法。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceRequest-getRequestMethod(): string--><!--Device-WebResourceRequest-getRequestMethod(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回HTTP请求方法字符串，常见值包括GET、POST、PUT、DELETE等，表示该资源请求所使用的HTTP方法类型。 |

## getRequestUrl

```TypeScript
getRequestUrl(): string
```

获取资源请求的URL信息。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceRequest-getRequestUrl(): string--><!--Device-WebResourceRequest-getRequestUrl(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回完整的资源请求URL字符串，包含协议、域名、路径、查询参数等完整信息。 |

## isMainFrame

```TypeScript
isMainFrame(): boolean
```

判断资源请求是否为主frame。用于区分处理主frame和子frame请求。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceRequest-isMainFrame(): boolean--><!--Device-WebResourceRequest-isMainFrame(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回资源请求是否为主frame的判断结果。 <br>true表示资源请求为主frame，false表示资源请求不为主frame。 |

## isRedirect

```TypeScript
isRedirect(): boolean
```

判断资源请求是否被服务端重定向。用于检查请求重定向链，识别恶意重定向。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceRequest-isRedirect(): boolean--><!--Device-WebResourceRequest-isRedirect(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回资源请求是否被服务端重定向。 <br>true表示资源请求被服务端重定向，false表示资源请求未被服务端重定向。 |

## isRequestGesture

```TypeScript
isRequestGesture(): boolean
```

判断资源请求是否与手势（如点击）相关联。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceRequest-isRequestGesture(): boolean--><!--Device-WebResourceRequest-isRequestGesture(): boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回资源请求是否与手势（如点击）相关联。 <br>true表示返回资源请求与手势（如点击）相关联，false表示返回资源请求与手势（如点击）不相关联。 |

