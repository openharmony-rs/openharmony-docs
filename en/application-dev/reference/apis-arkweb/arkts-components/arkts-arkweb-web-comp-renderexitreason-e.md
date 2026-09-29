# RenderExitReason

```TypeScript
declare enum RenderExitReason
```

Enumerates the reasons why the rendering process exits.

**Since:** 9

<!--Device-unnamed-declare enum RenderExitReason--><!--Device-unnamed-declare enum RenderExitReason-End-->

**System capability:** SystemCapability.Web.Webview.Core

## ProcessAbnormalTermination

```TypeScript
ProcessAbnormalTermination = 0
```

The rendering process exited abnormally. Possible causes include rendering process startup timeout, system reclaiming old rendering processes due to reaching the process quantity limit, and simultaneous closing of multiple tabs.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RenderExitReason-ProcessAbnormalTermination = 0--><!--Device-RenderExitReason-ProcessAbnormalTermination = 0-End-->

**System capability:** SystemCapability.Web.Webview.Core

## ProcessWasKilled

```TypeScript
ProcessWasKilled = 1
```

The rendering process receives a SIGKILL message or is manually terminated.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RenderExitReason-ProcessWasKilled = 1--><!--Device-RenderExitReason-ProcessWasKilled = 1-End-->

**System capability:** SystemCapability.Web.Webview.Core

## ProcessCrashed

```TypeScript
ProcessCrashed = 2
```

The rendering process crashes due to segmentation or other errors.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RenderExitReason-ProcessCrashed = 2--><!--Device-RenderExitReason-ProcessCrashed = 2-End-->

**System capability:** SystemCapability.Web.Webview.Core

## ProcessOom

```TypeScript
ProcessOom = 3
```

The program memory is insufficient.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RenderExitReason-ProcessOom = 3--><!--Device-RenderExitReason-ProcessOom = 3-End-->

**System capability:** SystemCapability.Web.Webview.Core

## ProcessExitUnknown

```TypeScript
ProcessExitUnknown = 4
```

Other reasons, such as rendering process spawning failure.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RenderExitReason-ProcessExitUnknown = 4--><!--Device-RenderExitReason-ProcessExitUnknown = 4-End-->

**System capability:** SystemCapability.Web.Webview.Core
