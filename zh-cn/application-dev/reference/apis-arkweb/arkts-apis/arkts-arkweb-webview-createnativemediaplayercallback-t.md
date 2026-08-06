# CreateNativeMediaPlayerCallback

```TypeScript
type CreateNativeMediaPlayerCallback =
      (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge
```

[onCreateNativeMediaPlayer]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 方法的参数。一个回调函数，创建一个播放器，用于接管网页中的媒体播放。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-webview-type CreateNativeMediaPlayerCallback =      (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge--><!--Device-webview-type CreateNativeMediaPlayerCallback =      (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 通过该对象，将播放器的状态报告给 ArkWeb 内核。  |
| mediaInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 网页媒体的信息。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 接管网页媒体的播放器和 ArkWeb 内核之间的一个接口类。\_\_\_HTML\_TAG\_USD\_0\_\_\_应用需要实现该接口类。\_\_\_HTML\_TAG\_USD\_1\_\_\_ ArkWeb 内核通过该接口类的对象来控制应用创建的 |

