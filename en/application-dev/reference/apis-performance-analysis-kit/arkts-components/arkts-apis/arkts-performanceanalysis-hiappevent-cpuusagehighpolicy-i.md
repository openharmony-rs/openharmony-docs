# CpuUsageHighPolicy

Defines the configuration policy for the high CPU usage event.

> **NOTE:** 
> 
> After this API is called, the setting is persisted. If this API is called again and the corresponding parameter
> is not set, the value used by the system last time is used.

**Since:** 22

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## backgroundLoadThreshold

```TypeScript
backgroundLoadThreshold?: number
```

High CPU usage threshold of the application background, in percentage. The value range is **[1, 100]**. The default value is **10**. If the value is not within the threshold range, the default value **10** is used.

**Note:**  It is recommended that the value be less than **10**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## foregroundLoadThreshold

```TypeScript
foregroundLoadThreshold?: number
```

High CPU usage threshold of the application foreground, in percentage. The value range is **[1, 100]**. The default value is **30**. If the value is not within the threshold range, the default value **30** is used.

**Note:**  It is recommended that the value be less than **30**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## perfLogCaptureCount

```TypeScript
perfLogCaptureCount?: number
```

Number of log collection times per day. Once the system detects that the number of log collection times exceeds the set value, the system still reports the event normally, but the **external_log** field in the exception event is not attached with the log file path information.

For debug-type applications, the threshold range is **[-1, 100]**.

For release-type applications, the threshold range is **[0, 20]**.

Unit: times. Default value: **1**.

If the value is not within the threshold range, the default value **1** is used.

**NOTE:** 

1. The value **-1** indicates that log collection times are not limited.
2. The value **0** indicates that logs are not collected.
3. A value greater than **0** indicates the maximum number of daily collection times.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## threadLoadInterval

```TypeScript
threadLoadInterval?: number
```

Interval for detecting high CPU usage of application threads, in seconds. The value range is **[5, 3600]**. The default value is **60**.

If the value is not within the threshold range, the default value **60** is used.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## threadLoadThreshold

```TypeScript
threadLoadThreshold?: number
```

High CPU usage threshold of the application thread, in percentage. The value range is **[15, 100]**. The default value is **70**. If the value is not within the threshold range, the default value **70** is used.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
