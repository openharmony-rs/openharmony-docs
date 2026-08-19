# FullScreenEnterEvent

提供 Web 组件进入全屏的回调信息，包括视频尺寸和退出句柄。适用于需要处理全屏视频的场景，提升视频播放的沉浸式体验和可控性。

**起始版本：** 12

<!--Device-unnamed-declare interface FullScreenEnterEvent--><!--Device-unnamed-declare interface FullScreenEnterEvent-End-->

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
handler: FullScreenExitHandler
```

用于退出全屏模式的函数句柄。

**类型：** [FullScreenExitHandler](arkts-arkweb-fullscreenexithandler-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FullScreenEnterEvent-handler: FullScreenExitHandler--><!--Device-FullScreenEnterEvent-handler: FullScreenExitHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## videoHeight

```TypeScript
videoHeight?: number
```

视频的高度，单位：px。如果进入全屏的是 `&lt;video&gt;` 元素，表示其高度；如果进入全屏的子元素中包含 `&lt;video&gt;` 元素，表示第一个子视频元素的高度；其他情况下，为0。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FullScreenEnterEvent-videoHeight?: number--><!--Device-FullScreenEnterEvent-videoHeight?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## videoWidth

```TypeScript
videoWidth?: number
```

视频的宽度，单位：px。如果进入全屏的是 `&lt;video&gt;` 元素，表示其宽度；如果进入全屏的子元素中包含 `&lt;video&gt;` 元素，表示第一个子视频元素的宽度；其他情况下，为0。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FullScreenEnterEvent-videoWidth?: number--><!--Device-FullScreenEnterEvent-videoWidth?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

