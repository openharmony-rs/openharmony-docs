# queryPrintJobList (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryPrintJobList

```TypeScript
function queryPrintJobList(callback: AsyncCallback<Array<PrintJob>>): void
```

Queries all print jobs. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[PrintJob](arkts-basicservices-print-printjob-i.md)&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryPrintJobList((error: BusinessError, printJobs : print.PrintJob[]) => {
    if (error) {
        console.error(`Failed to query print job list. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('queryPrintJobList success, data : ' + JSON.stringify(printJobs));
    }
});
```


<a id="queryprintjoblist-1"></a>

## queryPrintJobList

```TypeScript
function queryPrintJobList(): Promise<Array<PrintJob>>
```

Queries all print jobs. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PrintJob](arkts-basicservices-print-printjob-i.md)&gt;&gt; | Promise used to return a list of all print jobs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryPrintJobList().then((printJobs : print.PrintJob[]) => {
    console.info('queryPrintJobList success, data : ' + JSON.stringify(printJobs));
}).catch((error: BusinessError) => {
    console.error(`Failed to query print job list. Code: ${error.code}, message: ${error.message}`);
});
```
