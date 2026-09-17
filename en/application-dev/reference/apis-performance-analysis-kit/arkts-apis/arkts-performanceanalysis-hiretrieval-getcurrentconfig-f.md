# getCurrentConfig

## Modules to Import

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## getCurrentConfig

```TypeScript
function getCurrentConfig(): HiRetrievalConfig
```

Query the current HiRetrieval config.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiRetrieval

**Return value:**

| Type | Description |
| --- | --- |
| [HiRetrievalConfig](arkts-performanceanalysis-hiretrieval-hiretrievalconfig-i.md) | Returns the current HiRetrieval config, an empty HiRetrievalConfig will be returned if the result of invoking isParticipant function is false. |
