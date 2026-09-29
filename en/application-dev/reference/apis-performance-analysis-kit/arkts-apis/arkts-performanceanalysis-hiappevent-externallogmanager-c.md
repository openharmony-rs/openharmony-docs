# ExternalLogManager

```TypeScript
class ExternalLogManager
```

Defines an external log manager for external log management.

**Since:** 26.0.1

<!--Device-hiAppEvent-class ExternalLogManager--><!--Device-hiAppEvent-class ExternalLogManager-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 26.0.1.

<!--Device-ExternalLogManager-onCapacityReached(container: ExternalLogContainer): void--><!--Device-ExternalLogManager-onCapacityReached(container: ExternalLogContainer): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| container | [ExternalLogContainer](arkts-performanceanalysis-hiappevent-externallogcontainer-c.md) | Yes | The container with all external log files |
