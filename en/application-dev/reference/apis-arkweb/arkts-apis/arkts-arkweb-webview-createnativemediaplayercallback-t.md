# CreateNativeMediaPlayerCallback

```TypeScript
type CreateNativeMediaPlayerCallback =
      (handler: NativeMediaPlayerHandler, mediaInfo: MediaInfo) => NativeMediaPlayerBridge
```

Parameter of the [onCreateNativeMediaPlayer](arkts-arkweb-webview-webviewcontroller-c.md#oncreatenativemediaplayer) method. A callback invoked when the webpage needs to play media, used to create a player to take over media playback in the webpage. Through this takeover mechanism, the app can use a custom player to implement special features or optimize performance.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [NativeMediaPlayerHandler](arkts-arkweb-webview-nativemediaplayerhandler-i.md) | Yes | Object used by the app to report player status events, such as play, pause, and error, to the ArkWeb kernel, enabling the kernel to synchronize media playback states in web pages. |
| mediaInfo | [MediaInfo](arkts-arkweb-webview-mediainfo-i.md) | Yes | Information about the media on the web page. |

**Return value:**

| Type | Description |
| --- | --- |
| [NativeMediaPlayerBridge](arkts-arkweb-webview-nativemediaplayerbridge-i.md) | An interface class that bridges the web media player and the ArkWeb kernel.<br>The app needs to implement this interface class.<br>The ArkWeb kernel controls the media player created by the app through this interface object.<br>If the app returns null, it indicates that the app does not take over the playback of this media, and the ArkWeb kernel plays the media. |
