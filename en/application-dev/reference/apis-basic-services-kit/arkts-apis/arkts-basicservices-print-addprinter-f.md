# addPrinter

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## addPrinter

```TypeScript
function addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise<boolean>
```

Add a printer to system.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINTER_DRIVER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerName | string | Yes | Indicates the printer name.<br>Name of the printer to be added. |
| uri | string | Yes | Indicates the printer uri.<br>Uri of the printer to be added. |
| ppdName | string | No | Indicates the ppd name.<br>Ppd name of the printer to be added. |
| options | string | No | Indicates the options.<br>Optional parameters when adding a printer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [13100003](../errorcode-print.md#13100003-print-service-exception) | Add the printer to system failed. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerName : string = 'printerName';
let uri : string = 'uri';
let ppdName : string = 'ppdName';
print.addPrinter(printerName, uri, ppdName).then(() => {
    console.info('add printer success');
}).catch((error: BusinessError) => {
    console.error(`Failed to addPrinter. Code: ${error.code}, message: ${error.message}`);
})
```
