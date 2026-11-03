# deletePrinterFromCups (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## deletePrinterFromCups

```TypeScript
function deletePrinterFromCups(printerName: string): Promise<void>
```

Deletes a printer from CUPS. This API uses an asynchronous callback to return the result. CUPS is the print service framework in the system, which is used to manage printers and print jobs.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

<!--Device-print-function deletePrinterFromCups(printerName: string): Promise<void>--><!--Device-print-function deletePrinterFromCups(printerName: string): Promise<void>-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerName | string | Yes | Printer name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |

<!--Del-->
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

<!--DelEnd-->
