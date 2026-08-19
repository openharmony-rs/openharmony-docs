# OnAudioStateChangedEvent

定义网页音频播放状态改变时触发的回调信息，包括播放状态。适用于需要监控音频播放行为的场景，提升音频管理的可见性和用户体验。

**起始版本：** 12

<!--Device-unnamed-declare interface OnAudioStateChangedEvent--><!--Device-unnamed-declare interface OnAudioStateChangedEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## playing

```TypeScript
playing: boolean
```

当前页面的音频播放状态，true表示正在播放，false表示未播放。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnAudioStateChangedEvent-playing: boolean--><!--Device-OnAudioStateChangedEvent-playing: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

