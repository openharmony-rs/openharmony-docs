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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.0.

<!--Device-hiRetrieval-function getLastParticipationTimestamp(): long--><!--Device-hiRetrieval-function getLastParticipationTimestamp(): long-End-->

**System capability:** SystemCapability.HiviewDFX.HiRetrieval

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the timestamp of the last participating time in milliseconds, if never participated return 0. |
