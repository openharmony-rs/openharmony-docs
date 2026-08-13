# NativeMediaPlayerConfig

用于 [开启应用接管网页媒体播放功能](../../../reference/apis-arkweb/arkts-basic-components-web-attributes.md#enablenativemediaplayer12)的 配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface NativeMediaPlayerConfig--><!--Device-unnamed-export declare interface NativeMediaPlayerConfig-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

是否开启应用接管网页媒体播放功能。 true表示开启应用接管网页媒体播放功能，false表示关闭应用接管网页媒体播放功能。 默认值：false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-NativeMediaPlayerConfig-enable: boolean--><!--Device-NativeMediaPlayerConfig-enable: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## shouldOverlay

```TypeScript
shouldOverlay: boolean
```

开启应用接管网页媒体播放功能后，应用接管网页视频的播放器画面是否覆盖网页内容。 true表示改变视频图层的高度，使其覆盖网页内容。false表示不覆盖网页内容，跟原视频图层高度一样，嵌入在网页中。 默认值：false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-NativeMediaPlayerConfig-shouldOverlay: boolean--><!--Device-NativeMediaPlayerConfig-shouldOverlay: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

