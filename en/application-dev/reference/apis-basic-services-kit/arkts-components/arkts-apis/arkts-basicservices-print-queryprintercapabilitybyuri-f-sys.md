# queryPrinterCapabilityByUri (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## queryPrinterCapabilityByUri

```TypeScript
function queryPrinterCapabilityByUri(printerUri: string, printerId: string): Promise<PrinterCapabilities>
```

Query printer capabilityies by printer uri.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerUri | string | Yes | Indicates the printer uri.<br>Printer URI in the process of connecting. |
| printerId | string | Yes | Indicates the printer ID.<br>Printer ID in the process of connecting. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PrinterCapabilities](arkts-basicservices-print-printercapabilities-i.md)&gt; | Promise that resolves with the printer capabilityies. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application. |
| [13100005](../errorcode-print.md#13100005-invalid-printer) | Can not find the printer in system. |

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
