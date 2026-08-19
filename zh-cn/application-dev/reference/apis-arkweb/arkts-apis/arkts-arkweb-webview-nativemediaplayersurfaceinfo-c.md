# NativeMediaPlayerSurfaceInfo

NativeMediaPlayerSurfaceInfo 使用enableNativeMediaPlayer来进行同层渲染的 surface 信息配置。该类允许应用接管网页媒体播放功能，通过配置 surface 的 id 和位置信息，实现网页媒体内容与应用界面的同层渲染融合，提升媒体播放体验。

**起始版本：** 12

<!--Device-webview-class NativeMediaPlayerSurfaceInfo--><!--Device-webview-class NativeMediaPlayerSurfaceInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## id

```TypeScript
id: string
```

surface 的 id，用于同层渲染的 NativeImage 的 surfaceId。 详见NativeEmbedDataInfo。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerSurfaceInfo-id: string--><!--Device-NativeMediaPlayerSurfaceInfo-id: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## rect

```TypeScript
rect: RectEvent
```

surface 的位置信息，用于指定同层渲染时 surface 的显示位置和尺寸。

**类型：** [RectEvent](arkts-arkweb-webview-rectevent-i.md)

**起始版本：** 12

<!--Device-NativeMediaPlayerSurfaceInfo-rect: RectEvent--><!--Device-NativeMediaPlayerSurfaceInfo-rect: RectEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

