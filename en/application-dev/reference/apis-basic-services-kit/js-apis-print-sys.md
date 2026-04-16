# @ohos.print (Print) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @gcw_4D6e0BBd-->
<!--Tester: @guoshengbang-->
<!--Adviser: @RayShih-->

The **print** module provides APIs for basic print operations.

> **NOTE** 
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.print (Print) (System API)](js-apis-print-sys.md).

## Modules to Import

```ts
import { print } from '@kit.BasicServicesKit';
```

## PrinterExtensionInfo

Provides the printer extension information.

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Attributes**

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| extensionId | string | No| No| ID of the printer extension.|
| vendorId | string | No| No| Vendor ID of the printer extension.|
| vendorName | string | No| No| Vendor name of the printer extension.|
| vendorIcon | number | No| No| Vendor icon of the printer extension.|
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

print.queryAllPrinterExtensionInfos((err: BusinessError, extensionInfos: print.PrinterExtensionInfo[]) => {
    if (err) {
        console.error('queryAllPrinterExtensionInfos err ' + JSON.stringify(err));
    } else {
        console.info('queryAllPrinterExtensionInfos success ' + JSON.stringify(extensionInfos));
    }
})
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
    console.error('failed to get AllPrinterExtension because ' + JSON.stringify(error));
})
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
| printerId | string | Yes| Printer ID.|
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
print.disconnectPrinter(printerId, (err: BusinessError) => {
    if (err) {
        console.error('failed to disconnect Printer because : ' + JSON.stringify(err));
    } else {
        console.info('start disconnect Printer success');
    }
})
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
| printerId | string | Yes| Printer ID.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('failed to disconnect Printer because : ' + JSON.stringify(error));
})
```

## print.queryPrinterCapability

queryPrinterCapability(printerId: string, callback: AsyncCallback&lt;void&gt;): void

Queries the printer capability. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes| Printer ID.|
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
print.queryPrinterCapability(printerId, (err: BusinessError) => {
    if (err) {
        console.error('failed to query Printer Capability because : ' + JSON.stringify(err));
    } else {
        console.info('start query Printer Capability success');
    }
})
```

## print.queryPrinterCapability

queryPrinterCapability(printerId: string): Promise&lt;void&gt;

Queries the printer capability. This API uses a promise to return the result.

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
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('failed to query Printer Capability because : ' + JSON.stringify(error));
})
```

## print.startPrintJob

startPrintJob(jobInfo: PrintJob, callback: AsyncCallback&lt;void&gt;): void

Starts the specified print job. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | Yes| Information about the print job.|
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
    fdList : [44,45],
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
print.startPrintJob(jobInfo, (err: BusinessError) => {
    if (err) {
        console.error('failed to start Print Job because : ' + JSON.stringify(err));
    } else {
        console.info('start Print Job success');
    }
})
```

## print.startPrintJob

startPrintJob(jobInfo: PrintJob): Promise&lt;void&gt;

Starts the specified print job. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | Yes| Information about the print job.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    fdList : [44,45],
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
    console.error('failed to start Print because : ' + JSON.stringify(error));
})
```

## print.cancelPrintJob

cancelPrintJob(jobId: string, callback: AsyncCallback&lt;void&gt;): void

Cancels the specified print job, which is on the print queue of the printer. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes| Print job ID.|
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
print.cancelPrintJob(jobId, (err: BusinessError) => {
    if (err) {
        console.error('cancelPrintJob failed, because : ' + JSON.stringify(err));
    } else {
        console.info('cancelPrintJob success');
    }
})
```

## print.cancelPrintJob

cancelPrintJob(jobId: string): Promise&lt;void&gt;

Cancels the specified print job, which is on the print queue of the printer. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes| Print job ID.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('cancelPrintJob failed, because : ' + JSON.stringify(error));
})
```

## print.restartPrintJob<sup>20+</sup>

restartPrintJob(jobId: string): Promise&lt;void&gt;

Restarts a print job that has been finished before. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes| ID of a print job that has been finished before.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('restartPrintJob failed, because : ' + JSON.stringify(error));
})
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
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | Yes| Information about the print job.|
| callback | Callback&lt;number&gt; | Yes| Callback used to return the result.|

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
    fdList : [44,45],
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : COLOR_MODE_COLOR,
    duplexMode : DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.requestPrintPreview(jobInfo, (num : number) => {
    console.info('requestPrintPreview success, num : ' + JSON.stringify(num));

})
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
| jobInfo | [PrintJob](js-apis-print.md#printjob24) | Yes| Information about the print job.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;number&gt; | Promise used to return the preview result.|

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
    fdList : [44,45],
    jobId : 'jobId_12',
    printerId : 'printerId_32',
    jobState : PRINT_JOB_COMPLETED,
    jobSubstate : print.PrintJobSubState.PRINT_JOB_COMPLETED_SUCCESS,
    copyNumber : 1,
    pageRange : {},
    isSequential : false,
    pageSize : {id : '', name : '', width : 10, height : 20},
    isLandscape : false,
    colorMode : COLOR_MODE_COLOR,
    duplexMode : DUPLEX_MODE_NONE,
    margin : undefined,
    preview : undefined,
    options : undefined
};
print.requestPrintPreview(jobInfo).then((num: number) => {
    console.info('requestPrintPreview success, num : ' + JSON.stringify(num));
}).catch((error: BusinessError) => {
    console.error('requestPrintPreview failed, because : ' + JSON.stringify(error));
})
```

