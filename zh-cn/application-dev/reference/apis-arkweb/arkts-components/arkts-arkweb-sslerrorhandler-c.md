# SslErrorHandler

SslErrorHandler是Web组件中处理SSL证书验证错误的类。当加载安全页面时遇到SSL证书错误（如证书过期、主机名不匹配、不受信任的CA），应用可通过onSslErrorEvent回调获取SslErrorHandler实 例，并决定是否继续加载或取消导航。示例代码参考[onSslErrorEvent](arkts-arkweb-web-attribute.md#onsslerrorevent)事件。

**起始版本：** 9

<!--Device-unnamed-declare class SslErrorHandler--><!--Device-unnamed-declare class SslErrorHandler-End-->

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

SslErrorHandler的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorHandler-constructor()--><!--Device-SslErrorHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(): void
```

通知Web组件取消此请求，并停止当前SSL证书验证流程。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorHandler-handleCancel(): void--><!--Device-SslErrorHandler-handleCancel(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleCancel

```TypeScript
handleCancel(abortLoading: boolean): void
```

通知Web组件取消此请求，并根据参数abortLoading决定是否停止加载。

**起始版本：** 20

<!--Device-SslErrorHandler-handleCancel(abortLoading: boolean): void--><!--Device-SslErrorHandler-handleCancel(abortLoading: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abortLoading | boolean | 是 | 是否在取消请求后停止加载页面。 <br>true表示停止加载页面，false表示继续加载页面。 |

## handleConfirm

```TypeScript
handleConfirm(): void
```

忽略SSL证书验证错误，继续加载页面。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SslErrorHandler-handleConfirm(): void--><!--Device-SslErrorHandler-handleConfirm(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

