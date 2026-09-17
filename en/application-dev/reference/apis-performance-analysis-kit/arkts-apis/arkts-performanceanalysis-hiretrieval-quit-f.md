# quit

## Modules to Import

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## quit

```TypeScript
function quit(): void
```

Quit the HiRetrieval project. This operation clears the current HiRetrieval config. Invoking init function again is required after invoking quit function.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiRetrieval

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 36000001 | Initialization error. Possibly caused by invoking this function before invoking init function. |