## print.on

on(type: 'printerStateChange', callback: (state: PrinterState, info: PrinterInfo) => void): void

Registers a listener for printer state change events. This API uses a callback to return the result.

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
})
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
})
```

## print.on

on(type: 'jobStateChange', callback: (state: PrintJobState, job: PrintJob) => void): void

Registers a listener for print job state change events. This API uses a callback to return the result.

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
})
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
})
```

## print.on

on(type: 'extInfoChange', callback: (extensionId: string, info: string) => void): void

Registers a listener for printer extension information change events. This API uses a callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'extInfoChange' | Yes| Listening type. The value is fixed at **'extInfoChange'**.|
| callback | (extensionId: string, info: string) => void | Yes| Callback used to return the result.|

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
})
```

## print.off

off(type: 'extInfoChange', callback?: Callback&lt;boolean&gt;): void

Unregisters the listener for printer extension information change events. This API uses a callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'extInfoChange' | Yes| Listening type. The value is fixed at **'extInfoChange'**.|
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

print.off('extInfoChange', (data: boolean) => {
    console.info('offExtInfoChange data : ' + JSON.stringify(data));
})
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
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | Yes| List of printers to add.|
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
print.addPrinters([printerInfo], (err: BusinessError) => {
    if (err) {
        console.error('addPrinters failed, because : ' + JSON.stringify(err));
    } else {
        console.info('addPrinters success');
    }
})
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
| printers | Array&lt;[PrinterInfo](js-apis-print.md#printerinfo24)&gt; | Yes| List of printers to add.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('add printers error : ' + JSON.stringify(error));
})
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
| printerIds | Array&lt;string&gt; | Yes| List of printers to remove.|
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
print.removePrinters([printerId], (err: BusinessError) => {
    if (err) {
        console.error('removePrinters failed, because : ' + JSON.stringify(err));
    } else {
        console.info('removePrinters success');
    }
})
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
| printerIds | Array&lt;string&gt; | Yes| List of printers to remove.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('remove printers error : ' + JSON.stringify(error));
})
```

## print.updatePrinters

updatePrinters(printers: Array&lt;PrinterInfo&gt;, callback: AsyncCallback&lt;void&gt;): void

Updates information about the specified printers. This API uses an asynchronous callback to return the result.

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
print.updatePrinters([printerInfo], (err: BusinessError) => {
    if (err) {
        console.error('updataPrinters failed, because : ' + JSON.stringify(err));
    } else {
        console.info('updataPrinters success');
    }
})
```

## print.updatePrinters

updatePrinters(printers: Array&lt;PrinterInfo&gt;): Promise&lt;void&gt;

Updates information about the specified printers. This API uses a promise to return the result.

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
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('update printers error : ' + JSON.stringify(error));
})
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
| state | [PrinterState](js-apis-print.md#printerstate14) | Yes| Printer state.|
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
print.updatePrinterState(printerId, state, (err: BusinessError) => {
    if (err) {
        console.error('updatePrinterState failed, because : ' + JSON.stringify(err));
    } else {
        console.info('updatePrinterState success');
    }
})
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
| state | [PrinterState](js-apis-print.md#printerstate14) | Yes| Printer state.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('update printer state error : ' + JSON.stringify(error));
})
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
| info | string | Yes| New printer extension information.|
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

let info : string = 'WIFI_INACTIVE';
print.updateExtensionInfo(info, (err: BusinessError) => {
    if (err) {
        console.error('updateExtensionInfo failed, because : ' + JSON.stringify(err));
    } else {
        console.info('updateExtensionInfo success');
    }
})
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
| info | string | Yes| New printer extension information.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.info('update print job state success');
}).catch((error: BusinessError) => {
    console.error('update print job state error : ' + JSON.stringify(error));
})
```

## print.queryAllPrintJobs<sup>(deprecated)</sup>

