# addPrinter

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## addPrinter

```TypeScript
function addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise<boolean>
```

Adds a printer to the system. This API uses a promise to return the result. This API is intended for scenarios where printers or scanners need to be managed, such as the management of the printer drivers, printing management software, third-party printing management software, and cloud printing.

**Since:** 24

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB or ohos.permission.PRINTER_DRIVER

**Model restriction:** This API can be used only in the stage model.

<!--Device-print-function addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise<boolean>--><!--Device-print-function addPrinter(printerName: string, uri: string, ppdName?: string, options?: string): Promise<boolean>-End-->

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| printerName | string | Yes | Printer name. |
| uri | string | Yes | Printer URI. |
| ppdName | string | No | PPD driver file name of the printer in the file system. The name is generated after the driver is installed on the device, which is in the format of **package name_module name_file name**. For details about the name, contact the driver vendor. This parameter is passed when a specific PPD driver file needs to be specified. If this parameter is not passed, the system automatically matches a PPD driver file. |
| options | string | No | JSON object string, which indicates the printer option parameter. This is a reserved field, which is not used currently. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result indicating whether the printer is successfully added. **true** if the operation is successful, and **false** otherwise. |

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
