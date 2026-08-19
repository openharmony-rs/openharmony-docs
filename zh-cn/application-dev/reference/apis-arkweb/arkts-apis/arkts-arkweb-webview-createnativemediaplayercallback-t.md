# CreateNativeMediaPlayerCallback

```TypeScript
type CreateNativeMediaPlayerCallback =
      (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge
```

[onCreateNativeMediaPlayer](arkts-arkweb-webview-webviewcontroller-c.md#oncreatenativemediaplayer)方法的参数。一个回调函数，在网页需要播放媒体时被调用，用于 创建一个播放器接管网页中的媒体播放。通过接管机制，应用可以使用自定义播放器实现特殊功能或优化性能。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-webview-type CreateNativeMediaPlayerCallback =      (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge--><!--Device-webview-type CreateNativeMediaPlayerCallback =      (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [NativeMediaPlayerHandler](arkts-arkweb-webview-nativemediaplayerhandler-i.md) | 是 | 通过该对象，将播放器的状态报告给 ArkWeb 内核。应用通过该对象上报播放、暂停、错误等状态事件，使 ArkWeb 内核能够同步网页中的 媒体播放状态。 |
| mediaInfo | [MediaInfo](arkts-arkweb-webview-mediainfo-i.md) | 是 | 网页媒体的信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NativeMediaPlayerBridge](arkts-arkweb-webview-nativemediaplayerbridge-i.md) | 接管网页媒体播放器和 ArkWeb 内核之间的一个接口类。<br/>应用需要实现该接口类。<br/> ArkWeb 内核通过该接口对象控制应用创建的媒体播放 器。<br/>如果应用返回了 null，则表示应用不接管这个媒体的播放，由 ArkWeb 内核来播放该媒体。 |

