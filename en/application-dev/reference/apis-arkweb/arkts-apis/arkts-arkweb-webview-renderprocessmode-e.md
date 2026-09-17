# RenderProcessMode

Enumerates the ArkWeb renderer subprocess mode types. You can select the appropriate mode based on the app's requirements for memory usage and renderer process isolation.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## SINGLE

```TypeScript
SINGLE = 0
```

ArkWeb single render subprocess mode. In this mode, multiple **Web** components share one render subprocess.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## MULTIPLE

```TypeScript
MULTIPLE = 1
```

ArkWeb multi-render subprocess mode. In this mode, each **Web** component has a rendering subprocess.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
