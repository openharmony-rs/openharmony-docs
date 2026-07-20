# NativeMediaPlayerConfig

用于[开启应用接管网页媒体播放功能](web:WebAttribute.enableNativeMediaPlayer)的配置信息。

**起始版本：** 12

<!--Device-unnamed-declare interface NativeMediaPlayerConfig--><!--Device-unnamed-declare interface NativeMediaPlayerConfig-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

是否开启应用接管网页媒体播放功能。

true表示开启应用接管网页媒体播放功能，false表示关闭应用接管网页媒体播放功能。

默认值：false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerConfig-enable: boolean--><!--Device-NativeMediaPlayerConfig-enable: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## shouldOverlay

```TypeScript
shouldOverlay: boolean
```

开启应用接管网页媒体播放功能后，应用接管网页视频的播放器画面是否覆盖网页内容。

true表示改变视频图层的高度，使其覆盖网页内容。false表示不覆盖网页内容，跟原视频图层高度一样，嵌入在网页中。

默认值：false。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerConfig-shouldOverlay: boolean--><!--Device-NativeMediaPlayerConfig-shouldOverlay: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

