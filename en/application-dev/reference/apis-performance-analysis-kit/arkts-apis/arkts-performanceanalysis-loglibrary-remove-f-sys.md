# remove (System API)

## Modules to Import

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## remove

```TypeScript
function remove(logType: string, logName: string): void
```

Deletes log files of the specified type in synchronous mode.

**Since:** 10

**Required permissions:** ohos.permission.WRITE_HIVIEW_SYSTEM

**System capability:** SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| logType | string | Yes | Log type, for example, **FAULTLOG**, **BETACLUB**, or **REMOTELOG**. |
| logName | string | Yes | Log file name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [21300001](../errorcode-loglibrary-sys.md#21300001-specified-file-not-exist) | Source file does not exist |

**Examples**

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logObj = logLibrary.list('FAULTLOG');
  if (logObj.length > 0) {
    logLibrary.remove('FAULTLOG', logObj[0].name);
  }
} catch (error) {
  console.error(`error code: ${error?.code}, error msg: ${error?.message}`);
}
```
