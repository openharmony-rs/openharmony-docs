# ExternalLogManager

Defines an external log manager for external log management.

**Since:** 26.1.0

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## onCapacityReached

```TypeScript
onCapacityReached(container: ExternalLogContainer): void
```

This function is called when external log directory capacity is reached

**Since:** 26.1.0

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| container | [ExternalLogContainer](arkts-performanceanalysis-hiappevent-externallogcontainer-c.md) | Yes | The container with all external log files |
