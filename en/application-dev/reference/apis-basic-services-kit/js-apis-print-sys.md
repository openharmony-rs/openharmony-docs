# @ohos.print (Print) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=a077482f26289b96749dbeb1a0c6856695ebea0a translatedAt=2026-09-01T04:04:12.234Z pushedAt=2026-09-05T07:27:32.944Z -->

This module provides the system APIs for print management, including querying printer extension services, discovering and managing printers, setting printer preferences and the default printer, managing print jobs, and listening for state change events.

> **NOTE**
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.print (Print)](js-apis-print.md).

## Modules to Import

```ts
import { print } from '@kit.BasicServicesKit';
```

## PrinterExtensionInfo

Defines the printer extension information.

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Attributes**

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| extensionId | string | No | No | Printer extension ID. |
| vendorId | string | No| No| Vendor ID of the printer extension.|
| vendorName | string | No| No| Vendor name of the printer extension.|
| vendorIcon | number | No | No | Vendor icon resource ID. |
| version | string | No| No| Version of the printer extension.|

## print.queryAllPrinterExtensionInfos

queryAllPrinterExtensionInfos(callback: AsyncCallback&lt;Array&lt;PrinterExtensionInfo&gt;&gt;): void

Obtains the information of all installed printer extensions. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;[PrinterExtensionInfo](#printerextensioninfo)&gt;&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrinterExtensionInfos((error: BusinessError, extensionInfos: print.PrinterExtensionInfo[]) => {
    if (error) {
        console.error(`Failed to query all printer extension infos. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('queryAllPrinterExtensionInfos success ' + JSON.stringify(extensionInfos));
    }
});
```

## print.queryAllPrinterExtensionInfos

queryAllPrinterExtensionInfos(): Promise&lt;Array&lt;PrinterExtensionInfo&gt;&gt;

Obtains the information of all installed printer extensions. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[PrinterExtensionInfo](#printerextensioninfo)&gt;&gt; | Promise used to return the information of all installed printer extensions.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrinterExtensionInfos().then((extensionInfos: print.PrinterExtensionInfo[]) => {
    console.info('queryAllPrinterExtensionInfos success ' + JSON.stringify(extensionInfos));
    // ...
}).catch((error: BusinessError) => {
    console.error(`Failed to query all printer extension infos. Code: ${error.code}, message: ${error.message}`);
});
```

## print.disconnectPrinter

disconnectPrinter(printerId: string, callback: AsyncCallback&lt;void&gt;): void

Disconnects from the specified printer. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes | Printer ID. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked after the connection to the specified printer is asynchronously disconnected. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.disconnectPrinter(printerId, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to disconnect printer. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('start disconnect Printer success');
    }
});
```

## print.disconnectPrinter

disconnectPrinter(printerId: string): Promise&lt;void&gt;

Disconnects from the specified printer. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes | Printer ID. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the printer is successfully disconnected, **resolve** returns a value. If the printer fails to be disconnected, **reject** return an error message.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.disconnectPrinter(printerId).then(() => {
    console.info('start disconnect Printer success');
}).catch((error: BusinessError) => {
    console.error(`Failed to disconnect printer. Code: ${error.code}, message: ${error.message}`);
});
```

## print.queryPrinterCapability

queryPrinterCapability(printerId: string, callback: AsyncCallback&lt;void&gt;): void

Queries the printer capability. This API uses an asynchronous callback to return the result. The query result can be obtained from **PrinterInfo.capability** in the [on('printerStateChange')](#printon) event callback.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes | Printer ID. |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.queryPrinterCapability(printerId, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to query printer capability. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('start query Printer Capability success');
    }
});
```

## print.queryPrinterCapability

queryPrinterCapability(printerId: string): Promise&lt;void&gt;

Queries the printer capability. This API uses a promise to return the result. The query result can be obtained from **PrinterInfo.capability** in the [on('printerStateChange')](#printon) event callback.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes | Printer ID. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the printer capability is queried successfully, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId: string = 'printerId_32';
print.queryPrinterCapability(printerId).then(() => {
    console.info('start query Printer success');
}).catch((error: BusinessError) => {
    console.error(`Failed to query printer capability. Code: ${error.code}, message: ${error.message}`);
});
```

## print.startPrintJob

startPrintJob(jobInfo: PrintJob, callback: AsyncCallback&lt;void&gt;): void

Starts a print job. This API uses an asynchronous callback to return the result. You can listen for the [on('jobStateChange')](#printon-1) event to obtain the print job state change.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | Yes | Print job information, which is used to specify the detailed configuration of the print job to be executed, including the file list, task ID, job ID, and print parameters. |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobInfo : print.PrintJob = {
    fdList : [44, 45], // fd in fdList can be obtained through file operations such as fs.open to get the file descriptor.
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : print.PrintJobState.PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : print.PrintColorMode.COLOR_MODE_COLOR,
    duplexMode : print.PrintDuplexMode.DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.startPrintJob(jobInfo, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to start print job. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('start Print Job success');
    }
});
```

## print.startPrintJob

startPrintJob(jobInfo: PrintJob): Promise&lt;void&gt;

Starts a print job. This API uses a promise to return the result. You can listen for the [on('jobStateChange')](#printon-1) event to obtain the print job state change.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | Yes | Print job information, which is used to specify the detailed configuration of the print job to be executed, including the file list, task ID, printer ID, and print parameters. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the print job is started successfully, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobInfo : print.PrintJob = {
    fdList : [44, 45], // fd in fdList can be obtained through file operations such as fs.open to get the file descriptor.
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : print.PrintJobState.PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : print.PrintColorMode.COLOR_MODE_COLOR,
    duplexMode : print.PrintDuplexMode.DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.startPrintJob(jobInfo).then(() => {
    console.info('start Print success');
}).catch((error: BusinessError) => {
    console.error(`Failed to start print job. Code: ${error.code}, message: ${error.message}`);
});
```

## print.cancelPrintJob

cancelPrintJob(jobId: string, callback: AsyncCallback&lt;void&gt;): void

Cancels a print job that has been sent to the printer. This API uses an asynchronous callback to return the result. Only an ongoing print job can be canceled. Calling this API for a nonexistent or completed job returns an error.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes | ID of the print job sent to the printer. |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '121212';
print.cancelPrintJob(jobId, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to cancel print job. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('cancelPrintJob success');
    }
});
```

## print.cancelPrintJob

cancelPrintJob(jobId: string): Promise&lt;void&gt;

Cancels a print job that has been sent to the printer. This API uses a promise to return the result. Only an ongoing print job can be canceled. Calling this API for a nonexistent or completed job returns an error.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes | ID of the print job sent to the printer. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the print job is successfully canceled, **resolve** returns a value. If the print job fails to be canceled, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '121212';
print.cancelPrintJob(jobId).then(() => {
    console.info('cancelPrintJob success');
}).catch((error: BusinessError) => {
    console.error(`Failed to cancel print job. Code: ${error.code}, message: ${error.message}`);
});
```

## print.restartPrintJob<sup>20+</sup>

restartPrintJob(jobId: string): Promise&lt;void&gt;

Restarts a failed print job. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes | ID of a previous print job. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the print job is successfully re-executed, **resolve** returns a value. If the print job fails to be re-executed, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '121212';
print.restartPrintJob(jobId).then(() => {
    console.info('restartPrintJob success');
}).catch((error: BusinessError) => {
    console.error(`Failed to restart print job. Code: ${error.code}, message: ${error.message}`);
});
```

## print.requestPrintPreview

requestPrintPreview(jobInfo: PrintJob, callback: Callback&lt;number&gt;): void

Requests print preview data. This API uses a callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | Yes | Print job information, which is used to specify the detailed configuration of the print job to be previewed. |
| callback | Callback&lt;number&gt; | Yes | Callback used to return the preview result, which is of the number type. The value **0** indicates that the request is successful, and a non-zero value is the error code of the failure cause. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';

let jobInfo : print.PrintJob = {
    fdList : [44, 45], // fd in fdList can be obtained through file operations such as fs.open to get the file descriptor.
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : print.PrintJobState.PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : print.PrintColorMode.COLOR_MODE_COLOR,
    duplexMode : print.PrintDuplexMode.DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.requestPrintPreview(jobInfo, (num : number) => {
    console.info('requestPrintPreview success, num : ' + JSON.stringify(num));

});
```

## print.requestPrintPreview

requestPrintPreview(jobInfo: PrintJob): Promise&lt;number&gt;

Requests print preview data. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | Yes | Print job information, which is used to specify the detailed configuration of the print job to be previewed. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;number&gt; | Promise used to return the preview result, which is of the number type. The value **0** indicates that the request is successful, and a non-zero value is the error code of the failure cause. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobInfo : print.PrintJob = {
    fdList : [44, 45], // fd in fdList can be obtained through file operations such as fs.open to get the file descriptor.
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : print.PrintJobState.PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : print.PrintColorMode.COLOR_MODE_COLOR,
    duplexMode : print.PrintDuplexMode.DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.requestPrintPreview(jobInfo).then((num: number) => {
    console.info('requestPrintPreview success, num : ' + JSON.stringify(num));
}).catch((error: BusinessError) => {
    console.error(`Failed to request print preview. Code: ${error.code}, message: ${error.message}`);
});
```

## print.on

on(type: 'printerStateChange', callback: (state: PrinterState, info: PrinterInfo) => void): void

Registers a callback for the printer state change event. This API uses a callback to return the result. When the listener is no longer needed, call [print.off('printerStateChange')](#printoff) to unregister the callback. Otherwise, the callback may be continuously triggered, causing memory leak.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'printerStateChange' | Yes| Listening type. The value is fixed at **'printerStateChange'**.|
| callback | (state: [PrinterState](js-apis-print.md#printerstate14), info: [PrinterInfo](js-apis-print.md#printerinfo24)) => void | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';

print.on('printerStateChange', (state: print.PrinterState, info: print.PrinterInfo) => {
    if (state === null || info === null) {
        console.error('printer state changed state is null or info is null');
        return;
    } else {
        console.info('on printer state changed, state : ' + JSON.stringify(state));
        console.info('on printer state changed, info : ' + JSON.stringify(info));
    }
});
```

## print.off

off(type: 'printerStateChange', callback?: Callback&lt;boolean&gt;): void

Unregisters the listener for printer state change events. This API uses a callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'printerStateChange' | Yes| Listening type. The value is fixed at **'printerStateChange'**.|
| callback | Callback&lt;boolean&gt; | No| Callback used to return the result. The value **true** means that the operation is successful, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';

print.off('printerStateChange', (data: boolean) => {
    console.info('off printerStateChange data : ' + JSON.stringify(data));
});
```

## print.on

on(type: 'jobStateChange', callback: (state: PrintJobState, job: PrintJob) => void): void

Registers a callback for the print job state change event. This API uses a callback to return the result. When the listener is no longer needed, call [print.off('jobStateChange')](#printoff-1) to unregister the callback. Otherwise, the callback may be continuously triggered, causing memory leak.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'jobStateChange' | Yes| Listening type. The value is fixed at **'jobStateChange'**.|
| callback | (state: [PrintJobState](js-apis-print.md#printjobstate14), job: [PrintJob](js-apis-print.md#printjob24)) => void | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';

print.on('jobStateChange', (state: print.PrintJobState, job: print.PrintJob) => {
    console.info('onJobStateChange, state : ' + JSON.stringify(state) + ', job : ' + JSON.stringify(job));
});
```

## print.off

off(type: 'jobStateChange', callback?: Callback&lt;boolean&gt;): void

Unregisters the listener for print job state change events. This API uses a callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'jobStateChange' | Yes| Listening type. The value is fixed at **'jobStateChange'**.|
| callback | Callback&lt;boolean&gt; | No| Callback used to return the result. The value **true** means that the operation is successful, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';

print.off('jobStateChange', (data: boolean) => {
    console.info('offJobStateChanged data : ' + JSON.stringify(data));
});
```

## print.on

on(type: 'extInfoChange', callback: (extensionId: string, info: string) => void): void

Registers a callback for the printer extension information change event. This API uses a callback to return the result. When the listener is no longer needed, call [print.off('extInfoChange')](#printoff-2) to unregister the callback. Otherwise, the callback may be continuously triggered, causing memory leak.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'extInfoChange' | Yes | Printer extension information changes. |
| callback | (extensionId: string, info: string) => void | Yes | Callback invoked when the printer extension information changes. **extensionId** indicates the printer extension ID, and **info** indicates the extension information content. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';

print.on('extInfoChange', (extensionId: string, info: string) => {
    console.info('onExtInfoChange, extensionId : ' + JSON.stringify(extensionId) + ', info : ' + JSON.stringify(info));
});
```

## print.off

off(type: 'extInfoChange', callback?: Callback&lt;boolean&gt;): void

Unregisters the callback for the printer extension information change event. This API uses a callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'extInfoChange' | Yes | Printer extension information change. |
| callback | Callback&lt;boolean&gt; | No | Callback used to return the result of whether the callback for the printer extension information change event is successfully unregistered. The value **true** indicates success, and **false** indicates failure. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';

print.off('extInfoChange', (data: boolean) => {
    console.info('offExtInfoChange data : ' + JSON.stringify(data));
});
```

## print.addPrinters

addPrinters(printers: Array&lt;PrinterInfo&gt;, callback: AsyncCallback&lt;void&gt;): void

Adds printers. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | Yes | List of printers to be added. |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.addPrinters([printerInfo], (error: BusinessError) => {
    if (error) {
        console.error(`Failed to add printers. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('addPrinters success');
    }
});
```

## print.addPrinters

addPrinters(printers: Array&lt;PrinterInfo&gt;): Promise&lt;void&gt;

Adds printers. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | Yes | List of printers to be added. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the printer is successfully added, **resolve** returns a value. If the printer fails to be added, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.addPrinters([printerInfo]).then(() => {
    console.info('add printers success.');
}).catch((error: BusinessError) => {
    console.error(`Failed to add printers. Code: ${error.code}, message: ${error.message}`);
});
```

## print.removePrinters

removePrinters(printerIds: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Removes printers. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerIds | Array&lt;string&gt; | Yes | IDs of the printers to remove. |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1212';
print.removePrinters([printerId], (error: BusinessError) => {
    if (error) {
        console.error(`Failed to remove printers. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('removePrinters success');
    }
});
```

## print.removePrinters

removePrinters(printerIds: Array&lt;string&gt;): Promise&lt;void&gt;

Removes printers. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerIds | Array&lt;string&gt; | Yes | IDs of the printers to remove. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the printer is successfully removed, **resolve** returns a value. If the printer fails to be removed, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1212';
print.removePrinters([printerId]).then(() => {
    console.info('remove printers success');
}).catch((error: BusinessError) => {
    console.error(`Failed to remove printers. Code: ${error.code}, message: ${error.message}`);
});
```

## print.updatePrinters

updatePrinters(printers: Array&lt;PrinterInfo&gt;, callback: AsyncCallback&lt;void&gt;): void

Updates the information of the specified printers. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | Yes| List of printers whose information is to be updated.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.updatePrinters([printerInfo], (error: BusinessError) => {
    if (error) {
        console.error(`Failed to update printers. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('updatePrinters success');
    }
});
```

## print.updatePrinters

updatePrinters(printers: Array&lt;PrinterInfo&gt;): Promise&lt;void&gt;

Updates the information of the specified printers. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | Yes| List of printers whose information is to be updated.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the printer information is successfully updated, **resolve** returns a value. If the printer information fails to be updated, **reject** returns an error message.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerInfo : print.PrinterInfo = {
    printerId : '3232',
    printerName : 'hhhhh',
    printerState : 0,
    printerIcon : 12,
    description : 'str',
    capability : undefined,
    options : 'opt'
};
print.updatePrinters([printerInfo]).then(() => {
    console.info('update printers success');
}).catch((error: BusinessError) => {
    console.error(`Failed to update printers. Code: ${error.code}, message: ${error.message}`);
});
```

## print.updatePrinterState

updatePrinterState(printerId: string, state: PrinterState, callback: AsyncCallback&lt;void&gt;): void

Updates the printer state. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes| Printer ID.|
| state | [PrinterState](js-apis-print.md#printerstate14) | Yes | Printer state to be updated. |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1212';
let state : print.PrinterState = print.PrinterState.PRINTER_CONNECTED;
print.updatePrinterState(printerId, state, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to update printer state. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('updatePrinterState success');
    }
});
```

## print.updatePrinterState

updatePrinterState(printerId: string, state: PrinterState): Promise&lt;void&gt;

Updates the printer state. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes| Printer ID.|
| state | [PrinterState](js-apis-print.md#printerstate14) | Yes | Printer state to be updated. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the printer state is successfully updated, **resolve** returns a value. If the printer state fails to be updated, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1212';
let state : print.PrinterState = print.PrinterState.PRINTER_CONNECTED;
print.updatePrinterState(printerId, state).then(() => {
    console.info('update printer state success');
}).catch((error: BusinessError) => {
    console.error(`Failed to update printer state. Code: ${error.code}, message: ${error.message}`);
});
```

## print.updateExtensionInfo

updateExtensionInfo(info: string, callback: AsyncCallback&lt;void&gt;): void

Updates the printer extension information. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| info | string | Yes | Printer extension change information. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked after the printer extension information is asynchronously updated. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let info : string = 'WIFI_INACTIVE';
print.updateExtensionInfo(info, (error: BusinessError) => {
    if (error) {
        console.error(`Failed to update extension info. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('updateExtensionInfo success');
    }
});
```

## print.updateExtensionInfo

updateExtensionInfo(info: string): Promise&lt;void&gt;

Updates the printer extension information. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| info | string | Yes | Printer extension change information. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the printer extension information is updated successfully, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let info : string = 'WIFI_INACTIVE';
print.updateExtensionInfo(info).then(() => {
    console.info('updateExtensionInfo success');
}).catch((error: BusinessError) => {
    console.error(`Failed to update extension info. Code: ${error.code}, message: ${error.message}`);
});
```

## print.queryAllPrintJobs<sup>(deprecated)</sup>

> This API is supported since API version 10 and deprecated since API version 11. You are advised to use [queryPrintJobList](#printqueryprintjoblist11) instead.

queryAllPrintJobs(callback: AsyncCallback&lt;void&gt;): void

Queries all print jobs. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrintJobs((error: BusinessError) => {
    if (error) {
        console.error(`Failed to query all print jobs. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('queryAllPrintJobs success');
    }
});
```

## print.queryAllPrintJobs<sup>(deprecated)</sup>

> Supported since API version 10 and deprecated since API version 11. You are advised to use [queryPrintJobList](#printqueryprintjoblist11-1) instead.

queryAllPrintJobs(): Promise&lt;void&gt;

Queries all print jobs. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If all print jobs are queried successfully, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllPrintJobs().then(() => {
    console.info('queryAllPrintJobs success');
}).catch((error: BusinessError) => {
    console.error(`Failed to query all print jobs. Code: ${error.code}, message: ${error.message}`);
});
```

## print.queryAllActivePrintJobs<sup>20+</sup>

queryAllActivePrintJobs(): Promise&lt;[PrintJob](js-apis-print.md#printjob24)[]&gt;

Queries all active print jobs. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[PrintJob](js-apis-print.md#printjob24)[]&gt; | Promise used to return a list of all active print jobs.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryAllActivePrintJobs().then((printJobs : print.PrintJob[]) => {
    console.info('queryAllActivePrintJobs success, data : ' + JSON.stringify(printJobs));
}).catch((error: BusinessError) => {
    console.error(`Failed to query all active print jobs. Code: ${error.code}, message: ${error.message}`);
});
```

## print.queryPrintJobList<sup>11+</sup>

queryPrintJobList(callback: AsyncCallback&lt;Array&lt;PrintJob&gt;&gt;): void

Queries all print jobs. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;[PrintJob](js-apis-print.md#printjob24)&gt;&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryPrintJobList((error: BusinessError, printJobs : print.PrintJob[]) => {
    if (error) {
        console.error(`Failed to query print job list. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('queryPrintJobList success, data : ' + JSON.stringify(printJobs));
    }
});
```

## print.queryPrintJobList<sup>11+</sup>

queryPrintJobList(): Promise&lt;Array&lt;PrintJob&gt;&gt;

Queries all print jobs. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[PrintJob](js-apis-print.md#printjob24)&gt;&gt; | Promise used to return a list of all print jobs.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.queryPrintJobList().then((printJobs : print.PrintJob[]) => {
    console.info('queryPrintJobList success, data : ' + JSON.stringify(printJobs));
}).catch((error: BusinessError) => {
    console.error(`Failed to query print job list. Code: ${error.code}, message: ${error.message}`);
});
```

## print.queryPrintJobById<sup>11+</sup>

queryPrintJobById(jobId: string, callback: AsyncCallback&lt;PrintJob&gt;): void

Queries a print job by ID. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes | ID of the created print job. |
| callback | AsyncCallback&lt;[PrintJob](js-apis-print.md#printjob24)&gt; | Yes| Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.queryPrintJobById(jobId, (error: BusinessError, printJob : print.PrintJob) => {
    if (error) {
        console.error(`Failed to query print job by id. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('queryPrintJobById success, data : ' + JSON.stringify(printJob));
    }
});
```

## print.queryPrintJobById<sup>11+</sup>

queryPrintJobById(jobId: string): Promise&lt;PrintJob&gt;

Queries a print job by ID. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes | ID of the created print job. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[PrintJob](js-apis-print.md#printjob24)&gt; | Promise used to return the queried print job.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.queryPrintJobById(jobId).then((printJob : print.PrintJob) => {
    console.info('queryPrintJobById data : ' + JSON.stringify(printJob));
}).catch((error: BusinessError) => {
    console.error(`Failed to query print job by id. Code: ${error.code}, message: ${error.message}`);
});
```

## print.startGettingPrintFile<sup>11+</sup>

startGettingPrintFile(jobId: string, printAttributes: PrintAttributes, fd: number, onFileStateChanged: Callback&lt;PrintFileCreationState&gt;): void

Starts to obtain the print file.  This API uses an asynchronous callback to return the result. After **print()** is executed, **jobId** is created, and [PrintDocumentAdapter](js-apis-print.md#printdocumentadapter11) is registered, you can call this function to obtain the actual print file content.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes | ID of the created print job. |
| printAttributes | [PrintAttributes](js-apis-print.md#printattributes11) | Yes| Print attributes.|
| fd | number | Yes | Print file descriptor, which must be a non-negative integer. |
| onFileStateChanged | Callback&lt;[PrintFileCreationState](js-apis-print.md#printfilecreationstate11)&gt; | Yes| Callback for updating the file state.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
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

## print.notifyPrintService<sup>11+</sup>

notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started', callback: AsyncCallback&lt;void&gt;): void

Notifies the print service that the print preview page is closed. This API uses an asynchronous callback to return the result. This method is used to notify the print service to perform clearance, exit, and other operations after the print preview page is closed.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes | ID of the created print job. |
| type | 'spooler_closed_for_cancelled' \| 'spooler_closed_for_started' | Yes | Type of information that causes closing of the print preview page. **'spooler_closed_for_cancelled'** indicates that the print preview page is closed because the current print job is canceled. **'spooler_closed_for_started'** indicates that the print preview page is closed because the print job is successfully delivered. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked when the information about closing the print preview page is asynchronously sent to the printing service. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.notifyPrintService(jobId, 'spooler_closed_for_started', (error: BusinessError) => {
    if (error) {
        console.error(`Failed to notify print service. Code: ${error.code}, message: ${error.message}`);
    } else {
        console.info('notifyPrintService success');
    }
});
```

## print.notifyPrintService<sup>11+</sup>

notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started'): Promise&lt;void&gt;

Notifies the print service that the print preview page is closed. This API uses a promise to return the result. This method is used to notify the print service to perform clearance, exit, and other operations after the print preview page is closed.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes | ID of the created print job. |
| type | 'spooler_closed_for_cancelled' \| 'spooler_closed_for_started' | Yes | Type of information that causes closing of the print preview page. **'spooler_closed_for_cancelled'** indicates that the print preview page is closed because the current print job is canceled. **'spooler_closed_for_started'** indicates that the print preview page is closed because the print job is successfully delivered. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the print preview interface closing information is successfully notified to the print service, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let jobId : string = '1';
print.notifyPrintService(jobId, 'spooler_closed_for_started').then(() => {
    console.info('notifyPrintService success');
}).catch((error: BusinessError) => {
    console.error(`Failed to notify print service. Code: ${error.code}, message: ${error.message}`);
});
```

## print.getPrinterInfoById<sup>12+</sup>

getPrinterInfoById(printerId: string): Promise&lt;PrinterInfo&gt;

Obtains printer information based on the printer ID. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes| Printer ID.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | Promise used to return the printer information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1';
print.getPrinterInfoById(printerId).then((printerInfo : print.PrinterInfo) => {
    console.info('getPrinterInfoById data : ' + JSON.stringify(printerInfo));
}).catch((error: BusinessError) => {
    console.error(`Failed to get printer info by id. Code: ${error.code}, message: ${error.message}`);
});
```

## print.notifyPrintServiceEvent<sup>12+</sup>

notifyPrintServiceEvent(event: ApplicationEvent): Promise&lt;void&gt;

Notifies the print service of the print app events. This API uses a promise to return the result. This method is used to notify the print service to perform corresponding processing when a lifecycle event such as creation and destruction of a print app occurs.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | [ApplicationEvent](js-apis-print.md#applicationevent14) | Yes| Print application events.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the print app events are successfully notified to the print service, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let event : print.ApplicationEvent = print.ApplicationEvent.APPLICATION_CREATED;
print.notifyPrintServiceEvent(event).then(() => {
    console.info('notifyPrintServiceEvent success');
}).catch((error: BusinessError) => {
    console.error(`Failed to notify print service event. Code: ${error.code}, message: ${error.message}`);
});
```

## print.setPrinterPreferences<sup>18+</sup>

setPrinterPreferences(printerId: string, printerPreferences: PrinterPreferences): Promise&lt;void&gt;

Sets the printer preferences. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes| Printer ID.|
| printerPreferences | [PrinterPreferences](js-apis-print.md#printerpreferences18) | Yes | Printer preferences. This parameter is used to configure the default print parameters of the printer, such as the default duplex mode. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the printer preferences are set successfully, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = 'testPrinterId';
let preferences : print.PrinterPreferences = {
    defaultDuplexMode: print.PrintDuplexMode.DUPLEX_MODE_NONE
};
print.setPrinterPreferences(printerId, preferences).then(() => {
    console.info('setPrinterPreferences success');
}).catch((error: BusinessError) => {
    console.error(`Failed to set printer preferences. Code: ${error.code}, message: ${error.message}`);
});
```

## print.discoverUsbPrinters<sup>18+</sup>

discoverUsbPrinters(): Promise&lt;Array&lt;PrinterInformation&gt;&gt;

Discovers USB printers. This API uses an asynchronous callback to return the result. It returns the discovered USB printer information, and the printer URI can be used to query printer capabilities by calling [queryPrinterCapabilityByUri](#printqueryprintercapabilitybyuri24) or to add the printer to CUPS by calling [addPrinterToCups](#printaddprintertocups24).

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[PrinterInformation](js-apis-print.md#printerinformation14)&gt;&gt; | Promise used to return the discovered USB printer information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

print.discoverUsbPrinters().then((printers : print.PrinterInformation[]) => {
    console.info('discoverUsbPrinters data : ' + JSON.stringify(printers));
}).catch((error: BusinessError) => {
    console.error(`Failed to discover USB printers. Code: ${error.code}, message: ${error.message}`);
});
```

## print.setDefaultPrinter<sup>18+</sup>

setDefaultPrinter(printerId: string, type: DefaultPrinterType): Promise&lt;void&gt;

Sets the default printer. This API uses an asynchronous callback to return the result. It is used in scenarios where the system default printer needs to be specified, such as when a user manually selects a default printer or the system automatically sets the printer used last time as the default printer.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes| Printer ID.|
| type | [DefaultPrinterType](js-apis-print.md#defaultprintertype18) | Yes | Default printer type, which is used to specify the default printer. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the default printer is set successfully, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerId : string = '1';
let type : print.DefaultPrinterType = print.DefaultPrinterType.DEFAULT_PRINTER_TYPE_SET_BY_USER;
print.setDefaultPrinter(printerId, type).then(() => {
    console.info('setDefaultPrinter success');
}).catch((error: BusinessError) => {
    console.error(`Failed to set default printer. Code: ${error.code}, message: ${error.message}`);
});
```

## print.notifyPrintServiceEvent<sup>18+</sup>

notifyPrintServiceEvent(event: ApplicationEvent, jobId: string): Promise&lt;void&gt;

Notifies the print service of the print app events. This API uses a promise to return the result. This method is used to notify the print service based on the print job ID to perform corresponding processing when a lifecycle event such as creation and destruction of a print app occurs.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | [ApplicationEvent](js-apis-print.md#applicationevent14) | Yes | Print appn event, which is used to notify the print service of the app lifecycle event. |
| jobId | string | Yes | ID of the created print job. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the print app events are successfully notified to the print service, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let event : print.ApplicationEvent = print.ApplicationEvent.APPLICATION_CREATED;
let jobId : string = '1';
print.notifyPrintServiceEvent(event, jobId).then(() => {
    console.info('notifyPrintServiceEvent success');
}).catch((error: BusinessError) => {
    console.error(`Failed to notify print service event. Code: ${error.code}, message: ${error.message}`);
});
```

## print.queryPrinterCapabilityByUri<sup>24+</sup>

queryPrinterCapabilityByUri(printerUri: string, printerId: string): Promise&lt;[PrinterCapabilities](js-apis-print.md#printercapabilities14)&gt;

Queries the printer capability by the printer URI. This API uses a promise to return the result. This API can be used to query the capabilities of a printer when the printer URI is known but the printer is not registered locally. It can also be used to discover the capabilities of a USB printer.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerUri | string | Yes | Printer URI, which can be obtained by calling [PrinterInformation](js-apis-print.md#printerinformation14). |
| printerId | string | Yes| Printer ID.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[PrinterCapabilities](js-apis-print.md#printercapabilities14)&gt; | Promise used to return the printer capabilities, which are used to obtain the functions and configuration options supported by the printer.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Print Service Error Codes](errorcode-print.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 13100005 | Can not find the printer in system. |

**Example**

```ts
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

## print.addPrinterToCups<sup>24+</sup>

addPrinterToCups(printerUri: string, printerName: string, printerMake: string): Promise&lt;boolean&gt;

Adds a printer to CUPS. This API uses an asynchronous callback to return the result. CUPS is the print service framework in the system, which is used to manage printers and print jobs.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerUri | string | Yes | Printer URI, which can be obtained by calling [PrinterInformation](js-apis-print.md#printerinformation14). |
| printerName | string | Yes| Printer name.|
| printerMake | string | Yes | Printer brand. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and **false** indicates the opposite. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Print Service Error Codes](errorcode-print.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 13100003 | Add a printer to cups failed. |

**Example**

```ts
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

## print.deletePrinterFromCups<sup>24+</sup>

deletePrinterFromCups(printerName: string): Promise&lt;void&gt;

Deletes a printer from CUPS. This API uses an asynchronous callback to return the result. CUPS is the print service framework in the system, which is used to manage printers and print jobs.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerName | string | Yes| Printer name.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. If the printer is successfully deleted from CUPS, **resolve** returns a value. If it fails, **reject** returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerName : string = 'testPrinterName';

print.deletePrinterFromCups(printerName).then(() => {
    console.info('deletePrinterFromCups success');
}).catch((error: BusinessError) => {
    console.error(`Failed to delete printer from cups. Code: ${error.code}, message: ${error.message}`);
});
```