> This API is supported since API version 10 and deprecated since API version 11.
> You are advised to use [queryPrintJobList](#printqueryprintjoblist11) instead.

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

print.queryAllPrintJobs((err: BusinessError) => {
    if (err) {
        console.error('queryAllPrintJobs failed, because : ' + JSON.stringify(err));
    } else {
        console.info('queryAllPrintJobs success');
    }
})
```

## print.queryAllPrintJobs<sup>(deprecated)</sup>

> This API is supported since API version 10 and deprecated since API version 11.
> You are advised to use [queryPrintJobList](#printqueryprintjoblist11-1) instead.

queryAllPrintJobs(): Promise&lt;void&gt;

Queries all print jobs. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('queryAllPrintJobs failed, error : ' + JSON.stringify(error));
})
```

## print.queryAllActivePrintJobs<sup>20+</sup>

queryAllActivePrintJobs(): Promise&lt;[PrintJob](js-apis-print.md#printjob24)[]&gt;

Queries all active print jobs. This API uses a promise to return the result.

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
    console.error('queryAllActivePrintJobs failed, error : ' + JSON.stringify(error));
})
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

print.queryPrintJobList((err: BusinessError, printJobs : print.PrintJob[]) => {
    if (err) {
        console.error('queryPrintJobList failed, because : ' + JSON.stringify(err));
    } else {
        console.info('queryPrintJobList success, data : ' + JSON.stringify(printJobs));
    }
})
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
    console.error('queryPrintJobList failed, error : ' + JSON.stringify(error));
})
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
| jobId | string | Yes| ID of the print job.|
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
print.queryPrintJobById(jobId, (err: BusinessError, printJob : print.PrintJob) => {
    if (err) {
        console.error('queryPrintJobById failed, because : ' + JSON.stringify(err));
    } else {
        console.info('queryPrintJobById success, data : ' + JSON.stringify(printJob));
    }
})
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
| jobId | string | Yes| ID of the print job.|

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
    console.error('queryPrintJobById error : ' + JSON.stringify(error));
})
```

## print.startGettingPrintFile<sup>11+</sup>

startGettingPrintFile(jobId: string, printAttributes: PrintAttributes, fd: number, onFileStateChanged: Callback&lt;PrintFileCreationState&gt;): void

Starts to obtain the print file. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes| ID of the print job.|
| printAttributes | [PrintAttributes](js-apis-print.md#printattributes11) | Yes| Print attributes.|
| fd | number | Yes| File descriptor.|
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

let jobId : string= '1';
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

class MyPrintPageSize implements print.PrintPageSize {
    id: string = '0';
    name: string = '0';
    width: number = 210;
    height: number = 297;
}

let printAttributes = new MyPrintAttributes();
printAttributes.copyNumber = 2;
printAttributes.pageRange = new MyPrintPageRange();
printAttributes.pageRange.pages = [1, 3];
printAttributes.pageSize = print.PrintPageType.PAGE_ISO_A3;
printAttributes.directionMode = print.PrintDirectionMode.DIRECTION_MODE_AUTO;
printAttributes.colorMode = print.PrintColorMode.COLOR_MODE_MONOCHROME;
printAttributes.duplexMode = print.PrintDuplexMode.DUPLEX_MODE_NONE;

let fd : number = 1;
print.startGettingPrintFile(jobId, printAttributes, fd, (state: print.PrintFileCreationState) => {
    console.info('onFileStateChanged success, data : ' + JSON.stringify(state));
})
```

## print.notifyPrintService<sup>11+</sup>

notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started', callback: AsyncCallback&lt;void&gt;): void

Notifies the print service of the spooler shutdown information. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes| ID of the print job.|
| type | 'spooler_closed_for_cancelled' \| 'spooler_closed_for_started' | Yes| Spooler shutdown information.|
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

let jobId : string = '1';
print.notifyPrintService(jobId, 'spooler_closed_for_started', (err: BusinessError) => {
    if (err) {
        console.error('notifyPrintService failed, because : ' + JSON.stringify(err));
    } else {
        console.info('notifyPrintService success');
    }
})
```

## print.notifyPrintService<sup>11+</sup>

notifyPrintService(jobId: string, type: 'spooler_closed_for_cancelled' | 'spooler_closed_for_started'): Promise&lt;void&gt;

Notifies the print service of the spooler shutdown information. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| jobId | string | Yes| ID of the print job.|
| type | 'spooler_closed_for_cancelled' \| 'spooler_closed_for_started' | Yes| Spooler shutdown information.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('notifyPrintService error : ' + JSON.stringify(error));
})
```

## print.getPrinterInfoById<sup>12+</sup>

getPrinterInfoById(printerId: string): Promise&lt;PrinterInfo&gt;

