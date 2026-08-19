# VerifyPinEvent

定义当需要用户进行PIN码认证时触发回调。

**起始版本：** 22

<!--Device-unnamed-declare interface VerifyPinEvent--><!--Device-unnamed-declare interface VerifyPinEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## handler

```TypeScript
handler: VerifyPinHandler
```

通知Web组件用户操作行为。

**类型：** [VerifyPinHandler](arkts-arkweb-verifypinhandler-c.md)

**起始版本：** 22

<!--Device-VerifyPinEvent-handler: VerifyPinHandler--><!--Device-VerifyPinEvent-handler: VerifyPinHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## identity

```TypeScript
identity: string
```

用于认证的证书凭据标识。

**类型：** string

**起始版本：** 22

<!--Device-VerifyPinEvent-identity: string--><!--Device-VerifyPinEvent-identity: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

