# list (System API)

## Modules to Import

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## list

```TypeScript
function list(logType: string): LogEntry[]
```

Obtains the list of log files of the specified type in synchronous mode. This API accepts objects of the string type as input parameters and returns a list log files of the specified type.

**Since:** 10

**Required permissions:** ohos.permission.READ_HIVIEW_SYSTEM

**System capability:** SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| logType | string | Yes | Log type, for example, **HILOG**, **FAULTLOG**, **BETACLUB**, or **REMOTELOG**. |

**Return value:**

| Type | Description |
| --- | --- |
| [LogEntry](arkts-performanceanalysis-loglibrary-logentry-i-sys.md)[] | Array of log file objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |

**Examples**

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logObj = logLibrary.list('HILOG');
  // do something here.
} catch (error) {
  console.error(`error code: ${error?.code}, error msg: ${error?.message}`);
}
```
