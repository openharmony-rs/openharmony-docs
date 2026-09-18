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

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| logMngr | [ExternalLogManager](arkts-performanceanalysis-hiappevent-externallogmanager-c.md) | Yes | the external log manager. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 11106001 | State error. Possible causes: 1. Log manager already registered; |
