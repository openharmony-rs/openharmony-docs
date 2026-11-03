# updatePrintJobState

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## updatePrintJobState

```TypeScript
function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState,
    callback: AsyncCallback<void>): void
```

Updates the print job state. This API uses an asynchronous callback to return the result.

**Since:** 24

**Required permissions:** 
- API version 24 and later: ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT
- API versions 10 to 23: N/A

<!--Device-print-function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState,    callback: AsyncCallback<void>): void--><!--Device-print-function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState,    callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | ID of the print job. |
| state | [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | Yes | Print job state. |
| subState | [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | Yes | Substate of the print job. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the print job state is updated successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Async] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the job ID from the onStartPrintJob callback of the PrintExtensionAbility.
let jobId : string = 'jobId';
let state : print.PrintJobState = print.PrintJobState.PRINT_JOB_PREPARE;
let subState : print.PrintJobSubState = print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS;
print.updatePrintJobState(jobId, state, subState, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to updatePrintJobState. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('updatePrintJobState success');
    }
})
```


## updatePrintJobState

```TypeScript
function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState): Promise<void>
```

Updates the print job state. This API uses a promise to return the result.

**Since:** 24

**Required permissions:** 
- API version 24 and later: ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT
- API versions 10 to 23: N/A

<!--Device-print-function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState): Promise<void>--><!--Device-print-function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState): Promise<void>-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | ID of the print job. |
| state | [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | Yes | Print job state. |
| subState | [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | Yes | Substate of the print job. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Async] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the job ID from the onStartPrintJob callback of the PrintExtensionAbility.
let jobId : string = 'jobId';
let state : print.PrintJobState = print.PrintJobState.PRINT_JOB_PREPARE;
let subState : print.PrintJobSubState = print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS;
print.updatePrintJobState(jobId, state, subState).then(() => {
    console.info('update print job state success');
}).catch((error: BusinessError) => {
    console.error(`Failed to updatePrintJobState. Code: ${error.code}, message: ${error.message}`);
})
```
