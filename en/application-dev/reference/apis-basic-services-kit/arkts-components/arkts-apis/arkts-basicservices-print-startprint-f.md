# startPrint

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## startPrint

```TypeScript
function startPrint(job: PrintJobData): Promise<void>
```

Prints a file or binary data. This API uses a promise to return the result.

**Since:** 23

**Required permissions:** ohos.permission.PRINT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| job | [PrintJobData](arkts-basicservices-print-printjobdata-i.md) | Yes | Print job data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

let tempPath = '/data/storage/el2/base/haps/entry/files/note.jpg';
let file: fileIo.File;
file = fileIo.openSync(tempPath, 4);

let printJobData: print.PrintJobData = {
    printerId: 'printerId', // printer ID can be obtained from the on('printerChange') callback.
    jobName: 'jobName',
    documentFormat: print.PrintDocumentFormat.DOCUMENT_FORMAT_AUTO,
    docFlavor: print.DocFlavor.FILE_DESCRIPTOR,
    copyNumber: 1,
    isLandscape: false,
    colorMode: print.PrintColorMode.COLOR_MODE_MONOCHROME,
    duplexMode: print.PrintDuplexMode.DUPLEX_MODE_NONE,
    pageSize: {id: 'ISO_A4', name: 'ISO_A4', width: 8268, height: 11692},
    fdList: [file.fd],
};
print.startPrint(printJobData).then(() => {
    console.info('start print success');
}).catch((error: BusinessError) => {
    console.error(`Failed to startPrint. Code: ${error.code}, message: ${error.message}`);
})
```
