# OnScreenCaptureRequestEvent

定义收到屏幕捕获请求时触发的回调信息。适用于需要处理屏幕录制权限的场景，提升录屏流程的可控性和安全性。

**起始版本：** 12

<!--Device-unnamed-declare interface OnScreenCaptureRequestEvent--><!--Device-unnamed-declare interface OnScreenCaptureRequestEvent-End-->

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
handler: ScreenCaptureHandler
```

通知Web组件用户操作行为。

**类型：** [ScreenCaptureHandler](arkts-arkweb-screencapturehandler-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnScreenCaptureRequestEvent-handler: ScreenCaptureHandler--><!--Device-OnScreenCaptureRequestEvent-handler: ScreenCaptureHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

