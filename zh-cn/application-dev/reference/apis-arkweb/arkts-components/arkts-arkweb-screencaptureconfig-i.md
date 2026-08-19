# ScreenCaptureConfig

提供 Web 屏幕捕获的配置选项，包括捕获模式。适用于需要自定义网页录屏行为的场景，提升录屏功能的灵活性和用户体验。

**起始版本：** 10

<!--Device-unnamed-declare interface ScreenCaptureConfig--><!--Device-unnamed-declare interface ScreenCaptureConfig-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## captureMode

```TypeScript
captureMode: WebCaptureMode
```

Web屏幕捕获模式。

**类型：** [WebCaptureMode](arkts-arkweb-webcapturemode-e.md)

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScreenCaptureConfig-captureMode: WebCaptureMode--><!--Device-ScreenCaptureConfig-captureMode: WebCaptureMode-End-->

**系统能力：** SystemCapability.Web.Webview.Core

