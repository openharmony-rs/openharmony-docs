# isTraceEnabled

## Modules to Import

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## isTraceEnabled

```TypeScript
function isTraceEnabled(): boolean
```

Checks whether application trace capture is enabled.

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-hiTraceMeter-function isTraceEnabled(): boolean--><!--Device-hiTraceMeter-function isTraceEnabled(): boolean-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true** is returned when the trace capture is enabled using [hitrace](../../../dfx/hitrace.md). **false** is returned when it is disabled or stopped. In this case, calling the HiTraceMeter API does not take effect. |

**Examples**

```TypeScript
if (hiTraceMeter.isTraceEnabled()) {
  // Service flow...
} else {
  // Service flow...
}
```
