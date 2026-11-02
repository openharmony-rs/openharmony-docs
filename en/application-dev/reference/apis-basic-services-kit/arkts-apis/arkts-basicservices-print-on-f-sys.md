# on (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## on('printerStateChange')

```TypeScript
function on(type: 'printerStateChange', callback: (state: PrinterState, info: PrinterInfo) => void): void
```

Registers a callback for the printer state change event. This API uses a callback to return the result. When the listener is no longer needed, call [print.off('printerStateChange')](arkts-basicservices-print-off-f-sys.md#offprinterstatechange) to unregister the callback. Otherwise, the callback may be continuously triggered, causing memory leak.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function on(type: 'printerStateChange', callback: (state: PrinterState, info: PrinterInfo) => void): void--><!--Device-print-function on(type: 'printerStateChange', callback: (state: PrinterState, info: PrinterInfo) => void): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'printerStateChange' | Yes | Listening type. The value is fixed at **'printerStateChange'**. |
| callback | (state: PrinterState, info: PrinterInfo) =&gt; void | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

<!--Del-->
**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.on('printerStateChange', (state: print.PrinterState, info: print.PrinterInfo) => {
    if (state === null || info === null) {
        console.error('printer state changed state is null or info is null');
        return;
    } else {
        console.info('on printer state changed, state : ' + JSON.stringify(state));
        console.info('on printer state changed, info : ' + JSON.stringify(info));
    }
});
```

<!--DelEnd-->


## on('jobStateChange')

```TypeScript
function on(type: 'jobStateChange', callback: (state: PrintJobState, job: PrintJob) => void): void
```

Registers a callback for the print job state change event. This API uses a callback to return the result. When the listener is no longer needed, call [print.off('jobStateChange')](arkts-basicservices-print-off-f-sys.md#offjobstatechange) to unregister the callback. Otherwise, the callback may be continuously triggered, causing memory leak.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function on(type: 'jobStateChange', callback: (state: PrintJobState, job: PrintJob) => void): void--><!--Device-print-function on(type: 'jobStateChange', callback: (state: PrintJobState, job: PrintJob) => void): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'jobStateChange' | Yes | Listening type. The value is fixed at **'jobStateChange'**. |
| callback | (state: PrintJobState, job: PrintJob) =&gt; void | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

<!--Del-->
**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.on('jobStateChange', (state: print.PrintJobState, job: print.PrintJob) => {
    console.info('onJobStateChange, state : ' + JSON.stringify(state) + ', job : ' + JSON.stringify(job));
});
```

<!--DelEnd-->


## on('extInfoChange')

```TypeScript
function on(type: 'extInfoChange', callback: (extensionId: string, info: string) => void): void
```

Registers a callback for the printer extension information change event. This API uses a callback to return the result. When the listener is no longer needed, call [print.off('extInfoChange')](arkts-basicservices-print-off-f-sys.md#offextinfochange) to unregister the callback. Otherwise, the callback may be continuously triggered, causing memory leak.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

<!--Device-print-function on(type: 'extInfoChange', callback: (extensionId: string, info: string) => void): void--><!--Device-print-function on(type: 'extInfoChange', callback: (extensionId: string, info: string) => void): void-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'extInfoChange' | Yes | Printer extension information changes. |
| callback | (extensionId: string, info: string) =&gt; void | Yes | Callback invoked when the printer extension information changes. **extensionId** indicates the printer extension ID, and **info** indicates the extension information content. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

<!--Del-->
**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';

print.on('extInfoChange', (extensionId: string, info: string) => {
    console.info('onExtInfoChange, extensionId : ' + JSON.stringify(extensionId) + ', info : ' + JSON.stringify(info));
});
```

<!--DelEnd-->
