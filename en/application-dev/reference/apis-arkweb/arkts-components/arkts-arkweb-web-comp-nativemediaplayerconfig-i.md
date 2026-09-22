# NativeMediaPlayerConfig

```TypeScript
declare interface NativeMediaPlayerConfig
```

Configures the [enableNativeMediaPlayer](arkts-arkweb-web-comp-attribute.md#enablenativemediaplayer) API for the app to take over web page media playback, supporting whether to enable it and whether to override web page content. It is suitable for scenarios where custom media playback behavior is required, improving media playback integration and user experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

Whether to enable the app to take over web media playback.

The value **true** indicates that the app takes over web media playback, and **false** indicates that this feature is disabled.

Default value: **false**

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## shouldOverlay

```TypeScript
shouldOverlay: boolean
```

Whether the player screen of the app-taken-over web video overlays the web content after the app takes over web media playback.

The value **true** indicates that the video layer level is changed to overlay the web content, and **false** indicates that the original layer level is maintained and the video is embedded in the web page.

Default value: **false**

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
