# OnConsoleEvent

定义通知宿主应用JavaScript console消息。

**起始版本：** 12

<!--Device-unnamed-declare interface OnConsoleEvent--><!--Device-unnamed-declare interface OnConsoleEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## message

```TypeScript
message: ConsoleMessage
```

触发的控制台信息。

**类型：** [ConsoleMessage](arkts-arkweb-consolemessage-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnConsoleEvent-message: ConsoleMessage--><!--Device-OnConsoleEvent-message: ConsoleMessage-End-->

**系统能力：** SystemCapability.Web.Webview.Core

