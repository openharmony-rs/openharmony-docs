# connectPrinter

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## connectPrinter

```TypeScript
function connectPrinter(printerId: string, callback: AsyncCallback<void>): void
```

Connects to a printer by printer ID. This API uses an asynchronous callback to return the result.

**Since:** 20

**Required permissions:** 
- API version 20 and later: ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT
- API versions 10 to 19: ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | string | Yes | Printer ID. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback to be invoked when a printer is connected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application<br>**Applicable version:** 10 - 19 |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// printer ID can be obtained from the on('printerChange') callback.
let printerId: string = 'printerId_32';
print.connectPrinter(printerId, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to connectPrinter. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('start connect Printer success');
    }
})
```


<a id="connectprinter-1"></a>

## connectPrinter

```TypeScript
function connectPrinter(printerId: string): Promise<void>
```

Connects to a printer by printer ID. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** 
- API version 20 and later: ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINT
- API versions 10 to 19: ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | string | Yes | Printer ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application<br>**Applicable version:** 10 - 19 |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// printer ID can be obtained from the on('printerChange') callback.
let printerId: string = 'printerId_32';
print.connectPrinter(printerId).then(() => {
    console.info('start connect Printer success');
}).catch((error: BusinessError) => {
    console.error(`Failed to connectPrinter. Code: ${error.code}, message: ${error.message}`);
})
```
