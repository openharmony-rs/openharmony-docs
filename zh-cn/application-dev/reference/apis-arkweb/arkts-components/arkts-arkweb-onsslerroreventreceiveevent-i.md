# OnSslErrorEventReceiveEvent

定义网页收到SSL错误时触发的回调信息，包括错误码和证书链。适用于需要处理SSL错误的场景，提升安全异常的监控和处理能力。

**起始版本：** 12

<!--Device-unnamed-declare interface OnSslErrorEventReceiveEvent--><!--Device-unnamed-declare interface OnSslErrorEventReceiveEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## certChainData

```TypeScript
certChainData?: Array<Uint8Array>
```

证书链数据。

**类型：** Array&lt;Uint8Array&gt;

**起始版本：** 15

<!--Device-OnSslErrorEventReceiveEvent-certChainData?: Array<Uint8Array>--><!--Device-OnSslErrorEventReceiveEvent-certChainData?: Array<Uint8Array>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## error

```TypeScript
error: SslError
```

错误码。

**类型：** [SslError](arkts-arkweb-sslerror-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnSslErrorEventReceiveEvent-error: SslError--><!--Device-OnSslErrorEventReceiveEvent-error: SslError-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: SslErrorHandler
```

通知Web组件用户操作行为。

**类型：** [SslErrorHandler](arkts-arkweb-sslerrorhandler-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnSslErrorEventReceiveEvent-handler: SslErrorHandler--><!--Device-OnSslErrorEventReceiveEvent-handler: SslErrorHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

