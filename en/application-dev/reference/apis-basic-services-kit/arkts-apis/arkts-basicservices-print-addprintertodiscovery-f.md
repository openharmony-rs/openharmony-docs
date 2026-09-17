# addPrinterToDiscovery

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## addPrinterToDiscovery

```TypeScript
function addPrinterToDiscovery(printerInformation: PrinterInformation): Promise<void>
```

Adds a printer to the printer discovery list. This API uses a promise to return the result.

**Since:** 14

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerInformation | [PrinterInformation](arkts-basicservices-print-printerinformation-i.md) | Yes | The added printer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInformation : print.PrinterInformation = {
    printerId : 'testPrinterId', // printer ID can be obtained from the on('printerChange') callback.
    printerName : 'testPrinterName',
    printerStatus : 0,
    description : 'testDesc',
    uri : 'testUri',
    printerMake : 'testPrinterMake',
    options : 'testOps'
};
print.addPrinterToDiscovery(printerInformation).then(() => {
    console.info('addPrinterToDiscovery success');
}).catch((error: BusinessError) => {
    console.error(`Failed to addPrinterToDiscovery. Code: ${error.code}, message: ${error.message}`);
})
```
