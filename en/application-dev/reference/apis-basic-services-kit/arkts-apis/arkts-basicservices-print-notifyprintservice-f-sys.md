# notifyPrintService (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## notifyPrintService('spooler_closed_for_cancelled' | 'spooler_closed_for_started')

```TypeScript
function notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started',
    callback: AsyncCallback<void>): void
```

Notifies the print service that the print preview page is closed. This API uses an asynchronous callback to return the result. This method is used to notify the print service to perform clearance, exit, and other operations after the print preview page is closed.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started',    callback: AsyncCallback<void>): void--><!--Device-print-function notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started',    callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | ID of the created print job. |
| type | 'spooler_closed_for_cancelled' &#124; 'spooler_closed_for_started' | Yes | Type of information that causes closing of the print preview page. **'spooler_closed_for_cancelled'** indicates that the print preview page is closed because the current print job is canceled. **'spooler_closed_for_started'** indicates that the print preview page is closed because the print job is successfully delivered. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the information about closing the print preview page is successfully sent to the printing service, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Async] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.notifyPrintService(jobId, 'spooler_closed_for_started', (error: BusinessError) => {
    if (error) {
        console.error(`Failed to notify print service. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('notifyPrintService success');
    }
});
```

<!--DelEnd-->


## notifyPrintService('spooler_closed_for_cancelled' | 'spooler_closed_for_started')

```TypeScript
function notifyPrintService(jobId: string,
    type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started'): Promise<void>
```

Notifies the print service that the print preview page is closed. This API uses a promise to return the result. This method is used to notify the print service to perform clearance, exit, and other operations after the print preview page is closed.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function notifyPrintService(jobId: string,    type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started'): Promise<void>--><!--Device-print-function notifyPrintService(jobId: string,    type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started'): Promise<void>-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | ID of the created print job. |
| type | 'spooler_closed_for_cancelled' &#124; 'spooler_closed_for_started' | Yes | Type of information that causes closing of the print preview page. **'spooler_closed_for_cancelled'** indicates that the print preview page is closed because the current print job is canceled. **'spooler_closed_for_started'** indicates that the print preview page is closed because the print job is successfully delivered. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Async] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.notifyPrintService(jobId, 'spooler_closed_for_started').then(() => {
    console.info('notifyPrintService success');
}).catch((error: BusinessError) => {
    console.error(`Failed to notify print service. Code: ${error.code}, message: ${error.message}`);
});
```

<!--DelEnd-->
