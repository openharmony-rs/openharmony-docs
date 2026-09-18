# TriggerCondition

Defines the triggering condition parameters of the **onTrigger** callback of a [Watcher](arkts-performanceanalysis-hiappevent-watcher-i.md).

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## row

```TypeScript
row?: number
```

Total number of events that trigger callback. The value is a positive integer. The default value is 0, indicating that no callback is triggered. If this parameter is set to a negative value, the default value is used.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## size

```TypeScript
size?: number
```

Total size of events that trigger callback. The value is a positive integer, in bytes. The default value is 0, indicating that no callback is triggered. If this parameter is set to a negative value, the default value is used.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## timeOut

```TypeScript
timeOut?: number
```

Timeout interval for triggering callback. The value is a positive integer, in unit of 30s. The default value is 0, indicating that no callback is triggered. If this parameter is set to a negative value, the default value is used.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
