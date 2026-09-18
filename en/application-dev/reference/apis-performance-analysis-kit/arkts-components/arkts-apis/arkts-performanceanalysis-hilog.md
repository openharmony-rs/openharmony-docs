# @ohos.hilog

The HiLog subsystem allows your applications or services to output logs based on the specified type, level, and format string. Such logs help you learn the running status of applications and better debug programs.

**Since:** 7

**System capability:** SystemCapability.HiviewDFX.HiLog

## Modules to Import

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [clean](arkts-performanceanalysis-hilog-clean-f.md) | Delete all hilog logs in the sandbox. |
| [debug](arkts-performanceanalysis-hilog-debug-f.md) | Prints DEBUG logs. |
| [error](arkts-performanceanalysis-hilog-error-f.md) | Prints ERROR logs. |
| [fatal](arkts-performanceanalysis-hilog-fatal-f.md) | Prints FATAL logs. |
| [flush](arkts-performanceanalysis-hilog-flush-f.md) | Flush hilog logs in the sandbox. |
| [getLogFile](arkts-performanceanalysis-hilog-getlogfile-f.md) | Returns the list of hilog log file paths in the sandbox for the specified recent time period. |
| [getOutputDir](arkts-performanceanalysis-hilog-getoutputdir-f.md) | Returns the directory path of hilog logs in the sandbox. If the output type of hilog is DEFAULT, an empty string is returned. |
| [getOutputType](arkts-performanceanalysis-hilog-getoutputtype-f.md) | Returns the current output type of hilog. |
| [info](arkts-performanceanalysis-hilog-info-f.md) | Prints INFO logs. |
| [isLoggable](arkts-performanceanalysis-hilog-isloggable-f.md) | Checks whether logs are printable based on the specified service domain, log tag, and log level. |
| [setLogLevel](arkts-performanceanalysis-hilog-setloglevel-f.md) | Sets the minimum log level of the current application process. |
| [setMinLogLevel](arkts-performanceanalysis-hilog-setminloglevel-f.md) | Sets the minimum log level. |
| [setOutputType](arkts-performanceanalysis-hilog-setoutputtype-f.md) | Sets the output type of hilog. |
| [setOutputTypeByDomainID](arkts-performanceanalysis-hilog-setoutputtypebydomainid-f.md) | Sets the output type for hilog for the domainID list. |
| [warn](arkts-performanceanalysis-hilog-warn-f.md) | Prints WARN logs. |

### Enums

| Name | Description |
| --- | --- |
| [LogLevel](arkts-performanceanalysis-hilog-loglevel-e.md) | Enumerates the log levels. |
| [OutputType](arkts-performanceanalysis-hilog-outputtype-e.md) | Enumerates output type of hilog. |
| [PreferStrategy](arkts-performanceanalysis-hilog-preferstrategy-e.md) | Enumerates the preference strategies. |
