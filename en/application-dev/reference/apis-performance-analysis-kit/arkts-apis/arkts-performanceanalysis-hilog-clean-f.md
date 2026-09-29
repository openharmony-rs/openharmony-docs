# clean

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## clean

```TypeScript
function clean(): void
```

Delete all hilog logs in the sandbox.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-hilog-function clean(): void--><!--Device-hilog-function clean(): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

**Examples**

```TypeScript
hilog.clean();
```
