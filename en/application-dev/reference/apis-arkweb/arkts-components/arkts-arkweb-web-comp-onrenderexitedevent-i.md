# OnRenderExitedEvent

```TypeScript
declare interface OnRenderExitedEvent
```

Defines the callback triggered when the rendering process exits. It is suitable for scenarios where monitoring rendering process exceptions is required, improving rendering stability and troubleshooting efficiency.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## renderExitReason

```TypeScript
renderExitReason: RenderExitReason
```

Cause for the abnormal exit of the rendering process.

**Type:** [RenderExitReason](arkts-arkweb-web-comp-renderexitreason-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
