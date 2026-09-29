# run

## Modules to Import

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## run

```TypeScript
function run(): void
```

Trigger the HiRetrieval functionality, make it start working.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-hiRetrieval-function run(): void--><!--Device-hiRetrieval-function run(): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiRetrieval

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 36000001 | Initialization error. Possibly caused by invoking this function before invoking init function. |
