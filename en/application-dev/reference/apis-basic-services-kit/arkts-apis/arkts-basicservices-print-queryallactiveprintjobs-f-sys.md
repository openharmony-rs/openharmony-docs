# queryAllActivePrintJobs (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryAllActivePrintJobs

```TypeScript
function queryAllActivePrintJobs(): Promise<PrintJob[]>
```

Queries all active print jobs. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PrintJob](arkts-basicservices-print-printjob-i.md)[]&gt; | Promise used to return a list of all active print jobs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllActivePrintJobs().then((printJobs : print.PrintJob[]) => {
    console.info('queryAllActivePrintJobs success, data : ' + JSON.stringify(printJobs));
}).catch((error: BusinessError) => {
    console.error(`Failed to query all active print jobs. Code: ${error.code}, message: ${error.message}`);
});
```
