# WebResourceError

WebResourceError是Web组件中提供资源加载失败错误信息的类。该错误对象通过`onErrorReceive`和`onHttpErrorReceive`事件回调提供给应用，封装了错误详情用于调试和错误处理。通常与 WebResourceRequest配合使用以确定哪个资源加载失败。示例代码参考[onErrorReceive事件](arkts-arkweb-web-attribute.md#onerrorreceive)。

**起始版本：** 8

<!--Device-unnamed-declare class WebResourceError--><!--Device-unnamed-declare class WebResourceError-End-->

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

WebResourceError的构造函数，创建WebResourceError对象，用于封装Web组件资源加载失败时的错误信息。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceError-constructor()--><!--Device-WebResourceError-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## getCustomErrorCode

```TypeScript
getCustomErrorCode(): number
```

获取加载资源的自定义错误码。自定义错误码通过[WebSchemeHandlerResponse](../arkts-apis/arkts-arkweb-webview-webschemehandlerresponse-c.md)的 [setCustomErrorCode](../arkts-apis/arkts-arkweb-webview-webschemehandlerresponse-c.md#setcustomerrorcode)设置， 并通过[onErrorReceive](arkts-arkweb-web-attribute.md#onerrorreceive)事件直接传递给应用。

**起始版本：** 26.1.0

<!--Device-WebResourceError-getCustomErrorCode(): number--><!--Device-WebResourceError-getCustomErrorCode(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回加载资源的自定义错误码。 |

## getErrorCode

```TypeScript
getErrorCode(): number
```

获取加载资源的错误码。用于判断资源加载失败的具体原因（如网络错误、服务器错误、权限问题等），以便开发者根据错误类型采取相应的处理策略（如重试、提示用户、降级显示等）。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceError-getErrorCode(): number--><!--Device-WebResourceError-getErrorCode(): number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回加载资源的错误码。错误码含义参考[WebNetErrorList]{ |

## getErrorInfo

```TypeScript
getErrorInfo(): string
```

获取加载资源的错误信息。用于详细描述资源加载失败的具体原因，开发者可将错误信息输出到日志用于调试分析，或向用户显示友好的错误提示。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WebResourceError-getErrorInfo(): string--><!--Device-WebResourceError-getErrorInfo(): string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回加载资源的错误信息。 |

