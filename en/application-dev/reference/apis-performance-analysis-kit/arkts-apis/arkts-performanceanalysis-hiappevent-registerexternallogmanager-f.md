# registerExternalLogManager

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## registerExternalLogManager

```TypeScript
function registerExternalLogManager(logMngr: ExternalLogManager): void
```

Register external log manager

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-hiAppEvent-function registerExternalLogManager(logMngr: ExternalLogManager): void--><!--Device-hiAppEvent-function registerExternalLogManager(logMngr: ExternalLogManager): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| logMngr | [ExternalLogManager](arkts-performanceanalysis-hiappevent-externallogmanager-c.md) | Yes | the external log manager. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 11106001 | State error. Possible causes: 1. Log manager already registered; |
