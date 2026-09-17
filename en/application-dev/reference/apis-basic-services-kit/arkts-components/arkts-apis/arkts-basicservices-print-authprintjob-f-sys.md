# authPrintJob (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## authPrintJob

```TypeScript
function authPrintJob(jobId: string, userName: string, password: string): Promise<boolean>
```

Authenticate a print job.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | Indicates the print job ID.<br>Job ID to be printed. |
| userName | string | Yes | Indicates the user name.<br>Indicates the user name. |
| password | string | Yes | Indicates the user password.<br>Indicates the user password. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| [13100006](../errorcode-print.md#13100006-invalid-print-job) | Can not find the print job. |
