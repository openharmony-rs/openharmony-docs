# addPrinterToCups (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## addPrinterToCups

```TypeScript
function addPrinterToCups(printerUri: string, printerName: string, printerMake: string): Promise<boolean>
```

Add a printer to cups.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerUri | string | Yes | Indicates the printer uri.<br>Printer URI in the process of connecting. |
| printerName | string | Yes | Indicates the printer name.<br>Printer name in the process of connecting. |
| printerMake | string | Yes | Indicates the printer make.<br>Printer make in the process of connecting. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| [13100003](../errorcode-print.md#13100003-print-service-exception) | Add a printer to cups failed. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain printerUri from PrinterInformation returned by the discoverUsbPrinters API.
let printerUri : string = 'testPrinterUri';
let printerName : string = 'testPrinterName';
let printerMake : string = 'testPrinterMake';

print.addPrinterToCups(printerUri, printerName, printerMake).then((result: boolean) => {
    console.info('addPrinterToCups success' + JSON.stringify(result));
}).catch((error: BusinessError) => {
    console.error(`Failed to add printer to cups. Code: ${error.code}, message: ${error.message}`);
});
```
