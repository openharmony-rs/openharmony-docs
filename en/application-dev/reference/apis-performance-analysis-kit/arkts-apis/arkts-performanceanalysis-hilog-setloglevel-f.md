# setLogLevel

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## setLogLevel

```TypeScript
function setLogLevel(level: LogLevel, prefer: PreferStrategy): void
```

Sets the minimum log level for the current application process.

Different preference strategies can be configured via the prefer parameter. If the strategy PREFER_CLOSE_LOG is selected, it is equivalent to calling the setMinLogLevel function.

> **Note:** 
> 
> This function does not take effect in debug-version applications.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-hilog-function setLogLevel(level: LogLevel, prefer: PreferStrategy): void--><!--Device-hilog-function setLogLevel(level: LogLevel, prefer: PreferStrategy): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [LogLevel](arkts-performanceanalysis-hilog-loglevel-e.md) | Yes | Log level. |
| prefer | [PreferStrategy](arkts-performanceanalysis-hilog-preferstrategy-e.md) | Yes | Preference strategy. |
