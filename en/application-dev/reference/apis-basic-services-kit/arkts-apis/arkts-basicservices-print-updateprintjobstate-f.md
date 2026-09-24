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
- API versions 10 to 23: ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | ID of the print job. |
| state | [PrintJobState](arkts-basicservices-print-printjobstate-e.md) | Yes | Print job state. |
| subState | [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md) | Yes | Substate of the print job. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback to be invoked when the print job state is updated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application<br>**Applicable version:** 10 - 23 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

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


<a id="updateprintjobstate-1"></a>

## updatePrintJobState

```TypeScript
function updatePrintJobState(jobId: string, state: PrintJobState, subState: PrintJobSubState): Promise<void>
```

Updates the print job state. This API uses a promise to return the result.

**Since:** 24

**Required permissions:** 
- API version 24 and later: ohos.permission.MANAGE_PRINT_JOB or ohos.permission.ENTERPRISE_MANAGE_PRINT
- API versions 10 to 23: ohos.permission.MANAGE_PRINT_JOB

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
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application<br>**Applicable version:** 10 - 23 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

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
