# startGettingPrintFile (System API)

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## startGettingPrintFile

```TypeScript
function startGettingPrintFile(jobId: string, printAttributes: PrintAttributes, fd: number,
    onFileStateChanged: Callback<PrintFileCreationState>): void
```

Starts to obtain the print file. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_PRINT_JOB

**System capability:** SystemCapability.Print.PrintFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jobId | string | Yes | ID of the print job. |
| printAttributes | [PrintAttributes](arkts-basicservices-print-printattributes-i.md) | Yes | Print attributes. |
| fd | number | Yes | File descriptor. |
| onFileStateChanged | [Callback](arkts-basicservices-base-callback-i.md)&lt;[PrintFileCreationState](arkts-basicservices-print-printfilecreationstate-e.md)&gt; | Yes | Callback for updating the file state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | not system application |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Examples**

```TypeScript
import { print } from '@kit.BasicServicesKit';

let jobId : string = '1';
class MyPrintAttributes implements print.PrintAttributes {
    copyNumber?: number;
    pageRange?: print.PrintPageRange;
    pageSize?: print.PrintPageSize | print.PrintPageType;
    directionMode?: print.PrintDirectionMode;
    colorMode?: print.PrintColorMode;
    duplexMode?: print.PrintDuplexMode;
}

class MyPrintPageRange implements print.PrintPageRange {
    startPage?: number;
    endPage?: number;
    pages?: Array<number>;
}

let printAttributes = new MyPrintAttributes();
printAttributes.copyNumber = 2;
printAttributes.pageRange = new MyPrintPageRange();
printAttributes.pageRange.pages = [1, 3];
printAttributes.pageSize = print.PrintPageType.PAGE_ISO_A3;
printAttributes.directionMode = print.PrintDirectionMode.DIRECTION_MODE_AUTO;
printAttributes.colorMode = print.PrintColorMode.COLOR_MODE_MONOCHROME;
printAttributes.duplexMode = print.PrintDuplexMode.DUPLEX_MODE_NONE;

// fd can be obtained through file operations such as fs.open.
let fd : number = 1;
print.startGettingPrintFile(jobId, printAttributes, fd, (state: print.PrintFileCreationState) => {
    console.info('onFileStateChanged success, data : ' + JSON.stringify(state));
});
```
