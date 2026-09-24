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

The following example prints five HiLog logs of different levels and calls the setMinLogLevel API twice when the global log level is INFO:

```TypeScript
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 1);
hilog.setMinLogLevel(hilog.LogLevel.WARN);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 2);
hilog.error(0x0001, 'testTag', 'this is an error level log, id: %{public}d', 3);
hilog.setMinLogLevel(hilog.LogLevel.DEBUG);
hilog.debug(0x0001, "testTag", 'this is a debug level log, id: %{public}d', 4);
hilog.info(0x0001, "testTag", 'this is an info level log, id: %{public}d', 5);
```

The first log is printed properly because the global log level is INFO.

After the minimum log level of the process is set to WARN, the second log does not meet the log level and fails to be printed. The third log is printed properly.

After the minimum log level of the process is set to DEBUG, the fourth log does not meet the global log level and fails to be printed. The fifth log is printed.

The log result is as follows:

```TypeScript
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 1
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  E     this is an error level log, id: 3
08-07 23:50:01.532   13694-13694   A00001/testTag                  com.example.hilogDemo  I     this is an info level log, id: 5
```