Obtains printer information based on the printer ID. This API uses a promise to return the result.

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
    console.error('getPrinterInfoById error : ' + JSON.stringify(error));
})
```

## print.notifyPrintServiceEvent<sup>12+</sup>

notifyPrintServiceEvent(event: ApplicationEvent): Promise&lt;void&gt;

Notifies the print service of the print application events. This API uses a promise to return the result.

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
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('notifyPrintServiceEvent error : ' + JSON.stringify(error));
})
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
| printerPreferences | [PrinterPreferences](js-apis-print.md#printerpreferences18) | Yes| Printer preferences.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('setPrinterPreferences error : ' + JSON.stringify(error));
})
```

## print.discoverUsbPrinters<sup>18+</sup>

discoverUsbPrinters(): Promise&lt;Array&lt;PrinterInformation&gt;&gt;

Discovers USB printers. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[PrinterInformation](js-apis-print.md#printerinformation14)&gt;&gt; | Promise used to return the information about the discovered USB printers.|

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
    console.error('discoverUsbPrinters error : ' + JSON.stringify(error));
})
```

## print.setDefaultPrinter<sup>18+</sup>

setDefaultPrinter(printerId: string, type: DefaultPrinterType): Promise&lt;void&gt;

Sets the default printer. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerId | string | Yes| Printer ID.|
| type | [DefaultPrinterType](js-apis-print.md#defaultprintertype18) | Yes| Default printer type.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('setDefaultPrinter error : ' + JSON.stringify(error));
})
```

## print.notifyPrintServiceEvent<sup>18+</sup>

notifyPrintServiceEvent(event: ApplicationEvent, jobId: string): Promise&lt;void&gt;

Notifies the print service of the print application events. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| event | [ApplicationEvent](js-apis-print.md#applicationevent14) | Yes| Print application events.|
| jobId | string | Yes| ID of the print job.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

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
    console.error('notifyPrintServiceEvent error : ' + JSON.stringify(error));
})
```

## print.queryPrinterCapabilityByUri<sup>24+</sup>

queryPrinterCapabilityByUri(printerUri: string, printerId: string): Promise&lt;[PrinterCapabilities](js-apis-print.md#printercapabilities14)&gt;

Queries the printer capability by the printer URI. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerUri | string | Yes| Printer URI.|
| printerId | string | Yes| Printer ID.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[PrinterCapabilities](js-apis-print.md#printercapabilities14)&gt; | Promise used to return the printer capability.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Print Service Error Codes](errorcode-print.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 13100005 | Invalid printer. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerUri : string = "testPrinterUri";
let printerId : string = "testPrinterId";
print.queryPrinterCapabilityByUri(printerUri, printerId).then((capabilities: print.PrinterCapabilities) => {
    console.info('queryPrinterCapabilityByUri success' + JSON.stringify(capabilities));
}).catch((error: BusinessError) => {
    console.error('queryPrinterCapabilityByUri error : ' + JSON.stringify(error));
})
```

## print.addPrinterToCups<sup>24+</sup>

addPrinterToCups(printerUri: string, printerName: string, printerMake: string): Promise&lt;boolean&gt;

Adds a printer to CUPS. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_PRINT_JOB

**System API**: This is a system API.

**System capability**: SystemCapability.Print.PrintFramework

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| printerUri | string | Yes| Printer URI.|
| printerName | string | Yes| Printer name.|
| printerMake | string | Yes| Printer model.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the operation is successful, and **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Print Service Error Codes](errorcode-print.md).

| ID| Error Message                                   |
| -------- | ------------------------------------------- |
| 201 | the application does not have permission to call this function. |
| 202 | not system application |
| 13100003 | Failure of print service. |

**Example**

```ts
import { print } from '@kit.BasicServicesKit';
import { BusinessError } from '@kit.BasicServicesKit';

let printerUri : string = "testPrinterUri";
let printerName : string = "testPrinterName";
let printerMake : string = "testPrinterMake";

print.addPrinterToCups(printerUri, printerName, printerMake).then((result: boolean) => {
    console.info('addPrinterToCups success' + JSON.stringify(result));
}).catch((error: BusinessError) => {
    console.error('addPrinterToCups error : ' + JSON.stringify(error));
})
```

## print.deletePrinterFromCups<sup>24+</sup>

deletePrinterFromCups(printerName: string): Promise&lt;void&gt;

Deletes a printer from CUPS. This API uses a promise to return the result.

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
| Promise&lt;void&gt; | Promise that returns no value.|

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

let printerName : string = "testPrinterName";

print.deletePrinterFromCups(printerName).then(() => {
    console.info('deletePrinterFromCups success');
}).catch((error: BusinessError) => {
    console.error('deletePrinterFromCups error : ' + JSON.stringify(error));
})
```
