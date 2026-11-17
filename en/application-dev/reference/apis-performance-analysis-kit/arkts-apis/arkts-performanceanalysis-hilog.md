# @ohos.hilog(HiLOG Logging)

**Since:** 7

<!--Device-unnamed-declare namespace hilog--><!--Device-unnamed-declare namespace hilog-End-->

**System capability:** SystemCapability.HiviewDFX.HiLog

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [clean](arkts-performanceanalysis-hilog-clean-f.md#clean-1) | Deletes all hilog logs in the sandbox. |
| [debug](arkts-performanceanalysis-hilog-debug-f.md#debug-1) | Prints a DEBUG-level log. |
| [error](arkts-performanceanalysis-hilog-error-f.md#error-1) | Prints an ERROR-level log. |
| [fatal](arkts-performanceanalysis-hilog-fatal-f.md#fatal-1) | Prints a FATAL-level log. |
| [flush](arkts-performanceanalysis-hilog-flush-f.md#flush-1) | Flushes hilog logs in the sandbox to ensure logs are persisted to disk. |
| [getLogFile](arkts-performanceanalysis-hilog-getlogfile-f.md#getlogfile-1) | Returns hilog sandbox log files that have been modified within the specified number of seconds. |
| [getOutputDir](arkts-performanceanalysis-hilog-getoutputdir-f.md#getoutputdir-1) | Returns the path of hilog logs in the sandbox. If the hilog output type is DEFAULT, an empty string is returned. |
| [getOutputType](arkts-performanceanalysis-hilog-getoutputtype-f.md#getoutputtype-1) | Gets the current hilog output type. |
| [info](arkts-performanceanalysis-hilog-info-f.md#info-1) | Prints an INFO-level log. |
| [isLoggable](arkts-performanceanalysis-hilog-isloggable-f.md#isloggable-1) | Called before printing a log to check whether a log with the specified domain identifier, tag, and level can be printed. |
| [setLogLevel](arkts-performanceanalysis-hilog-setloglevel-f.md#setloglevel-1) | Sets the minimum log level for the current application process. |
| [setMinLogLevel](arkts-performanceanalysis-hilog-setminloglevel-f.md#setminloglevel-1) | Sets the minimum log level for application log printing to filter out lower-level logs. Used when optimizing application performance or reducing interference from low-value logs to avoid redundant logs. |
| [setOutputType](arkts-performanceanalysis-hilog-setoutputtype-f.md#setoutputtype-1) | Sets the hilog output type. |
| [setOutputTypeByDomainID](arkts-performanceanalysis-hilog-setoutputtypebydomainid-f.md#setoutputtypebydomainid-1) | Sets the hilog output type and configures the domain ID list for output. You can choose to output only the domain IDs in the list, or exclude the domain IDs in the list from output. |
| [warn](arkts-performanceanalysis-hilog-warn-f.md#warn-1) | Prints a WARN-level log. |

### Enums

| Name | Description |
| --- | --- |
| [LogLevel](arkts-performanceanalysis-hilog-loglevel-e.md) | Log level. |
| [OutputType](arkts-performanceanalysis-hilog-outputtype-e.md) | Enum values for hilog output types. DEFAULT and CONSOLE_ONLY are suitable for console-only output scenarios, PRIVATE_SANDBOX_ONLY is suitable for privacy log storage, SHARE_SANDBOX_ONLY is suitable for scenarios requiring cloud log collection, PRIVATE_SANDBOX_WITH_CONSOLE and SHARE_SANDBOX_WITH_CONSOLE are suitable for scenarios requiring both console output and sandbox storage. |
| [PreferStrategy](arkts-performanceanalysis-hilog-preferstrategy-e.md) | Preference strategy. |
