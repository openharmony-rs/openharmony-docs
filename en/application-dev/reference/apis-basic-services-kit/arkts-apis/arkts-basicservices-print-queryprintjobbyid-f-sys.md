# queryPrintJobById (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryPrintJobById

```TypeScript
function queryPrintJobById(jobId: string, callback: AsyncCallback<PrintJob>): void
```

Queries a print job by ID. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | ID of the print job. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[PrintJob](arkts-basicservices-print-printjob-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.queryPrintJobById(jobId, (error: BusinessError, printJob : print.PrintJob) => {
    if (error) {
        console.error(`Failed to query print job by id. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('queryPrintJobById success, data : ' + JSON.stringify(printJob));
    }
});
```

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.queryPrintJobById(jobId).then((printJob : print.PrintJob) => {
    console.info('queryPrintJobById data : ' + JSON.stringify(printJob));
}).catch((error: BusinessError) => {
    console.error(`Failed to query print job by id. Code: ${error.code}, message: ${error.message}`);
});
```


## queryPrintJobById

```TypeScript
function queryPrintJobById(jobId: string): Promise<PrintJob>
```

Queries a print job by ID. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | ID of the print job. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PrintJob](arkts-basicservices-print-printjob-i.md)&gt; | Promise used to return the queried print job. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

See [queryPrintJobById](#queryprintjobbyid)
