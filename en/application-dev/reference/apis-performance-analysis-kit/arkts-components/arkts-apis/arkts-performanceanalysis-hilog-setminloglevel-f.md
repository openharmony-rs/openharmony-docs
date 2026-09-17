# setMinLogLevel

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## setMinLogLevel

```TypeScript
function setMinLogLevel(level: LogLevel): void
```

Sets the minimum log level.

> **NOTE:** 
> 
> If the set log level is lower than the
> [global log level](../../../dfx/hilog.md#displaying-and-setting-log-levels), the setting does not take effect.
> 
> This function does not take effect for debug applications.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.HiviewDFX.HiLog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [LogLevel](arkts-performanceanalysis-hilog-loglevel-e.md) | Yes | Log level. |

**Examples**

```TypeScript
The following example prints five HiLog logs of different levels and calls the setMinLogLevel API twice when the global log level is INFO:
```

```TypeScript
The first log is printed properly because the global log level is INFO.

After the minimum log level of the process is set to WARN, the second log does not meet the log level and fails to be printed. The third log is printed properly.

After the minimum log level of the process is set to DEBUG, the fourth log does not meet the global log level and fails to be printed. The fifth log is printed.

The log result is as follows:
```
