# NativeMediaPlayerConfig

用于配置应用接管网页媒体播放功能接口[enableNativeMediaPlayer](arkts-arkweb-web-attribute.md#enablenativemediaplayer)的功能，支持是否开启及是否覆盖网页内容。适用于需要自定义媒体 播放行为的场景，提升媒体播放的集成度和用户体验。

**起始版本：** 12

<!--Device-unnamed-declare interface NativeMediaPlayerConfig--><!--Device-unnamed-declare interface NativeMediaPlayerConfig-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## enable

```TypeScript
enable: boolean
```

是否开启应用接管网页媒体播放功能。 true表示开启应用接管网页媒体播放功能，false表示关闭该功能。 默认值：false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerConfig-enable: boolean--><!--Device-NativeMediaPlayerConfig-enable: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## shouldOverlay

```TypeScript
shouldOverlay: boolean
```

开启应用接管网页媒体播放功能后，应用接管网页视频的播放器画面是否覆盖网页内容。 true表示改变视频图层的层级，覆盖网页内容。false表示保持原层级，嵌入在网页中。 默认值：false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerConfig-shouldOverlay: boolean--><!--Device-NativeMediaPlayerConfig-shouldOverlay: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

