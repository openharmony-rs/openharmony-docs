# @ohos.dlpPermission (DLP)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @lucky-jinduo-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

Data loss prevention (DLP) is a system solution provided to prevent data disclosure. This module provides APIs for cross-device file access management, encrypted storage, and access authorization.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The kit to which **@ohos.dlpPermission** belongs has been changed from `DataLossPreventionKit` to `DataProtectionKit`. You are advised to use the new module name `@kit.DataProtectionKit` to import the module. If `@kit.DataLossPreventionKit` is imported, only the APIs before the change can be called and the APIs after the change cannot be used.

## Modules to Import

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
```

## dlpPermission.isDLPFile

isDLPFile(fd: number): Promise&lt;boolean&gt;

Checks whether a file is a DLP file based on the FD. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fd | number | Yes| FD of the file to be checked. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, **false** is returned. If the value of **fd** is greater than 2<sup>31</sup>-1, the value is truncated.|

**Return value**
| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise object. The value **true** means the file is a DLP file; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "file://docs/storage/Users/currentUser/Documents/test.txt.dlp";
let file: number | undefined = undefined;
file = fileIo.openSync(uri).fd;
let res = await dlpPermission.isDLPFile(file);
console.info('res', res);
if (file !== undefined) {
  fileIo.closeSync(file);
}
```

## dlpPermission.isDLPFile

isDLPFile(fd: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a file is a DLP file based on the FD. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fd | number | Yes| FD of the file to be checked. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, **false** is returned. If the value of **fd** is greater than 2<sup>31</sup>-1, the value is truncated.|
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. The value **true** means the file is a DLP file; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
let file: number | undefined = undefined;
file = fileIo.openSync(uri).fd;
dlpPermission.isDLPFile(file, (err, res) => {
 if (err != undefined) {
    console.error('isDLPFile error,', err.code, err.message);
  } else {
    console.info('res', res);
  }
  fileIo.closeSync(file);
});
```

## dlpPermission.getDLPPermissionInfo

getDLPPermissionInfo(): Promise&lt;DLPPermissionInfo&gt;

Obtains the permission information of this DLP file. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[DLPPermissionInfo](#dlppermissioninfo)&gt; | Promise used to return the permission information about the DLP file. The operation is successful if no error is reported.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100006 | No permission to call this API, which is available only for DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.isInSandbox().then(async (inSandbox) => { // Check whether the application is running in a sandbox.
  if (inSandbox) {
    let res: dlpPermission.DLPPermissionInfo = await dlpPermission.getDLPPermissionInfo(); // Obtain the permission information.
    console.info('res', JSON.stringify(res));
  }
});
```

## dlpPermission.getDLPPermissionInfo

getDLPPermissionInfo(callback: AsyncCallback&lt;DLPPermissionInfo&gt;): void

Obtains the permission information of this DLP file. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;[DLPPermissionInfo](#dlppermissioninfo)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100006 | No permission to call this API, which is available only for DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.isInSandbox().then((inSandbox) => { // Check whether the application is running in a sandbox.
  if (inSandbox) {
    dlpPermission.getDLPPermissionInfo((err, res) =>  { 
      if (err != undefined) {
        console.error('getDLPPermissionInfo error', err.code, err.message);
      } else {
        console.info('res', JSON.stringify(res));
      }
    }); // Obtain the permission information.
  }
});
```

## dlpPermission.getOriginalFileName

getOriginalFileName(fileName: string): string

Obtains the original file name of a DLP file. This API returns the result synchronously.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fileName | string | Yes| Name of the target file. The value contains up to 255 bytes. Otherwise, **null** is returned.|

**Return value**

| Type| Description|
| -------- | -------- |
| string | Original name of the DLP file obtained. For example, if the DLP file name is **test.txt.dlp**, the original file name returned is **test.txt**. The value contains up to 255 bytes.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let res = dlpPermission.getOriginalFileName('test.txt.dlp'); // Obtain the original file name.
console.info('res', res);
```

## dlpPermission.getDLPSuffix

getDLPSuffix(): string

Obtains the DLP file name extension. This API returns the result synchronously.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| string | DLP file name extension obtained. For example, if the original file name is **text.txt**, the encrypted DLP file name is **test.txt.dlp**, and the returned extension is **.dlp**.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let res = dlpPermission.getDLPSuffix(); // Obtain the DLP file name extension.
console.info('res', res);
```

## dlpPermission.on('openDLPFile')

on(type: 'openDLPFile', listener: Callback&lt;AccessedDLPFileInfo&gt;): void

Subscribes to a DLP file open event. The application will be notified when the DLP file is opened.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'openDLPFile' | Yes| Event type. It has a fixed value of **openDLPFile**, which indicates the DLP file open event.|
| listener | Callback&lt;[AccessedDLPFileInfo](#accesseddlpfileinfo)&gt; | Yes| Callback invoked when a DLP file is opened. The application will be notified when the DLP file is opened.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.on('openDLPFile', (info: dlpPermission.AccessedDLPFileInfo) => {
  console.info('openDlpFile event', info.uri, info.lastOpenTime);
}); // Subscribe to a DLP file open event.
```

