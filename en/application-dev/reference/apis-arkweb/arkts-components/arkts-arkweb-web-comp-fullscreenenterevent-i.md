# FullScreenEnterEvent

```TypeScript
declare interface FullScreenEnterEvent
```

Provides the callback information for the **Web** component to enter the full-screen mode, including the video size and exit handler. It is suitable for scenarios where handling full-screen video is required, improving video playback immersive experience and controllability.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: FullScreenExitHandler
```

Function handle for exiting full screen mode.

**Type:** [FullScreenExitHandler](arkts-arkweb-web-comp-fullscreenexithandler-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## videoHeight

```TypeScript
videoHeight?: number
```

Video height, in px. If the element that enters fulls screen mode is a **&lt;video&gt;** element, the value represents its height; if the element that enters fulls screen mode contains a **&lt;video&gt;** element, the value represents the height of the first sub-video element; in other cases, the value is **0**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## videoWidth

```TypeScript
videoWidth?: number
```

Video width, in px. If the element that enters fulls screen mode is a **&lt;video&gt;** element, the value represents its width; if the element that enters fulls screen mode contains a **&lt;video&gt;** element, the value represents the width of the first sub-video element; in other cases, the value is **0**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
