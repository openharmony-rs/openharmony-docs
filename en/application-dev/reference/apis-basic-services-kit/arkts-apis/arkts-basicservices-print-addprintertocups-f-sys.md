# addPrinterToCups (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## addPrinterToCups

```TypeScript
function addPrinterToCups(printerUri: string, printerName: string, printerMake: string): Promise<boolean>
```

Adds a printer to CUPS. This API uses an asynchronous callback to return the result. CUPS is the print service framework in the system, which is used to manage printers and print jobs.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

<!--Device-print-function addPrinterToCups(printerUri: string, printerName: string, printerMake: string): Promise<boolean>--><!--Device-print-function addPrinterToCups(printerUri: string, printerName: string, printerMake: string): Promise<boolean>-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerUri | string | Yes | Printer URI, which can be obtained by calling [PrinterInformation](arkts-basicservices-print-printerinformation-i.md). |
| printerName | string | Yes | Printer name. |
| printerMake | string | Yes | Printer brand. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| [13100003](../errorcode-print.md#13100003-print-service-exception) | Add a printer to cups failed. |

<!--Del-->
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

<!--DelEnd-->
