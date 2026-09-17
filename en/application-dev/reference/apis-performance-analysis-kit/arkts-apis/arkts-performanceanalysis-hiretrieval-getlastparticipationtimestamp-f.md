# getLastParticipationTimestamp

## Modules to Import

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## getLastParticipationTimestamp

```TypeScript
function getLastParticipationTimestamp(): number
```

Query the UNIX timestamp of the last participating time.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiRetrieval

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the timestamp of the last participating time in milliseconds, if never participated return 0. |
