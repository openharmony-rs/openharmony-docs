# queryPrinterCapabilityByUri (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryPrinterCapabilityByUri

```TypeScript
function queryPrinterCapabilityByUri(printerUri: string, printerId: string): Promise<PrinterCapabilities>
```

Queries the printer capability by the printer URI. This API uses a promise to return the result. This API can be used to query the capabilities of a printer when the printer URI is known but the printer is not registered locally. It can also be used to discover the capabilities of a USB printer.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

<!--Device-print-function queryPrinterCapabilityByUri(printerUri: string, printerId: string): Promise<PrinterCapabilities>--><!--Device-print-function queryPrinterCapabilityByUri(printerUri: string, printerId: string): Promise<PrinterCapabilities>-End-->

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerUri | string | Yes | Printer URI, which can be obtained by calling [PrinterInformation](arkts-basicservices-print-printerinformation-i.md). |
| printerId | string | Yes | Printer ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PrinterCapabilities](arkts-basicservices-print-printercapabilities-i.md)&gt; | Promise used to return the printer capabilities, which are used to obtain the functions and configuration options supported by the printer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| [13100005](../errorcode-print.md#13100005-invalid-printer) | Can not find the printer in system. |

<!--Del-->
**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain printerUri from PrinterInformation returned by the discoverUsbPrinters API.
let printerUri : string = 'testPrinterUri';
let printerId : string = 'testPrinterId';
print.queryPrinterCapabilityByUri(printerUri, printerId).then((capabilities: print.PrinterCapabilities) => {
    console.info('queryPrinterCapabilityByUri success' + JSON.stringify(capabilities));
}).catch((error: BusinessError) => {
    console.error(`Failed to query printer capability by uri. Code: ${error.code}, message: ${error.message}`);
});
```

<!--DelEnd-->
