# NativeMediaPlayerSurfaceInfo

NativeMediaPlayerSurfaceInfo 使用[enableNativeMediaPlayer](../arkts-components/arkts-arkweb-web-attribute.md#enablenativemediaplayer)来进行同层渲染的 surface 信息配置。该类允许应用接管网页媒体播放功能，通过配置 surface 的 id 和位置信息，实现网页媒体内容与应用界面的同层渲染融合，提升媒体播放体验。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## id

```TypeScript
id: string
```

surface 的 id，用于同层渲染的 NativeImage 的 surfaceId。详见[NativeEmbedDataInfo](../arkts-components/arkts-arkweb-nativeembeddatainfo-i.md)。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

## rect

```TypeScript
rect: RectEvent
```

surface 的位置信息，用于指定同层渲染时 surface 的显示位置和尺寸。

**类型：** [RectEvent](arkts-arkweb-webview-rectevent-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core
