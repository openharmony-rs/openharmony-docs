# FullScreenExitHandler

FullScreenExitHandler 是 Web 组件提供的全屏退出处理类，用于响应网页退出全屏模式的事件。该类通过 exitFullScreen 方法通知开发者 Web 组件已退出全屏状态，帮助开发者及时处理全屏状态变化，调整 应用界面布局或执行相应逻辑。示例代码参考[onFullScreenEnter](arkts-arkweb-web-attribute.md#onfullscreenenter)。

**起始版本：** 9

<!--Device-unnamed-declare class FullScreenExitHandler--><!--Device-unnamed-declare class FullScreenExitHandler-End-->

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

FullScreenExitHandler的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FullScreenExitHandler-constructor()--><!--Device-FullScreenExitHandler-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## exitFullScreen

```TypeScript
exitFullScreen(): void
```

通知开发者Web组件退出全屏。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FullScreenExitHandler-exitFullScreen(): void--><!--Device-FullScreenExitHandler-exitFullScreen(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

