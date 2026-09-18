# removePrinterFromDiscovery

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## removePrinterFromDiscovery

```TypeScript
function removePrinterFromDiscovery(printerId: string): Promise<void>
```

Removes a printer from the printer discovery list. This API uses a promise to return the result.

**Since:** 14

**Required permissions:** ohos.permission.PRINT

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerId | string | Yes | Printer to remove. |

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

// printer ID can be obtained from the on('printerChange') callback.
let printerId : string = 'testPrinterId';
print.removePrinterFromDiscovery(printerId).then(() => {
    console.info('removePrinterFromDiscovery success');
}).catch((error: BusinessError) => {
    console.error(`Failed to removePrinterFromDiscovery. Code: ${error.code}, message: ${error.message}`);
})
```
