# discoverUsbPrinters (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## discoverUsbPrinters

```TypeScript
function discoverUsbPrinters(): Promise<Array<PrinterInformation>>
```

Discovers USB printers. This API uses a promise to return the result.

**Since:** 18

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[PrinterInformation](arkts-basicservices-print-printerinformation-i.md)&gt;&gt; | Promise used to return the information about the discovered USB printers. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.discoverUsbPrinters().then((printers : print.PrinterInformation[]) => {
    console.info('discoverUsbPrinters data : ' + JSON.stringify(printers));
}).catch((error: BusinessError) => {
    console.error(`Failed to discover USB printers. Code: ${error.code}, message: ${error.message}`);
});
```
