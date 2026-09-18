# savePdfFileJob (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## savePdfFileJob

```TypeScript
function savePdfFileJob(jobId: string, fd: number): Promise<void>
```

Save the pdf file for a print job.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | Indicates the print job ID.<br>The print job ID to which the file to be saved belongs. |
| fd | number | Yes | Indicates the fd.<br>Fd of the file to be saved. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| [13100006](../errorcode-print.md#13100006-invalid-print-job) | Invalid job ID. |
| 13100007 | Save file failed. |
