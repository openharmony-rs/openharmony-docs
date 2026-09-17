# deletePrinterFromCups (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## deletePrinterFromCups

```TypeScript
function deletePrinterFromCups(printerName: string): Promise<void>
```

Delete a printer from cups.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerName | string | Yes | Indicates the printer name.<br>Printer name to be deleted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerName : string = 'testPrinterName';

print.deletePrinterFromCups(printerName).then(() => {
    console.info('deletePrinterFromCups success');
}).catch((error: BusinessError) => {
    console.error(`Failed to delete printer from cups. Code: ${error.code}, message: ${error.message}`);
});
```