## dlpPermission.off('openDLPFile')

off(type: 'openDLPFile', listener?: Callback&lt;AccessedDLPFileInfo&gt;): void

Unsubscribes from the DLP file open event. The application will not be notified when a DLP file is opened.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'openDLPFile' | Yes| Event type. It has a fixed value of **openDLPFile**, which indicates the DLP file open event.|
| listener | Callback&lt;[AccessedDLPFileInfo](#accesseddlpfileinfo)&gt; | No| Callback for the DLP file open event. The application will not be notified when a DLP file is opened. By default, this parameter is left blank, which unregisters all callbacks for the file open event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.off('openDLPFile', (info: dlpPermission.AccessedDLPFileInfo) => {
  console.info('openDlpFile event', info.uri, info.lastOpenTime);
}); // Unsubscribe from the DLP file open event.
```

## dlpPermission.isInSandbox

isInSandbox(): Promise&lt;boolean&gt;

Checks whether this application is running in a DLP sandbox environment. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise object. The value **true** means the application is running in a sandbox; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inSandbox = await dlpPermission.isInSandbox(); // Check whether the application is running in a sandbox.
console.info('res', inSandbox);
```

## dlpPermission.isInSandbox

isInSandbox(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether this application is running in a DLP sandbox environment. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. The value **true** means the application is running in a sandbox; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.isInSandbox((err, data) => {
  if (err) {
    console.error('isInSandbox error', err.code, err.message);
  } else {
    console.info('isInSandbox, data', JSON.stringify(data));
  }
}); // Whether the application is running in a sandbox.
```

## dlpPermission.getDLPSupportedFileTypes

getDLPSupportedFileTypes(): Promise&lt;Array&lt;string&gt;&gt;

Obtains the file name extension types that support DLP. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the file name extension types obtained.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let res = await dlpPermission.getDLPSupportedFileTypes(); // Obtain the file types that support DLP.
console.info('res', JSON.stringify(res));
```

## dlpPermission.getDLPSupportedFileTypes

getDLPSupportedFileTypes(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Obtains the file name extension types that support DLP. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.getDLPSupportedFileTypes((err, res) => {
  if (err != undefined) {
    console.error('getDLPSupportedFileTypes error', err.code, err.message);
  } else {
    console.info('res', JSON.stringify(res));
  }
}); // Obtain the file types that support DLP.
```

## dlpPermission.setRetentionState

setRetentionState(docUris: Array&lt;string&gt;): Promise&lt;void&gt;

Sets the sandbox retention state. This API uses an asynchronous callback to return the result. A sandbox application is automatically installed when a DLP file is opened, and automatically uninstalled when the DLP file is closed. Once the sandbox retention state is set for a DLP file, the sandbox application will not be automatically uninstalled when the DLP file is closed. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| docUris | Array&lt;string&gt; | Yes| URIs of the files to be set with the retention state. The array has no length limit, but each string cannot exceed 4,095 bytes. Otherwise, **null** is returned.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100006 | No permission to call this API, which is available only for DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
let inSandbox = await dlpPermission.isInSandbox(); // Check whether the application is running in a sandbox.
if (inSandbox) {
  await dlpPermission.setRetentionState([uri]); // Set the sandbox retention state.
}
```

## dlpPermission.setRetentionState

setRetentionState(docUris: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Sets the sandbox retention state. This API uses an asynchronous callback to return the result. A sandbox application is automatically installed when a DLP file is opened, and automatically uninstalled when the DLP file is closed. Once the sandbox retention state is set for a DLP file, the sandbox application will not be automatically uninstalled when the DLP file is closed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| docUris | Array&lt;string&gt; | Yes| URIs of the files to be set with the retention state. The array has no length limit, but each string cannot exceed 4095 bytes.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100006 | No permission to call this API, which is available only for DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
let inSandbox = await dlpPermission.isInSandbox(); // Check whether the application is running in a sandbox.
if (inSandbox) {
  dlpPermission.setRetentionState([uri], (err, res) => {
    if (err != undefined) {
      console.error('setRetentionState error,', err.code, err.message);
    } else {
      console.info('setRetentionState success');
      console.info('res', JSON.stringify(res));
    }
  }); // Set the sandbox retention state.
}
```

## dlpPermission.cancelRetentionState

cancelRetentionState(docUris: Array&lt;string&gt;): Promise&lt;void&gt;

Cancels the sandbox retention state, that is, allows the sandbox application to be automatically uninstalled when the DLP file is closed. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| docUris | Array&lt;string&gt; | Yes| URIs of the files to be set with the retention state. The array has no length limit, but each string cannot exceed 4,095 bytes. Otherwise, **null** is returned.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
await dlpPermission.cancelRetentionState([uri]); // Cancel the sandbox retention state.
```

## dlpPermission.cancelRetentionState

cancelRetentionState(docUris: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Cancels the sandbox retention state, that is, allows the sandbox application to be automatically uninstalled when the DLP file is closed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| docUris | Array&lt;string&gt; | Yes| URIs of the files to be set with the retention state. The array has no length limit, but each string cannot exceed 4,095 bytes. Otherwise, **null** is returned.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
dlpPermission.cancelRetentionState([uri], (err, res) => {
  if (err != undefined) {
    console.error('cancelRetentionState error,', err.code, err.message);
  } else {
    console.info('cancelRetentionState success');
  }
}); // Cancel the sandbox retention state.
```

## dlpPermission.getRetentionSandboxList

getRetentionSandboxList(bundleName?: string): Promise&lt;Array&lt;RetentionSandboxInfo&gt;&gt;

Obtains the sandbox applications in the retention state of an application. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | No| Bundle name of the application. By default, this parameter is left empty, which obtains the sandbox retention information about the current application. The value contains 7 to 128 bytes. If the value exceeds this range, **null** is returned.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[RetentionSandboxInfo](#retentionsandboxinfo)&gt;&gt; | Promise used to return the sandbox retention information obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let res:Array<dlpPermission.RetentionSandboxInfo> = await dlpPermission.getRetentionSandboxList(); // Obtain the sandbox apps in the retention state.
console.info('res', JSON.stringify(res));
```

## dlpPermission.getRetentionSandboxList

getRetentionSandboxList(bundleName: string, callback: AsyncCallback&lt;Array&lt;RetentionSandboxInfo&gt;&gt;): void

Obtains the sandbox applications in the retention state of an application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name of the application. The value contains 7 to 128 bytes. If the value exceeds this range, **null** is returned.|
| callback | AsyncCallback&lt;Array&lt;[RetentionSandboxInfo](#retentionsandboxinfo)&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.getRetentionSandboxList("bundleName", (err, res) => {
  if (err != undefined) {
    console.error('getRetentionSandboxList error,', err.code, err.message);
  } else {
    console.info('res', JSON.stringify(res));
  }
}); // Obtain the sandbox retention information.
```

## dlpPermission.getRetentionSandboxList

getRetentionSandboxList(callback: AsyncCallback&lt;Array&lt;RetentionSandboxInfo&gt;&gt;): void

Obtains the sandbox applications in the retention state of an application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;[RetentionSandboxInfo](#retentionsandboxinfo)&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.getRetentionSandboxList((err, res) => {
  if (err != undefined) {
    console.error('getRetentionSandboxList error,', err.code, err.message);
  } else {
    console.info('res', JSON.stringify(res));
  }
}); // Obtain the sandbox retention information.
```

## dlpPermission.getDLPFileAccessRecords

getDLPFileAccessRecords(): Promise&lt;Array&lt;AccessedDLPFileInfo&gt;&gt;

Obtains the list of DLP files that are accessed recently. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[AccessedDLPFileInfo](#accesseddlpfileinfo)&gt;&gt; | Promise used to return the list of recently accessed files obtained.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let res:Array<dlpPermission.AccessedDLPFileInfo> = await dlpPermission.getDLPFileAccessRecords(); // Obtain the list of recently accessed DLP files.
console.info('res', JSON.stringify(res));
```

## dlpPermission.getDLPFileAccessRecords

getDLPFileAccessRecords(callback: AsyncCallback&lt;Array&lt;AccessedDLPFileInfo&gt;&gt;): void

Obtains the list of DLP files that are accessed recently. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;[AccessedDLPFileInfo](#accesseddlpfileinfo)&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.getDLPFileAccessRecords((err, res) => {
  if (err != undefined) {
    console.error('getDLPFileAccessRecords error,', err.code, err.message);
  } else {
    console.info('res', JSON.stringify(res));
  }
}); // Obtain the list of recently accessed DLP files.
```

## dlpPermission.startDLPManagerForResult<sup>11+</sup>

startDLPManagerForResult(context: common.UIAbilityContext, want: Want): Promise&lt;DLPManagerResult&gt;

Starts the DLP manager application on the current [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability page in borderless mode. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called only by domain accounts.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [common.UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes| [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) context.|
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| Object that requests the start of the DLP manager application.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[DLPManagerResult](#dlpmanagerresult11)&gt; | Promise used to return the **DLPManagerResult** object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |
| 19100016 | The uri field is missing in the want parameter. |
| 19100017 | The displayName field is missing in the want parameter. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { common, Want } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

let context = new UIContext().getHostContext() as common.UIAbilityContext; // Obtain the current UIAbilityContext.
let want: Want = {
  "uri": "file://docs/storage/Users/currentUser/Desktop/1.txt",
  "parameters": {
    "displayName": "1.txt"
  }
}; // Request parameters.
dlpPermission.startDLPManagerForResult(context, want).then((res) => {
  console.info('res.resultCode', res.resultCode);
  console.info('res.want', JSON.stringify(res.want));
}); // Start the DLP manager application.
```

## dlpPermission.setSandboxAppConfig<sup>11+<sup>
setSandboxAppConfig(configInfo: string): Promise&lt;void&gt;

Sets sandbox application configuration. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| configInfo | string | Yes| Sandbox application configuration. The length must be less than 4 MB. If the value exceeds this range, **null** is returned.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |
| 19100018 | The application is not authorized. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

await dlpPermission.setSandboxAppConfig('configInfo'); // Set sandbox application configuration.
```

## dlpPermission.cleanSandboxAppConfig<sup>11+<sup>
cleanSandboxAppConfig(): Promise&lt;void&gt;

Cleans sandbox application configuration. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |
| 19100018 | The application is not authorized. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

await dlpPermission.cleanSandboxAppConfig(); // Clear the sandbox application configuration.
```

## dlpPermission.getSandboxAppConfig<sup>11+<sup>
getSandboxAppConfig(): Promise&lt;string&gt;

Obtains sandbox application configuration. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**
| Type| Description|
| -------- | -------- |
| Promise\<string> | Promise used to return the sandbox application configuration obtained. The length is less than 4 MB.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |
| 19100018 | The application is not authorized. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let res = await dlpPermission.getSandboxAppConfig() // Obtain the sandbox application configuration.
console.info('res', JSON.stringify(res));
```

## dlpPermission.isDLPFeatureProvided<sup>12+<sup>
isDLPFeatureProvided(): Promise&lt;boolean&gt;

Queries whether the current system provides the data encryption feature. This API uses a promise to return the result.

>**NOTE**
>
> This API is enabled by the [MDM](../../mdm/mdm-kit-intro.md) kit and is used for enterprise devices. For other devices (such as consumer devices), this API is inapplicable. Calling it returns **false**.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**
| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise object. The value **true** means the current system provides the data encryption feature; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

dlpPermission.isDLPFeatureProvided().then((res) => {
  console.info('res', JSON.stringify(res));
}).catch((err: BusinessError) => {
  console.error('error', (err as BusinessError).code, (err as BusinessError).message); // Throw an error if the operation fails.
});
```

## dlpPermission.setEnterprisePolicy<sup>21+</sup>

setEnterprisePolicy(policy: EnterprisePolicy): void

Sets the protection policy for enterprise applications.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| policy | [EnterprisePolicy](#enterprisepolicy21) | Yes| Protection policy to be set for enterprise applications.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |
| 19100021 | Failed to set the enterprise policy. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

interface Attribute {
  attributeId: string;
  attributeValues: Array<string>;
  valueType: number;
  opt: number;
}

interface Rule {
  ruleId: string;
  attributes: Array<Attribute>;
}

interface Policy {
  rules: Array<Rule>;
  policyId: string;
  ruleConflictAlg: number;
}

try {
  let attributeValues: Array<string> = [ '1' ];
  let attribute: Attribute = {
    attributeId: 'DeviceHealthyStatus',
    attributeValues: attributeValues,
    valueType: 0,
    opt: 2
  }; // Attribute information
  let rule: Rule = {
    ruleId: 'ruleId',
    attributes: [ attribute ]
  }; // Rules
  let policy: Policy = {
    rules: [ rule ],
    policyId: 'policyId',
    ruleConflictAlg: 0
  }; // Policy
  let enterprisePolicy: dlpPermission.EnterprisePolicy = {
    policyString: JSON.stringify(policy)
  };
  dlpPermission.setEnterprisePolicy(enterprisePolicy);
  console.info('set enterprise policy success');
} catch (err) {
  console.error('error:' + err.code + err.message); // Throw an error if the operation fails.
}
```

## ActionFlagType

Enumerates the operations that can be performed on a DLP file. For example, the DLP sandbox application can dim its button based on this parameter.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Value| Description|
| -------- | -------- | -------- |
| ACTION_VIEW | 0x00000001 | View the file.|
| ACTION_SAVE | 0x00000002 | Save the file.|
| ACTION_SAVE_AS | 0x00000004 | Save the file as another file.|
| ACTION_EDIT | 0x00000008 | Edit the file.|
| ACTION_SCREEN_CAPTURE | 0x00000010 | Capture screenshots of the file.|
| ACTION_SCREEN_SHARE | 0x00000020 | Share the screen of the file.|
| ACTION_SCREEN_RECORD | 0x00000040 | Record the screen on which the file is open.|
| ACTION_COPY | 0x00000080 | Copy the file.|
| ACTION_PRINT | 0x00000100 | Print the file.|
| ACTION_EXPORT | 0x00000200 | Export the file.|
| ACTION_PERMISSION_CHANGE | 0x00000400 | Modify the permissions on the file.|

## DLPFileAccess

Enumerates the permissions on a DLP file.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Value| Description|
| -------- | -------- | -------- |
| NO_PERMISSION | 0 | The user has no permission on the file.|
| READ_ONLY | 1 | The user has only the permission to read the file.|
| CONTENT_EDIT | 2 | Edit the file.|
| FULL_CONTROL | 3 | The user has full control on the file.|

## DLPPermissionInfo

Represents the permission information about a DLP file.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| dlpFileAccess | [DLPFileAccess](#dlpfileaccess) | No| No| User permission on the DLP file, for example, read-only.|
| flags | number | No| No| Operations that can be performed on the DLP file. It is a combination of different [ActionFlagTypes](#actionflagtype).|

## AccessedDLPFileInfo

Represents the information about a DLP file opened.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| uri | string | No| No| URI of the DLP file. The value contains up to 4095 bytes.|
| lastOpenTime | number | No| No| Time when the file was last opened. The value must be greater than or equal to 0.|

## DLPManagerResult<sup>11+</sup>

Represents information about the trigger of the DLP manager application.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| resultCode | number | No| No| Result code returned after the DLP manager application is started and exits. The value ranges from 0 to 3.|
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | No| No| Data returned after the DLP manager application is started and exits.|

## RetentionSandboxInfo

Represents the sandbox retention information.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| appIndex | number | No| No| Index of the DLP sandbox application. The value ranges from 1001 to 1100.|
| bundleName | string | No| No| Bundle name of the application. The value contains 7 to 128 bytes.|
| docUris | Array&lt;string&gt; | No| No| URI list of the DLP files. The array has no length limit, but each string cannot exceed 4095 bytes.|

## EnterprisePolicy<sup>21+</sup>

Represents an enterprise custom policy.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| policyString | string | No| No| JSON string of an enterprise custom policy. The length cannot exceed 4 MB.|

## dlpPermission.generateDlpFileForEnterprise<sup>21+</sup>

generateDlpFileForEnterprise(plaintextFd: number, dlpFd: number, property: DLPProperty, customProperty: CustomProperty): Promise&lt;void&gt;

Obtains a **DLPFile** object. This API uses a promise to return the result.

> **NOTE**
>
> This API can be called only by enterprise accounts. Enterprises need to set up their own enterprise account servers. This API generates a DLP file, which is an encrypted file that can be accessed only by accounts authorized by the enterprise server.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| plaintextFd | number | Yes| FD of a plaintext file. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, **false** is returned. If the value of **fd** is greater than 2<sup>31</sup>-1, the value is truncated.|
| dlpFd | number | Yes| FD of an encrypted file. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, **false** is returned. If the value of **fd** is greater than 2<sup>31</sup>-1, the value is truncated.|
| property | [DLPProperty](#dlpproperty21) | Yes| General policy of DLP files.|
| customProperty | [CustomProperty](#customproperty21) | Yes| Enterprise custom policy.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100001 | Invalid parameter value. |
| 19100002 | Credential service busy due to too many tasks or duplicate tasks. |
| 19100003 | Credential task time out. |
| 19100004 | Credential service error. |
| 19100005 | Credential authentication server error. |
| 19100009 | Failed to operate the DLP file. |
| 19100011 | The system ability works abnormally. |
| 19100014 | Account not logged in. |
  
**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let plaintextFd: number | undefined = undefined;
let dlpFd: number | undefined = undefined;
plaintextFd = fileIo.openSync(plainFilePath, fileIo.OpenMode.READ_ONLY).fd;
dlpFd = fileIo.openSync(dlpFilePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE).fd;
let dlpProperty: dlpPermission.DLPProperty = {
   ownerAccount: 'zhangsan',
   ownerAccountType: dlpPermission.AccountType.DOMAIN_ACCOUNT,
   authUserList: [],
   contactAccount: 'zhangsan',
   offlineAccess: true,
   ownerAccountID: 'xxxxxxx',
   everyoneAccessList: []
 };
let customProperty: dlpPermission.CustomProperty = {
  enterprise: 'customProperty'
};
await dlpPermission.generateDlpFileForEnterprise(plaintextFd, dlpFd, dlpProperty, customProperty);
console.info('Successfully generate DLP file for enterprise.');
if (dlpFd) {
  fileIo.closeSync(dlpFd);
}
if (plaintextFd) {
  fileIo.closeSync(plaintextFd);
}
```

## dlpPermission.decryptDlpFile<sup>21+</sup>

decryptDlpFile(dlpFd: number, plaintextFd: number): Promise&lt;void&gt;

Decrypts a DLP file to generate a plaintext file. This API uses a promise to return the result.
>**NOTE**
>
> This API can be called only by enterprise accounts. Enterprises need to set up their own enterprise account servers. The enterprise server determines whether an account is authorized to decrypt DLP files.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| dlpFd | number | Yes| FD of the file to be decrypted. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, **false** is returned. If the value of **fd** is greater than 2<sup>31</sup>-1, the value is truncated.|
| plaintextFd | number | Yes| FD of the decrypted file. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, **false** is returned. If the value of **fd** is greater than 2<sup>31</sup>-1, the value is truncated.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100001 | Invalid parameter value. |
| 19100002 | Credential service busy due to too many tasks or duplicate tasks. |
| 19100003 | Credential task time out. |
| 19100004 | Credential service error. |
| 19100005 | Credential authentication server error. |
| 19100008 | The file is not a DLP file. |
| 19100009 | Failed to operate the DLP file. |
| 19100011 | The system ability works abnormally. |
| 19100013 | The user does not have the permission. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let plaintextFd: number | undefined = undefined;
let dlpFd: number | undefined = undefined;
plaintextFd = fileIo.openSync(plainFilePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE).fd;
dlpFd = fileIo.openSync(dlpFilePath, fileIo.OpenMode.READ_ONLY).fd;
await dlpPermission.decryptDlpFile(dlpFd, plaintextFd);
console.info('Successfully decrypt DLP file.');
if (dlpFd) {
   fileIo.closeSync(dlpFd);
}
if (plaintextFd) {
   fileIo.closeSync(plaintextFd);
}
```

## dlpPermission.queryDlpPolicy<sup>21+</sup>

queryDlpPolicy(dlpFd: number): Promise&lt;string&gt;

Parses the file header in a DLP file to obtain the DLP plaintext policy. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| dlpFd | number | Yes| FD of the file to be decrypted. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, **false** is returned. If the value of **fd** is greater than 2<sup>31</sup>-1, the value is truncated.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;string&gt; | Promise used to return the JSON string of the DLP policy. The length cannot exceed 4 MB.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100001 | Invalid parameter value. |
| 19100002 | Credential service busy due to too many tasks or duplicate tasks. |
| 19100003 | Credential task time out. |
| 19100004 | Credential service error. |
| 19100005 | Credential authentication server error. |
| 19100008 | The file is not a DLP file. |
| 19100009 | Failed to operate the DLP file. |
| 19100011 | The system ability works abnormally. |
| 19100013 | The user does not have the permission. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dlpFd : number | undefined = undefined;
dlpFd = fileIo.openSync(dlpFilePath, fileIo.OpenMode.READ_ONLY).fd;
let policy: string = await dlpPermission.queryDlpPolicy(dlpFd);
console.info('DLP policy:' + policy);
if (dlpFd) {
   fileIo.closeSync(dlpFd);
 }
```

## ActionType<sup>21+</sup>

Enumerates the actions to be performed when the file's permission expiration time is reached. The default value is **NOT_OPEN**.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Value| Description|
| -------- | -------- | -------- |
| NOT_OPEN | 0 | Users are not allowed to open the DLP file when the file's permission expiration time is reached.|
| OPEN | 1 | Logged-in users are allowed to edit the DLP file when the file's permission expiration time is reached.|
  
## AccountType<sup>21+</sup>

Enumerates the types of authorized accounts.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Value| Description|
| -------- | -------- | -------- |
| CLOUD_ACCOUNT | 1 | Cloud account.|
| DOMAIN_ACCOUNT | 2 | Domain account.|
| ENTERPRISE_ACCOUNT | 4 | Enterprise account.|

## CustomProperty<sup>21+</sup>

Represents a custom policy.


**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| enterprise | string | No| No| JSON string of an enterprise custom policy. The length cannot exceed 4 MB. If the value exceeds this range, **null** is returned.|
| options<sup>26+</sup> | [DlpFileQueryOptions](#dlpfilequeryoptions26) | No| Yes| Query options for DLP files.<br>**Model restriction**: This API can be used only in the stage model.|

## DLPProperty<sup>21+</sup>

Represents the authorization information.


**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| ownerAccount | string | No| No| Account of the owner who can set the permission. The value contains up to 255 bytes. If the value exceeds this range, **null** is returned.|
| ownerAccountID | string | No| No| Account ID of the owner. The value contains up to 255 bytes. If the value exceeds this range, **null** is returned.|
| ownerAccountType | [AccountType](#accounttype21) | No| No| Account type of the owner.|
| authUserList | Array&lt;[AuthUser](#authuser21)&gt; | No| Yes| List of users who are authorized to access the DLP file. By default, this parameter is left blank.|
| contactAccount | string | No| No| Account of the contact. The value contains up to 255 bytes. If the value exceeds this range, **null** is returned.|
| offlineAccess | boolean | No| No| Whether the file can be accessed offline. **true**: yes; **false**: no.|
| everyoneAccessList | Array&lt;[DLPFileAccess](js-apis-dlppermission.md#dlpfileaccess)&gt; | No| Yes| Permission granted to everyone. This parameter is left blank by default.|
| expireTime | number | No| Yes| Timestamp when the file permission has expired. This parameter is left blank by default. The value must be greater than or equal to 0. If the value is not within the range, **null** is returned.|
| actionUponExpiry | [ActionType](#actiontype21) | No| Yes| Whether the file can be opened after the permission expires (with the editing permission). This parameter is valid only when **expireTime** is not empty. This parameter is left empty by default.|
| fileId | string | No| Yes| System account ID. This parameter is left empty by default. The value contains up to 255 bytes. If the value exceeds this range, **null** is returned.|
| allowedOpenCount | number | No| Yes| Number of allowed opening times. This parameter is left empty by default. The value must be greater than or equal to 0. If the value is not within the range, **null** is returned.|
| waterMarkConfig<sup>23+</sup> | boolean | No| Yes| Whether watermarks are required. **true**: yes; **false**: no. This parameter is left empty by default.|
| countdown<sup>23+</sup> | number | No| Yes| Validity period for file viewing, in seconds. After the validity period expires, the file is automatically closed. This parameter is left empty by default. The value must be greater than or equal to 0. If the value is not within the range, **null** is returned.<br>**Model restriction**: This API can be used only in the stage model.|
| extensionFields<sup>24+</sup> | Record<string, Object> | No| Yes| Extended attribute of a DLP file. This parameter is left empty by default.<br>**Model restriction**: This API can be used only in the stage model.|

## AuthUser<sup>21+</sup>

Represents the user authorization information.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| authAccount | string | No| No| Account of the user who can access the DLP file. The value contains up to 255 bytes.|
| authAccountType | [AccountType](#accounttype21) | No| No| Type of the account.|
| dlpFileAccess | [DLPFileAccess](js-apis-dlppermission.md#dlpfileaccess) | No| No| Permission granted to the user.|
| permExpiryTime | number | No| No| Time when the authorization expires. The value must be greater than or equal to 0.|

## DlpConnPlugin<sup>21+</sup>

Registers the callback capability with the system ability (SA). This API is used in the **registerPlugin** API.

>**NOTE**
>
> [registerPlugin](#registerplugin21) requires identical parameters to this API. [connectServer](#connectserver21) is called by the SA and the parameters are returned through the callback.

### connectServer<sup>21+</sup>
connectServer(requestId: string, requestData: string, callback: Callback\<string\>): void
  
This API is called by the SA. After processing the cloud connection capability, it will be called as a callback in the SA.

>**NOTE**
>
> **connectServer** indicates a call from the system capability side to the frontend.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE since API version 26. ohos.permission.ENTERPRISE_ACCESS_DLP_FILE for API versions 21 to 24.

**System capability**: SystemCapability.Security.DataLossPrevention
  
**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| requestId | string | Yes| ID of the request transferred by the SA. No value range restriction is specified.|
| requestData | string | Yes| Data transferred by the SA. No value range restriction is specified.|
| callback | Callback\<string\>| Yes| API transferred by the SA, which is used for callback. No value range restriction is specified.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100011 | The system ability works abnormally. |

 
## DlpConnManager<sup>21+</sup>
  
Calls **registerPlugin** and **unregisterPlugin** to register and deregister callback capabilities in the SA.

>**NOTE**
>
> **registerPlugin** registers callback capabilities in the SA, and **unregisterPlugin** deregisters callback capabilities from the SA.

### constructor<sup>21+</sup>

constructor()

Represents a constructor for instantiating [DlpConnManager](#dlpconnmanager21).
 
**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE since API version 26. ohos.permission.ENTERPRISE_ACCESS_DLP_FILE for API versions 21 to 24.
 
**System capability**: SystemCapability.Security.DataLossPrevention

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |

### registerPlugin<sup>21+</sup>
static registerPlugin(plugin: DlpConnPlugin): number
  
Registers a callback with the SA.

>**NOTE**
>
> **registerPlugin** registers the callback with the SA.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE since API version 26. ohos.permission.ENTERPRISE_ACCESS_DLP_FILE for API versions 21 to 24.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| plugin | [DlpConnPlugin](#dlpconnplugin21) | Yes|Callback capability.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Registration result, which indicates the ID of the callback. The value range is [0, 2<sup>64</sup>-1].|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100001 | Invalid parameter value. |
| 19100002 | Credential service busy due to too many tasks or duplicate tasks. |
| 19100003 | Credential task time out. |
| 19100004 | Credential service error. |

### unregisterPlugin<sup>21+</sup>
static unregisterPlugin(): void
  
Unregisters a callback from the SA.

>**NOTE**
>
> **unregisterPlugin** deregisters a plug-in from the SA.
  
**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE since API version 26. ohos.permission.ENTERPRISE_ACCESS_DLP_FILE for API versions 21 to 24.

**System capability**: SystemCapability.Security.DataLossPrevention

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100001 | Invalid parameter value. |
| 19100002 | Credential service busy due to too many tasks or duplicate tasks. |
| 19100003 | Credential task time out. |
| 19100004 | Credential service error. |

```
## DlpFileQueryOptions<sup>26+</sup>

Represents query options for DLP files.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| classificationLabel | string | No| Yes| User-defined classification label for an enterprise DLP file. The value contains up to 255 bytes. |

## dlpPermission.queryOpenedEnterpriseDlpFiles<sup>26+</sup>

queryOpenedEnterpriseDlpFiles(options?: DlpFileQueryOptions): Promise&lt;Array&lt;string&gt;&gt;

Queries the list of URIs of DLP files that have been opened and matched the specified options. This API uses a promise to return the result.

>**NOTE**
>
> - This API can only query DLP files generated by the caller application using [generateDlpFileForEnterprise](#dlppermissiongeneratedlpfileforenterprise21). DLP files generated by other applications cannot be queried.
> - DLP files with the same classification label are opened in the same sandbox. If multiple DLP files with the same label are opened in a sandbox, the query result returns the URIs of all these files. Even if some files are manually closed by the user, the URIs of all opened files (including those manually closed) are still returned as long as at least one file remains open in the sandbox. When all files in the sandbox are closed and the sandbox is uninstalled, the query result becomes empty.
> - If **options** is not specified, or if **classificationLabel** in **options** is not specified or is an empty string, all DLP files of all labels are queried.

**Model restriction**: This API can be used only in the stage model.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [DlpFileQueryOptions](#dlpfilequeryoptions26) | No| Query options for DLP files. If this parameter is not specified, all DLP files are queried.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the list of URIs of the target DLP files that have been opened.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 801 | Capability not supported. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let options: dlpPermission.DlpFileQueryOptions = {
  classificationLabel: 'label1'
};
dlpPermission.queryOpenedEnterpriseDlpFiles(options).then((uris: Array<string>) => {
  console.info("try to query opened enterprise dlp files, result: ", JSON.stringify(uris));
}).catch((error: BusinessError)=> {
  console.error(error.message);
}).finally(()=> {
  console.info("after query opened enterprise dlp files");
});
```

## dlpPermission.closeOpenedEnterpriseDlpFiles<sup>26+</sup>

closeOpenedEnterpriseDlpFiles(options?: DlpFileQueryOptions): Promise&lt;void&gt;

Closes all currently open DLP files that match the specified options. This API uses a promise to return the result.

>**NOTE**
>
> - This API can only close DLP files generated by the caller application using [generateDlpFileForEnterprise](#dlppermissiongeneratedlpfileforenterprise21). DLP files generated by other applications cannot be closed.
> - If **options** is not specified, or if **classificationLabel** in **options** is not specified or is an empty string, all DLP files of all labels are closed.

**Model restriction**: This API can be used only in the stage model.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [DlpFileQueryOptions](#dlpfilequeryoptions26) | No| Query options for DLP files. If this parameter is not specified, all DLP files are closed.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 801 | Capability not supported. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { BusinessError } from '@kit.BasicServicesKit';

let options: dlpPermission.DlpFileQueryOptions = {
  classificationLabel: 'label1'
};
dlpPermission.closeOpenedEnterpriseDlpFiles(options).then(() => {
  console.info("try to close opened enterprise dlp files");
}).catch((error: BusinessError)=> {
  console.error(error.message);
}).finally(()=> {
  console.info("after close opened enterprise dlp files");
});
```