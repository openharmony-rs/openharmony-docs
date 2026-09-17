# @ohos.hiviewdfx.hiRetrieval

Provide interfaces and functions for HiRetrieval feature.

**Since:** 26.0.0

**System capability:** SystemCapability.HiviewDFX.HiRetrieval

## Modules to Import

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getCurrentConfig](arkts-performanceanalysis-hiretrieval-getcurrentconfig-f.md) | Query the current HiRetrieval config. |
| [getLastParticipationTimestamp](arkts-performanceanalysis-hiretrieval-getlastparticipationtimestamp-f.md) | Query the UNIX timestamp of the last participating time. |
| [init](arkts-performanceanalysis-hiretrieval-init-f.md) | Init the HiRetrieval functionality. |
| [isParticipant](arkts-performanceanalysis-hiretrieval-isparticipant-f.md) | Query if the app is participating the HiRetrieval project. |
| [participate](arkts-performanceanalysis-hiretrieval-participate-f.md) | Participate the HiRetrieval project with given HiRetrievalConfig. |
| [quit](arkts-performanceanalysis-hiretrieval-quit-f.md) | Quit the HiRetrieval project. This operation clears the current HiRetrieval config. Invoking init function again is required after invoking quit function. |
| [run](arkts-performanceanalysis-hiretrieval-run-f.md) | Trigger the HiRetrieval functionality, make it start working. |

### Interfaces

| Name | Description |
| --- | --- |
| [HiRetrievalConfig](arkts-performanceanalysis-hiretrieval-hiretrievalconfig-i.md) | HiRetrieval functionality config. |
