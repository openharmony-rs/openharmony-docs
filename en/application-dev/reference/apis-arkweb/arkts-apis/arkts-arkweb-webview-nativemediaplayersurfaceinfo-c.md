# NativeMediaPlayerSurfaceInfo

NativeMediaPlayerSurfaceInfo uses [enableNativeMediaPlayer](../arkts-components/arkts-arkweb-web-comp-attribute.md#enablenativemediaplayer) to configure the surface information for same-layer rendering. This class allows an app to take over the web media playback functionality, configuring the surface ID and position information to integrate web media content with the app UI through same-layer rendering and enhance the media playback experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## id

```TypeScript
id: string
```

ID of the surface, which is the surfaceId of the NativeImage used for same-layer rendering.

For details, see [NativeEmbedDataInfo](../arkts-components/arkts-arkweb-nativeembeddatainfo-i.md).

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## rect

```TypeScript
rect: RectEvent
```

Position information of the surface, used to specify the display position and size of the surface during same- layer rendering.

**Type:** [RectEvent](arkts-arkweb-webview-rectevent-i.md)

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core
