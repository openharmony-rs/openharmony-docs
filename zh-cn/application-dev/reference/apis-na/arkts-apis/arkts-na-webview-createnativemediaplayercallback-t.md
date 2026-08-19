# CreateNativeMediaPlayerCallback

```TypeScript
type CreateNativeMediaPlayerCallback =
        (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge
```

[onCreateNativeMediaPlayer](../../../reference/apis-arkweb/arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer) 方法的参数。一个回调函数，创建一个播放器，用于接管网页中的媒体播放。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-type CreateNativeMediaPlayerCallback =        (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge--><!--Device-webview-type CreateNativeMediaPlayerCallback =        (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [NativeMediaPlayerHandler](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-nativemediaplayerhandler-i.md) | 是 | 通过该对象，将播放器的状态报告给 ArkWeb 内核。 |
| mediaInfo | [MediaInfo](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-mediainfo-i.md) | 是 | 网页媒体的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NativeMediaPlayerBridge](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-nativemediaplayerbridge-i.md) | 接管网页媒体的播放器和 ArkWeb 内核之间的一个接口类。<br/>应用需要实现该接口类。<br/> ArkWeb 内核通过该接口类的对象来控制应用创 建的用来接管网页媒体的播放器。<br/>如果应用返回了 null，则表示应用不接管这个媒体的播放，由 ArkWeb 内核来播放该媒体。 |

