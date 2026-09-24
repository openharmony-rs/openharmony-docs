# notifyPrintServiceEvent (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## notifyPrintServiceEvent

```TypeScript
function notifyPrintServiceEvent(event: ApplicationEvent): Promise<void>
```

Notifies the print service of the print application events. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [ApplicationEvent](arkts-basicservices-print-applicationevent-e.md) | Yes | Print application events. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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

let event : print.ApplicationEvent = print.ApplicationEvent.APPLICATION_CREATED;
print.notifyPrintServiceEvent(event).then(() => {
    console.info('notifyPrintServiceEvent success');
}).catch((error: BusinessError) => {
    console.error(`Failed to notify print service event. Code: ${error.code}, message: ${error.message}`);
});
```


<a id="notifyprintserviceevent-1"></a>

## notifyPrintServiceEvent

```TypeScript
function notifyPrintServiceEvent(event: ApplicationEvent, jobId: string): Promise<void>
```

Notifies the print service of the print application events. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [ApplicationEvent](arkts-basicservices-print-applicationevent-e.md) | Yes | Print application events. |
| jobId | string | Yes | ID of the print job. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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

let event : print.ApplicationEvent = print.ApplicationEvent.APPLICATION_CREATED;
let jobId : string = '1';
print.notifyPrintServiceEvent(event, jobId).then(() => {
    console.info('notifyPrintServiceEvent success');
}).catch((error: BusinessError) => {
    console.error(`Failed to notify print service event. Code: ${error.code}, message: ${error.message}`);
});
```
