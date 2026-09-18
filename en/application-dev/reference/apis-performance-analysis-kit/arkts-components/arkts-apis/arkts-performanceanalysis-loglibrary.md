# @ohos.logLibrary

The **logLibrary** module provides APIs for obtaining various system maintenance and test logs.

**Since:** 10

**System capability:** SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [copy](arkts-performanceanalysis-loglibrary-copy-f-sys.md) | Copies log files of the specified type to the target application directory. This API uses a promise to return the result. |
| [copy](arkts-performanceanalysis-loglibrary-copy-f-sys.md) | Copies log files of the specified type to the target application directory. This API uses an asynchronous callback to return the result. |
| [list](arkts-performanceanalysis-loglibrary-list-f-sys.md) | Obtains the list of log files of the specified type in synchronous mode. This API accepts objects of the string type as input parameters and returns a list log files of the specified type. |
| [move](arkts-performanceanalysis-loglibrary-move-f-sys.md) | Moves log files of the specified type to the target application directory. This API uses a promise to return the result. |
| [move](arkts-performanceanalysis-loglibrary-move-f-sys.md) | Moves log files of the specified type to the target application directory. This API uses an asynchronous callback to return the result. |
| [remove](arkts-performanceanalysis-loglibrary-remove-f-sys.md) | Deletes log files of the specified type in synchronous mode. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [LogEntry](arkts-performanceanalysis-loglibrary-logentry-i-sys.md) | Defines a **LogEntry** object. |
<!--DelEnd-->
