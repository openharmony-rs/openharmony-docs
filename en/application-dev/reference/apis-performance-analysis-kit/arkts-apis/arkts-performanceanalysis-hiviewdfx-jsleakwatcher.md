# @ohos.hiviewdfx.jsLeakWatcher

This module provides the capability of monitoring whether ArkTS objects are leaked.

**Since:** 12

**System capability:** SystemCapability.HiviewDFX.HiChecker

## Modules to Import

```TypeScript
import { jsLeakWatcher } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [check](arkts-performanceanalysis-jsleakwatcher-check-f.md) | Obtains the list of objects that are leaked and registered using **jsLeakWatcher.watch()**. Objects that are not reclaimed after GC is triggered are marked as leaked. |
| [dump](arkts-performanceanalysis-jsleakwatcher-dump-f.md) | Dumps the list of leaked objects and VM memory snapshot. |
| [enable](arkts-performanceanalysis-jsleakwatcher-enable-f.md) | Enables the detection for ArkTS object leaks. This function is disabled by default. |
| [enableLeakWatcher](arkts-performanceanalysis-jsleakwatcher-enableleakwatcher-f.md) | Enables the ArkTS object leak detection. |
| [enableLeakWatcher](arkts-performanceanalysis-jsleakwatcher-enableleakwatcher-f.md) | Enables the ArkTS object leak detection. |
| [watch](arkts-performanceanalysis-jsleakwatcher-watch-f.md) | Registers the object to be checked. |

### Interfaces

| Name | Description |
| --- | --- |
| [LeakWatcherConfig](arkts-performanceanalysis-jsleakwatcher-leakwatcherconfig-i.md) | Defines the **LeakWatcherConfig** object, which contains multiple configurable properties for memory leak monitoring. |

### Enums

| Name | Description |
| --- | --- |
| [MonitorObjectType](arkts-performanceanalysis-jsleakwatcher-monitorobjecttype-e.md) | Enumerates the types of component objects to be monitored. |
