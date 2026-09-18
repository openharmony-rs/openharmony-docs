# copy (System API)

## Modules to Import

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## copy

```TypeScript
function copy(logType: string, logName: string, dest: string): Promise<void>
```

Copies log files of the specified type to the target application directory. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.READ_HIVIEW_SYSTEM

**System capability:** SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| logType | string | Yes | Log type, for example, **HILOG**, **FAULTLOG**, **BETACLUB**, or **REMOTELOG**. |
| logName | string | Yes | Log file name. |
| dest | string | Yes | Target directory. Enter the relative path of the directory. If this parameter is specified, log files will be saved to the **hiview/dest** folder in the application cache path, that is, **../cache/hiview/dest**. You can enter a multi-level directory.<br>If you leave this parameter empty, log files will be saved to the root directory, that is, the **hiview** folder in the application cache path. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. Depending on whether the operation is successful, you can use the **then()** or **catch()** method to process the callback. |

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
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logObj = logLibrary.list('HILOG');
  if (logObj.length > 0) {
    logLibrary.copy('HILOG', logObj[0].name, ''
    ).then(
      (val) => {
        // do something here.
      }
    ).catch(
      (err: BusinessError) => {
        // do something here.
      }
    )
  }
} catch (error) {
    console.error(`error code: ${error?.code}, error msg: ${error?.message}`);
}
```

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logObj = logLibrary.list('HILOG');
  if (logObj.length > 0) {
    logLibrary.copy('HILOG', logObj[0].name, 'dir1', (error, val) => {
      if (val === undefined) {
        // copy failed.
      } else {
        // copy success.
      }
    });
  }
} catch (error) {
    console.error(`error code: ${error?.code}, error msg: ${error?.message}`);
}
```


## copy

```TypeScript
function copy(logType: string, logName: string, dest: string, callback: AsyncCallback<void>): void
```

Copies log files of the specified type to the target application directory. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.READ_HIVIEW_SYSTEM

**System capability:** SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| logType | string | Yes | Log type, for example, **HILOG**, **FAULTLOG**, **BETACLUB**, or **REMOTELOG**. |
| logName | string | Yes | Log file name. |
| dest | string | Yes | Target directory. Enter the relative path of the directory. If this parameter is specified, log files will be saved to the **hiview/dest** folder in the application cache path, that is, **../cache/hiview/dest**. You can enter a multi-level directory.<br>If you leave this parameter empty, log files will be saved to the root directory, that is, the **hiview** folder in the application cache path. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to process the received return value. The value **0** indicates that the operation is successful, and any other value indicates that the operation has failed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [21300001](../errorcode-loglibrary-sys.md#21300001-specified-file-not-exist) | Source file does not exist |

**Examples**

See [copy](#copy)
