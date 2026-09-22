# ExternalLogManager

```TypeScript
class ExternalLogManager
```

Defines an external log manager for external log management.

**Since:** 26.0.1

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

**Since:** 26.0.1

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| container | [ExternalLogContainer](arkts-performanceanalysis-hiappevent-externallogcontainer-c.md) | Yes | The container with all external log files |
