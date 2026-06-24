# @ohos.dlpPermission (DLP)
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

Data loss prevention (DLP) is a system solution provided to prevent data disclosure. This module provides APIs for cross-device file access management, encrypted storage, and access authorization. DLP protects sensitive files through encryption and generates encrypted files in .dlp format. When opening a DLP file, the system automatically creates an isolated DLP sandbox environment to ensure that the file content is not leaked to unauthorized environments. Fine-grained permission control is supported for enterprise DLP files, including management of permissions to view, edit, copy, print, and screen-record files.

**Use scenarios**
- Protect sensitive documents of enterprises from unauthorized access and disclosure.
- Ensure secure document transfer between different devices.
- Implement fine-grained permissions control during document sharing and collaboration.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The kit to which **@ohos.dlpPermission** belongs has been changed from `DataLossPreventionKit` to `DataProtectionKit`. You are advised to use the new module name `@kit.DataProtectionKit` to import the module. If `@kit.DataLossPreventionKit` is imported, only the APIs before the change can be called and the APIs after the change cannot be used.

## Key Classes and APIs

### Key Enums
- **ActionFlagType**: enumerates the executable operation types of DLP files, which is used for fine-grained permission control.
- **DLPFileAccess**: enumerates the permissions on a DLP file, which defines the file access level.
- **ActionType**: enumerates the actions to be performed after the file permission expires.
- **AccountType**: enumerates the types of authorized accounts.

### Key APIs

- **CustomProperty**: represents a custom policy, including a JSON string of an enterprise custom policy and the query options about an enterprise DLP file.
- **DLPProperty**: represents authorization information, including the account of the owner who can set the permission, the account ID, and the account type.
- **AuthUser**: represents the authorized user data, including the account of the user who can access the DLP file, the account type, and granted permissions.
- **DlpConnPlugin**: registers a callback for returning the cloud-based authentication result, including the server connection method. The parameters include the request ID, request data, and callback function.

### Key Callbacks

- **Callback\<AccessedDLPFileInfo>**: callback for accessing information about a DLP file, which is used to subscribe to a DLP file open event.
- **AsyncCallback\<DLPPermissionInfo>**: asynchronous callback for DLP permission information, which is used to return the sandbox permission query result.
- **AsyncCallback\<Array\<RetentionSandboxInfo>>**: asynchronous callback for the sandbox applications in the retention state, which is used to return the sandbox query result.
- **AsyncCallback\<Array\<AccessedDLPFileInfo>>**: asynchronous callback for the DLP file access records, which is used to return the file access records.

### Key Classes

- **DlpConnManager**: core management class of the DLP system, which is used to register or unregister the callback capability in the system ability (SA).

![](figures/normal_dlpPermission_main_class.png)

## APIs Called in Pairs

| API Called First| API Called in Pairs| Description|
|---------|---------|------|
| on('openDLPFile', listener) | off('openDLPFile', listener) | Subscribe to a DLP file open event. When the page is destroyed or subscription is no longer needed, unsubscribe from the event to release resources.|
| DlpConnManager.registerPlugin() | DlpConnManager.unregisterPlugin() | Register the callback capability in the SA. Unregister the capability when the app exits or the capability is no longer needed.|
| setRetentionState() | cancelRetentionState() | Set the retention state for sandbox applications to quickly reopen files. Cancel the retention state when it is no longer needed to release system resources.|
| setSandboxAppConfig() | cleanSandboxAppConfig() | Set the custom configuration for sandbox applications. After the configuration is used, clear the configuration to restore the default status. |
| generateDlpFileForEnterprise() | decryptDlpFile() | Encrypt a plaintext file to generate an enterprise DLP file, or decrypt a DLP file to restore it to a plaintext file. The two operations are reverse of each other.|
| setSandboxAppConfig() | getSandboxAppConfig() | After setting the sandbox configuration, check whether the configuration has taken effect or read the current configuration status using the query API.|
| isInSandbox() | getDLPPermissionInfo() | After determining that the application is in a DLP sandbox environment, call the permission query API to obtain specific permissions to control the application behavior.|
| isDLPFile() | getOriginalFileName() | After confirming that a file is a DLP file, obtain the original file name to determine the file type and select a suitable application to open the file.|
| isDLPFeatureProvided() | generateDlpFileForEnterprise() or startDLPManagerForResult()| After confirming that the system supports the DLP encryption feature, call related APIs to avoid execution failures on devices that do not support this feature.|

## Modules to Import

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
```

## dlpPermission.isDLPFile

isDLPFile(fd: number): Promise&lt;boolean&gt;

Checks whether a file is a DLP file based on the FD. This API uses a promise to return the result.

During file processing, the system checks whether the file is a DLP file and then determines the subsequent processing policy. For example, whether to open the file in a DLP sandbox.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fd | number | Yes| FD of the file to be checked. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, error code 19100001 is thrown. If the value of **fd** is greater than 2<sup>31</sup>-1, the excess part will be truncated.|

**Return value**
| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the file is a DLP file; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';

let uri = "file://docs/storage/Users/currentUser/Documents/test.txt.dlp";
let file: number | undefined = undefined;
file = fileIo.openSync(uri).fd;
dlpPermission.isDLPFile(file).then((isDLPFile: boolean) => {
    console.info(JSON.stringify(isDLPFile));
}).catch((error: BusinessError)=> {
    console.error(error.message);
}).finally(()=> {
    if (file !== undefined) {
        fileIo.closeSync(file);
    }
});
```

## dlpPermission.isDLPFile

isDLPFile(fd: number, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a file is a DLP file based on the FD. After the API is successfully called, a result is returned. The value **true** means the file is a DLP file; the value **false** means the opposite. This API uses an asynchronous callback to return the result.

During file processing, the system checks whether the file is a DLP file and then determines the subsequent processing policy. For example, whether to open the file in a DLP sandbox.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fd | number | Yes| FD of the file to be checked. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, error code 19100001 is thrown. If the value of **fd** is greater than 2<sup>31</sup>-1, the excess part will be truncated.|
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to receive the query result. The callback parameters include **err** and **res**. **err** is **undefined** when the query is successful; otherwise, **err** is an error object. If **true** is returned, **res** is a DLP file; if **false** is returned, **res** is not a DLP file.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
let file: number | undefined = undefined;
file = fileIo.openSync(uri).fd;
dlpPermission.isDLPFile(file, (err, isDLPFile) => {
 if (err != undefined) {
    console.error('isDLPFile error,', err.code, err.message);
  } else {
    console.info('isDLPFile:', isDLPFile);
  }
  fileIo.closeSync(file);
});
```

## dlpPermission.getDLPPermissionInfo

getDLPPermissionInfo(): Promise&lt;DLPPermissionInfo&gt;

Queries the permission information of the current DLP sandbox, including permissions on the file and operations that can be performed (such as viewing, editing, and copying). This API can be called only in DLP sandbox applications. This API uses a promise to return the result.

When processing files in the DLP sandbox, the system determines the operations that can be performed for the current user to prevent calling unauthorized capabilities.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[DLPPermissionInfo](#dlppermissioninfo)&gt; | Promise used to return the permission information about the DLP file. The operation is successful if no error is reported.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100006 | No permission to call this API, which is available only for DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox().then(async (inSandbox) => { // Check whether the application is running in a sandbox.
  if (inSandbox) {
    dlpPermission.getDLPPermissionInfo().then((permissionInfo: dlpPermission.DLPPermissionInfo) => {
      console.info('permissionInfo', JSON.stringify(permissionInfo));
    }).catch((error: BusinessError)=> {
      console.error(JSON.stringify(error));
    })
  }
});
```

## dlpPermission.getDLPPermissionInfo

getDLPPermissionInfo(callback: AsyncCallback&lt;DLPPermissionInfo&gt;): void

Obtains the permission information of this DLP file. The returned permission information includes permissions on the file and operations that can be performed (such as viewing, editing, and copying). This API can be called only in DLP sandbox applications. This API uses an asynchronous callback to return the result.

When processing files in the DLP sandbox, the system determines the operations that can be performed for the current user to prevent calling unauthorized capabilities.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;[DLPPermissionInfo](#dlppermissioninfo)&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100006 | No permission to call this API, which is available only for DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox().then((inSandbox) => { // Check whether the application is running in a sandbox.
  if (inSandbox) {
    dlpPermission.getDLPPermissionInfo((err, permissionInfo) => { 
      if (err != undefined) {
        console.error('getDLPPermissionInfo error', err.code, err.message);
      } else {
        console.info('permissionInfo', JSON.stringify(permissionInfo));
      }
    }); // Obtain the permission information.
  }
});
```

## dlpPermission.getOriginalFileName

getOriginalFileName(fileName: string): string

Obtains the original name of a DLP file. This API returns the result synchronously.

Determine the file type based on the original file name extension and select an application to open the file.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fileName | string | Yes| Name of the target DLP file. The value contains a maximum of 255 bytes. If the value is out of range, error code 19100001 is thrown.|

**Return value**

| Type| Description|
| -------- | -------- |
| string | Original name of the DLP file obtained. For example, if the DLP file name is **test.txt.dlp**, the original file name returned is **test.txt**. The value contains up to 255 bytes.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

let originalFileName = dlpPermission.getOriginalFileName('test.txt.dlp'); // Obtain the original file name.
console.info('originalFileName:', originalFileName);
```

## dlpPermission.getDLPSuffix

getDLPSuffix(): string

Obtains the DLP file name extension. After the API is called successfully, the DLP file name extension (for example, .dlp) is returned. This API returns the result synchronously.

This API is used to obtain the standard extension of the DLP file, which can be used to construct the DLP file name or the determination of the file type.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| string | DLP file name extension obtained. For example, if the original file name is **test.txt**, the encrypted DLP file name is **test.txt.dlp**, and the returned extension is **.dlp**.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

let dlpSuffix = dlpPermission.getDLPSuffix(); // Obtain the DLP file name extension.
console.info('dlpSuffix:', dlpSuffix);
```

## dlpPermission.on('openDLPFile')

on(type: 'openDLPFile', listener: Callback&lt;AccessedDLPFileInfo&gt;): void

Subscribes to a DLP file open event. After this API is successfully called, a callback notification is sent to the current application when the DLP file is opened. This API can be called only in non-DLP sandbox applications.

 You can subscribe to this event when your application needs to perform specific operations (such as logging and updating the UI) after a DLP file is opened.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'openDLPFile' | Yes| Event type. It has a fixed value of **openDLPFile**, which indicates the DLP file open event.|
| listener | Callback&lt;[AccessedDLPFileInfo](#accesseddlpfileinfo)&gt; | Yes| Callback invoked when a DLP file is opened. The application will be notified when the DLP file is opened.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.on('openDLPFile', (info: dlpPermission.AccessedDLPFileInfo) => {
  console.info('openDlpFile event', info.uri, info.lastOpenTime);
}); // Subscribe to the DLP file open event.
```

## dlpPermission.off('openDLPFile')

off(type: 'openDLPFile', listener?: Callback&lt;AccessedDLPFileInfo&gt;): void

Unsubscribes from the DLP file open event. This API can be called only in non-DLP sandbox applications. After the API is successfully called, the application will no longer receive notifications for the DLP file open event.

This API is usually called to release resources when the page is destroyed or the subscription is no longer needed.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**
| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | 'openDLPFile' | Yes| Event type. It has a fixed value of **openDLPFile**, which indicates the DLP file open event.|
| listener | Callback&lt;[AccessedDLPFileInfo](#accesseddlpfileinfo)&gt; | No| Callback for the DLP file open event. This parameter is passed when a specific callback (registered before the parameter is passed) needs to be unregistered. This parameter does not need to be passed when all callbacks need to be unregistered. By default, this parameter is left blank, which unregisters all callbacks for the file open event. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.off('openDLPFile', (info: dlpPermission.AccessedDLPFileInfo) => {
  console.info('openDlpFile event', info.uri, info.lastOpenTime);
}); // Unsubscribe from the DLP file open event.
```

## dlpPermission.isInSandbox

isInSandbox(): Promise&lt;boolean&gt;

Checks whether this application is running in a DLP sandbox environment. This API uses a promise to return the result.

This API is used to determine whether the current application is running in a DLP sandbox environment. If it is, the system can perform operations or call APIs for sandbox applications.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the application is running in a sandbox; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox().then((isInSandbox) => { // Check whether the application is running in a sandbox.
  console.info('isInSandbox', isInSandbox);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

## dlpPermission.isInSandbox

isInSandbox(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether this application is running in a DLP sandbox environment. This API uses an asynchronous callback to return the result.

This API is used to determine whether the current application is running in a DLP sandbox environment. If it is, the system can perform operations or call APIs for sandbox applications.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. The value **true** means the application is running in a sandbox; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox((err, isInSandbox) => {
  if (err) {
    console.error('isInSandbox error', err.code, err.message);
  } else {
    console.info('isInSandbox: ', JSON.stringify(isInSandbox));
  }
}); // Whether the application is running in a sandbox.
```

## dlpPermission.getDLPSupportedFileTypes

getDLPSupportedFileTypes(): Promise&lt;Array&lt;string&gt;&gt;

Obtains the file name extension types that support DLP. After the API is successfully called, the list of supported file types is returned, indicating the types of files that can be used to generate DLP files. This API uses a promise to return the result.

This API is used to obtain the types of files that can be used to generate DLP files. If the current file type is in the list, it can be encrypted.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the file name extension types obtained.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPSupportedFileTypes().then((fileTypes) => { // Obtain the file types that support DLP.
  console.info('fileTypes', JSON.stringify(fileTypes));
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

## dlpPermission.getDLPSupportedFileTypes

getDLPSupportedFileTypes(callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Obtains the file name extension types that support DLP. After the API is successfully called, the list of supported file types is returned, indicating the types of files that can be used to generate DLP files. This API uses an asynchronous callback to return the result.

This API is used to obtain the types of files that can be used to generate DLP files. If the current file type is in the list, it can be encrypted.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPSupportedFileTypes((err, fileTypes) => {
  if (err != undefined) {
    console.error('getDLPSupportedFileTypes error', err.code, err.message);
  } else {
    console.info('fileTypes', JSON.stringify(fileTypes));
  }
}); // Obtain the file types that support DLP.
```

## dlpPermission.setRetentionState

setRetentionState(docUris: Array&lt;string&gt;): Promise&lt;void&gt;

Sets the retention state for sandbox applications. By default, when a DLP file is opened, the system automatically creates a sandbox environment. After the file is closed, the sandbox is automatically destroyed. After the retention state is set, the sandbox environment is retained even if the DLP file is closed, allowing the system to quickly reopen the same DLP file. This is applicable to scenarios where the same DLP file needs to be frequently operated, improving the file opening efficiency. This API can be called only in DLP sandbox applications. This API uses a promise to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| docUris | Array&lt;string&gt; | Yes| URIs of the files to be set with the retention state. The length of the array is not limited. Each string contains a maximum of 4095 bytes. If the string is out of range, error code 19100001 is thrown.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100006 | No permission to call this API, which is available only for DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
dlpPermission.isInSandbox().then(async (inSandbox) => {
  if (inSandbox) {
    await dlpPermission.setRetentionState([uri]); // Set the sandbox retention state.
  }
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
}); // Whether the application is running in a sandbox.
```

## dlpPermission.setRetentionState

setRetentionState(docUris: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Sets the retention state for sandbox applications. By default, when a DLP file is opened, the system automatically creates a sandbox environment. After the file is closed, the sandbox is automatically destroyed. After the retention state is set, the sandbox environment is retained even if the DLP file is closed, allowing the system to quickly reopen the same DLP file. This is applicable to scenarios where the same DLP file needs to be frequently operated, improving the file opening efficiency. This API can be called only in DLP sandbox applications. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| docUris | Array&lt;string&gt; | Yes| URIs of the files to be set with the retention state. The length of the array is not limited. Each string contains a maximum of 4095 bytes. If the string is out of range, error code 19100001 is thrown.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100006 | No permission to call this API, which is available only for DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
dlpPermission.isInSandbox().then((inSandbox) => { // Check whether the application is running in a sandbox.
  if (inSandbox) {
    dlpPermission.setRetentionState([uri], (err, retentionState) => {
      if (err != undefined) {
        console.error('setRetentionState error,', err.code, err.message);
      } else {
        console.info('setRetentionState success');
        console.info('retentionState: ', JSON.stringify(retentionState));
      }
    }); // Set the sandbox retention state.
  }
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

## dlpPermission.cancelRetentionState

cancelRetentionState(docUris: Array&lt;string&gt;): Promise&lt;void&gt;

Cancels the sandbox retention state, that is, allows the sandbox application to be automatically uninstalled when the DLP file is closed. This API uses a promise to return the result.

This API is used to cancel the retention state for sandbox application and restore the default behavior to release system resources. It is applicable to scenarios where the DLP file is no longer frequently accessed.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| docUris | Array&lt;string&gt; | Yes| URIs of the files to be canceled with the retention state. The length of the array is not limited. Each string contains a maximum of 4095 bytes. If the string is out of range, error code 19100001 is thrown.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = "file://docs/storage/Users/currentUser/Desktop/test.txt.dlp";
dlpPermission.cancelRetentionState([uri]).then(() => { // Cancel the retention state for a sandbox application.
  console.info('success!');
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

## dlpPermission.cancelRetentionState

cancelRetentionState(docUris: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Cancels the sandbox retention state, that is, allows the sandbox application to be automatically uninstalled when the DLP file is closed. This API uses an asynchronous callback to return the result.

This API is used to cancel the retention state for sandbox application and restore the default behavior to release system resources. It is applicable to scenarios where the DLP file is no longer frequently accessed.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| docUris | Array&lt;string&gt; | Yes| URIs of the files to be canceled with the retention state. The length of the array is not limited. Each string contains a maximum of 4095 bytes. If the string is out of range, error code 19100001 is thrown.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

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

Obtains the sandbox applications in the retention state of an application. This API can be called only in non-DLP sandbox applications. This API uses a promise to return the result.

This API is used to query the sandbox retention information of a specified application, so that the sandbox environment in the retention state can be checked or managed.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | No| Bundle name of the application, which is used to query the sandbox retention information of the application. This parameter is required when you need to query the sandbox retention information of another application. It is optional when you need to query the sandbox retention information of the current application. The value contains 7 to 128 bytes. If the value is out of range, error code 19100001 is thrown.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[RetentionSandboxInfo](#retentionsandboxinfo)&gt;&gt; | Promise used to return the sandbox retention information obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getRetentionSandboxList().then((sandboxList) => { // Obtain the sandbox retention information.
  console.info('sandboxList', JSON.stringify(sandboxList));
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

## dlpPermission.getRetentionSandboxList

getRetentionSandboxList(bundleName: string, callback: AsyncCallback&lt;Array&lt;RetentionSandboxInfo&gt;&gt;): void

Obtains the sandbox applications in the retention state of an application. This API can be called only in non-DLP sandbox applications. This API uses an asynchronous callback to return the result.

This API is used to query the sandbox retention information of a specified application, so that the sandbox environment in the retention state can be checked or managed.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name of the application, which is used to query the sandbox retention information of the application. The value contains 7 to 128 bytes. If the value is out of range, error code 19100001 is thrown.|
| callback | AsyncCallback&lt;Array&lt;[RetentionSandboxInfo](#retentionsandboxinfo)&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getRetentionSandboxList("bundleName", (err, sandboxList) => {
  if (err != undefined) {
    console.error('getRetentionSandboxList error,', err.code, err.message);
  } else {
    console.info('sandboxList', JSON.stringify(sandboxList));
  }
}); // Obtain the sandbox retention information.
```

## dlpPermission.getRetentionSandboxList

getRetentionSandboxList(callback: AsyncCallback&lt;Array&lt;RetentionSandboxInfo&gt;&gt;): void

Obtains the sandbox applications in the retention state of an application. This API uses an asynchronous callback to return the result.

This API is used to query the sandbox retention information of a specified application, so that the sandbox environment in the retention state can be checked or managed.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;[RetentionSandboxInfo](#retentionsandboxinfo)&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getRetentionSandboxList((err, retentionSandboxList) => {
  if (err != undefined) {
    console.error('getRetentionSandboxList error,', err.code, err.message);
  } else {
    console.info('res', JSON.stringify(retentionSandboxList));
  }
}); // Obtain the sandbox retention information.
```

## dlpPermission.getDLPFileAccessRecords

getDLPFileAccessRecords(): Promise&lt;Array&lt;AccessedDLPFileInfo&gt;&gt;

Obtains the list of DLP files that are accessed recently. After the API is successfully called, the file access records are returned, which can be used to track and manage the usage of DLP files. This API can be called only in non-DLP sandbox applications. This API uses a promise to return the result.

This API is used to obtain the list of DLP files that are accessed recently, which can be used to track and manage file usage.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[AccessedDLPFileInfo](#accesseddlpfileinfo)&gt;&gt; | Promise used to return the list of recently accessed DLP files obtained.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPFileAccessRecords().then((accessRecords) => { // Obtain the list of recently accessed DLP files.
  console.info('accessRecords', JSON.stringify(accessRecords));
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

## dlpPermission.getDLPFileAccessRecords

getDLPFileAccessRecords(callback: AsyncCallback&lt;Array&lt;AccessedDLPFileInfo&gt;&gt;): void

Obtains the list of DLP files that are accessed recently. After the API is successfully called, the file access records are returned, which can be used to track and manage the usage of DLP files. This API uses an asynchronous callback to return the result.

This API is used to obtain the list of DLP files that are accessed recently, which can be used to track and manage file usage.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;Array&lt;[AccessedDLPFileInfo](#accesseddlpfileinfo)&gt;&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getDLPFileAccessRecords((err, accessRecords) => {
  if (err != undefined) {
    console.error('getDLPFileAccessRecords error,', err.code, err.message);
  } else {
    console.info('accessRecords', JSON.stringify(accessRecords));
  }
}); // Obtain the list of recently accessed DLP files.
```

## dlpPermission.startDLPManagerForResult<sup>11+</sup>

startDLPManagerForResult(context: common.UIAbilityContext, want: Want): Promise&lt;DLPManagerResult&gt;

Starts the DLP manager application on the current [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) page in borderless mode. This API uses a promise to return the result.

This API starts the DLP manager application to configure file permissions and return the user operation result to the caller.

> **NOTE**
>
> This API can be called only by domain accounts.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [common.UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes| [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md#uiability) context.|
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes| Request object, which must contain the **uri** and **displayName** fields.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[DLPManagerResult](#dlpmanagerresult11)&gt; | Promise used to return the **DLPManagerResult** object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
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
if (context !== undefined) {
    let want: Want = {
        "uri": "file://docs/storage/Users/currentUser/Desktop/1.txt",
        "parameters": {
        "displayName": "1.txt"
        }
    }; // Construct request parameters, which must include uri and displayName.
    dlpPermission.startDLPManagerForResult(context, want).then((res) => {
        console.info('res.resultCode', res.resultCode);
        console.info('res.want', JSON.stringify(res.want));
    }); // Start the DLP manager application.
}
```

## dlpPermission.setSandboxAppConfig<sup>11+</sup>
setSandboxAppConfig(configInfo: string): Promise&lt;void&gt;

Sets the configuration information of the sandbox application. The configuration information is in JSON string format and can be set by the application. After the API is successfully called, the sandbox application runs based on the configuration information. This API uses a promise to return the result.

This API sets the sandbox application configuration so that the application can pass custom parameters as required.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| configInfo | string | Yes| Sandbox application configuration. The value contains a maximum of 2<sup>22</sup>-1 bytes. If the value is out of range, error code 19100001 is thrown.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |
| 19100018 | The application is not authorized. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.setSandboxAppConfig('configInfo').then((configInfo) => { // Set sandbox application configuration.
  console.info('configInfo: ', configInfo);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

## dlpPermission.cleanSandboxAppConfig<sup>11+</sup>
cleanSandboxAppConfig(): Promise&lt;void&gt;

Clears the sandbox application configuration. After the API is successfully called, the sandbox application configuration is cleared and the default state is restored. This API uses a promise to return the result.

This API clears the sandbox application configuration and restores the default state to prevent residual configurations from affecting subsequent use.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100007 | No permission to call this API, which is available only for non-DLP sandbox applications. |
| 19100011 | The system ability works abnormally. |
| 19100018 | The application is not authorized. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.cleanSandboxAppConfig().then((configInfo) => { // Clear sandbox application configuration.
  console.info('configInfo: ', configInfo);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

## dlpPermission.getSandboxAppConfig<sup>11+</sup>
getSandboxAppConfig(): Promise&lt;string&gt;

Obtains sandbox application configuration. This API uses a promise to return the result.

This API obtains the sandbox application configuration, which can be used to read or verify the current configuration status.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**
| Type| Description|
| -------- | -------- |
| Promise\<string> | Promise used to return the sandbox application configuration obtained. The length must be less than 4,194,304 bytes.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |
| 19100018 | The application is not authorized. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.getSandboxAppConfig().then((configInfo) => { // Obtain the sandbox application configuration.
  console.info('configInfo', configInfo);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```

## dlpPermission.isDLPFeatureProvided<sup>12+</sup>
isDLPFeatureProvided(): Promise&lt;boolean&gt;

Checks whether the current system provides the encryption protection feature. This API is available only for enterprise devices and must be enabled by the [MDM](../../mdm/mdm-kit-intro.md) kit. After the API is successfully called, the query result is returned, indicating whether the system supports DLP encryption. This API uses a promise to return the result.

This API checks whether the current system supports the DLP encryption function, so that compatibility processing or function degradation can be performed on devices that do not support this function.

> **NOTE**
>
> This API is enabled by the [MDM](../../mdm/mdm-kit-intro.md) kit and is used for enterprise devices. For other devices (such as consumer devices), this API is inapplicable. Calling it returns **false**.

**System capability**: SystemCapability.Security.DataLossPrevention

**Return value**
| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the current system provides the data encryption feature; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [DLP Service Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isDLPFeatureProvided().then((isFeatureProvided) => { // Check whether the current system provides the encryption protection feature.
  console.info('isFeatureProvided', JSON.stringify(isFeatureProvided));
}).catch((err: BusinessError) => {
  console.error('error', (err as BusinessError).code, (err as BusinessError).message); // Throw an error if the operation fails.
});
```

## dlpPermission.setEnterprisePolicy<sup>21+</sup>

setEnterprisePolicy(policy: EnterprisePolicy): void

Sets the protection policy for enterprise applications. After the API is successfully called, the DLP protection for enterprise applications is implemented based on the configured policy.

This API is used by the enterprise administrator to configure DLP security policies for unified management of data security protection rules.

> **NOTE**
>
> This API can be called only by enterprise accounts.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| policy | [EnterprisePolicy](#enterprisepolicy21) | Yes| Enterprise application protection policy to be set. Access control and behavior restrictions of enterprise DLP files are implemented based on the policy.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
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
| flags | number | No| No| Operations that can be performed on the DLP file. The value is determined by a combination of different [ActionFlagTypes](#actionflagtype).|

## AccessedDLPFileInfo

Represents the information about a DLP file opened.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| uri | string | No| No| URI of the DLP file. The value contains up to 4095 bytes.|
| lastOpenTime | number | No| No| Time when the file was last opened. Unit: s.|

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
| policyString | string | No| No| JSON string of an enterprise custom policy. The value contains a maximum of 2<sup>22</sup> bytes. If the value is out of range, error code 19100001 is thrown.|

## dlpPermission.generateDlpFileForEnterprise<sup>21+</sup>

generateDlpFileForEnterprise(plaintextFd: number, dlpFd: number, property: DLPProperty, customProperty: CustomProperty): Promise&lt;void&gt;

Encrypts a plaintext file to generate a DLP file for an enterprise account. This API can be called only by enterprise accounts. This API uses a promise to return the result.

This API encrypts a plaintext file to generate a DLP file that can be accessed only by enterprise accounts, implementing enterprise-level file permission management.

> **NOTE**
>
> This API can be called only by enterprise accounts. Enterprises need to set up their own enterprise account servers. This API generates a DLP file, which is an encrypted file that can be accessed only by accounts authorized by the enterprise server.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| plaintextFd | number | Yes| FD of a plaintext file. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, an error log is generated, and the function stops running. If the value of **fd** is greater than 2<sup>31</sup>-1, the excess part will be truncated.|
| dlpFd | number | Yes| FD of an encrypted file. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, an error log is generated, and the function stops running. If the value of **fd** is greater than 2<sup>31</sup>-1, the excess part will be truncated.|
| property | [DLPProperty](#dlpproperty21) | Yes| General policy of DLP files.|
| customProperty | [CustomProperty](#customproperty21) | Yes| Enterprise custom policy.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
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

let plaintextFd: number | undefined = undefined;
let dlpFd: number | undefined = undefined;
let plainFilePath: string = "file://docs/storage/Users/currentUser/Documents/test.txt";
let dlpFilePath: string = "file://docs/storage/Users/currentUser/Documents/test.txt.dlp";
plaintextFd = fileIo.openSync(plainFilePath, fileIo.OpenMode.READ_ONLY).fd; // Open a plaintext file.
dlpFd = fileIo.openSync(dlpFilePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE).fd; // Open a DLP file.
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
dlpPermission.generateDlpFileForEnterprise(plaintextFd, dlpFd, dlpProperty, customProperty).then((res) => {
  console.info('Successfully generate DLP file for enterprise.');
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
}).finally(()=>{
  if (dlpFd) {
    fileIo.closeSync(dlpFd);
  }
  if (plaintextFd) {
    fileIo.closeSync(plaintextFd);
  }
});
```

## dlpPermission.decryptDlpFile<sup>21+</sup>

decryptDlpFile(dlpFd: number, plaintextFd: number): Promise&lt;void&gt;

Decrypts a DLP file to generate a plaintext file. This API can be called only by enterprise accounts. This API uses a promise to return the result.

This API decrypts DLP files into plaintext files, which is applicable to exporting or migrating files by users with owner permissions.
> **NOTE**
>
> This API can be called only by enterprise accounts. Enterprises need to set up their own enterprise account servers. The enterprise server determines whether an account is authorized to decrypt DLP files.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| dlpFd | number | Yes| FD of the DLP file to be decrypted. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, an error log is generated, and the function stops running. If the value of **fd** is greater than 2<sup>31</sup>-1, the excess part will be truncated.|
| plaintextFd | number | Yes| FD of the decrypted file. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, an error log is generated, and the function stops running. If the value of **fd** is greater than 2<sup>31</sup>-1, the excess part will be truncated.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
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

let plaintextFd: number | undefined = undefined;
let dlpFd: number | undefined = undefined;
let plainFilePath: string = "file://docs/storage/Users/currentUser/Documents/test.txt";
let dlpFilePath: string = "file://docs/storage/Users/currentUser/Documents/test.txt.dlp";
plaintextFd = fileIo.openSync(plainFilePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE).fd; // Open the target plaintext file.
dlpFd = fileIo.openSync(dlpFilePath, fileIo.OpenMode.READ_ONLY).fd; // Open the DLP file to be decrypted.
dlpPermission.decryptDlpFile(dlpFd, plaintextFd).then((res) => {
  console.info('Successfully decrypt DLP file.');
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
}).finally(()=>{
  if (dlpFd) {
    fileIo.closeSync(dlpFd);
  }
  if (plaintextFd) {
    fileIo.closeSync(plaintextFd);
  }
});
```

## dlpPermission.queryDlpPolicy<sup>21+</sup>

queryDlpPolicy(dlpFd: number): Promise&lt;string&gt;

Parses the file header in a DLP file to obtain the DLP plaintext policy. The returned JSON string of the DLP policy contains the [DLPProperty](#dlpproperty21) and [CustomProperty](#customproperty21) information. This API uses a promise to return the result.

This API obtains the policy information of a DLP file for analysis in scenarios such as viewing the DLP file permission configuration.

> **NOTE**
>
> This API can be called only by enterprise accounts.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| dlpFd | number | Yes| FD of the DLP file to be queried. The value range is [0, 2<sup>31</sup>-1]. If the value of **fd** is less than 0, an error log is generated, and the function stops running. If the value of **fd** is greater than 2<sup>31</sup>-1, the excess part will be truncated.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;string&gt; | Promise used to return the JSON string of the DLP policy. The length cannot exceed 4,194,304 bytes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
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

let dlpFd : number | undefined = undefined; // FD of the DLP file to be queried.
let dlpFilePath: string = "file://docs/storage/Users/currentUser/Documents/test.txt.dlp"; // Specify the DLP file path.
dlpFd = fileIo.openSync(dlpFilePath, fileIo.OpenMode.READ_ONLY).fd; // Open the DLP file to obtain the descriptor.
dlpPermission.queryDlpPolicy(dlpFd).then((policy) => {
  console.info('DLP policy:' + policy);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
}).finally(()=>{
  if (dlpFd) {
    fileIo.closeSync(dlpFd);
  }
});
```

## ActionType<sup>21+</sup>

Enumerates the actions to be performed when the file's permission expiration time is reached. The default value is **NOT_OPEN**.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Value| Description|
| -------- | -------- | -------- |
| NOT_OPEN | 0 | Users are not allowed to open the DLP file when the file's permission expiration time is reached.|
| OPEN | 1 | Logged-in accounts can still open and edit the DLP file when the file's permission expiration time is reached.|
  
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
| enterprise | string | No| No| JSON string of an enterprise custom policy. The value contains a maximum of 2<sup>22</sup> bytes. If the value is out of range, error code 19100001 is thrown.|
| options | [DlpFileQueryOptions](#dlpfilequeryoptions) | No| Yes| Query options about an enterprise DLP file. This parameter is left blank by default. **Since**: 26.0.0 **Model restriction**: This API can be used only in the stage model.|

## DLPProperty<sup>21+</sup>

Represents the authorization information.


**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| ownerAccount | string | No| No| Account of the owner who can set the permission. The value contains a maximum of 255 bytes. If the value is out of range, error code 19100001 is thrown.|
| ownerAccountID | string | No| No| Account ID of the owner. The value contains a maximum of 255 bytes. If the value is out of range, error code 19100001 is thrown.|
| ownerAccountType | [AccountType](#accounttype21) | No| No| Account type of the owner.|
| authUserList | Array&lt;[AuthUser](#authuser21)&gt; | No| Yes| List of users who are authorized to access the DLP file. By default, this parameter is left blank.|
| contactAccount | string | No| No| Account of the contact. The value contains a maximum of 255 bytes. If the value is out of range, error code 19100001 is thrown.|
| offlineAccess | boolean | No| No| Whether the file can be accessed offline. **true**: yes; **false**: no.|
| everyoneAccessList | Array&lt;[DLPFileAccess](#dlpfileaccess)&gt; | No| Yes| Permission granted to everyone. This parameter is left blank by default.|
| expireTime | number | No| Yes| Timestamp when the file permission has expired. This parameter is left blank by default. The value must be greater than or equal to 0. If the value is out of range, an error code is thrown. Unit: s.|
| actionUponExpiry | [ActionType](#actiontype21) | No| Yes| Whether the file can be opened after the permission expires (with the editing permission). This parameter is valid only when **expireTime** is not empty. This parameter is left empty by default.|
| fileId | string | No| Yes| System account ID. This parameter is left empty by default. The value contains a maximum of 255 bytes. If the value is out of range, error code 19100001 is thrown.|
| allowedOpenCount | number | No| Yes| Number of allowed opening times. The default value is **0**. No value range restriction is specified.|
| waterMarkConfig<sup>23+</sup> | boolean | No| Yes| Whether watermarks are required. **true**: yes; **false**: no. This parameter is left empty by default.|
| countdown<sup>23+</sup> | number | No| Yes| Validity period for file viewing, in seconds. The default value is **0**. After the validity period expires, the file is automatically closed. The value must be greater than or equal to 0. No value range restriction is specified.<br>**Model restriction**: This API can be used only in the stage model.|
| extensionFields<sup>24+</sup> | Record<string, Object> | No| Yes| Extended attribute of a DLP file. This parameter is left empty by default.<br>**Model restriction**: This API can be used only in the stage model.|

## AuthUser<sup>21+</sup>

Represents the user authorization information.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| authAccount | string | No| No| Account of the user who can access the DLP file. The value contains a maximum of 255 bytes. If the value is out of range, error code 19100001 is thrown.|
| authAccountType | [AccountType](#accounttype21) | No| No| Type of the account.|
| dlpFileAccess | [DLPFileAccess](#dlpfileaccess) | No| No| Permission granted to the user.|
| permExpiryTime | number | No| No| Time when the authorization expires. The value must be greater than or equal to 0. If the value is out of range, it will be forcibly converted to an unsigned integer. Unit: s.|

## DlpConnPlugin<sup>21+</sup>

Registers the callback capability with the system ability (SA). This API is used in the **registerPlugin** API.

> **NOTE**
>
> [registerPlugin](#registerplugin21) requires identical parameters to this API. [connectServer](#connectserver21) is called by the SA and the parameters are returned through the callback.

### connectServer<sup>21+</sup>
connectServer(requestId: string, requestData: string, callback: Callback\<string\>): void

This API is called by the SA. After the request of connecting to the cloud server is processed, the result is returned the SA using a callback.

This API can be used in enterprise account authentication and cloud permission verification to enable communication between the SA and the cloud server.

> **NOTE**
>
> **connectServer** indicates a call from the system capability side to the frontend.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE since API version 26.0.0. ohos.permission.ENTERPRISE_ACCESS_DLP_FILE for API versions 21 to 24.

**System capability**: SystemCapability.Security.DataLossPrevention
  
**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| requestId | string | Yes| ID of the request transferred by the SA. No value range restriction is specified.|
| requestData | string | Yes| Data transferred by the SA. No value range restriction is specified.|
| callback | Callback\<string\>| Yes| API transferred by the SA, which is used for callback. No value range restriction is specified.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100011 | The system ability works abnormally. |
  
**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { Callback } from '@kit.BasicServicesKit';

export default class DataCapsulePlugin implements dlpPermission.DlpConnPlugin {
  constructor() {
  }

  connectServer(requestId: string, requestData: string, callback: Callback<string>): void {
    let callbackJson = JSON.stringify({
      'requestId': requestId,
    }); // Construct callback JSON data.
    callback(callbackJson);  // Use a callback to return the result.
  }
}

let plugin: dlpPermission.DlpConnPlugin = new DataCapsulePlugin();
```

 
## DlpConnManager<sup>21+</sup>
  
Calls **registerPlugin** and **unregisterPlugin** to register or unregister callback capabilities in the SA.

> **NOTE**
>
> **registerPlugin** registers callback capabilities in the SA, and **unregisterPlugin** unregisters callback capabilities from the SA.

### constructor<sup>21+</sup>

constructor()

Represents a constructor for instantiating [DlpConnManager](#dlpconnmanager21).
 
**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE since API version 26.0.0. ohos.permission.ENTERPRISE_ACCESS_DLP_FILE for API versions 21 to 24.
 
**System capability**: SystemCapability.Security.DataLossPrevention

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
  
**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

let dlpConnManager: dlpPermission.DlpConnManager = new dlpPermission.DlpConnManager();
```

### registerPlugin<sup>21+</sup>
static registerPlugin(plugin: DlpConnPlugin): number
  
Registers a callback with the SA.

> **NOTE**
>
> **registerPlugin** registers the callback with the SA.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE since API version 26.0.0. ohos.permission.ENTERPRISE_ACCESS_DLP_FILE for API versions 21 to 24.

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| plugin | [DlpConnPlugin](#dlpconnplugin21) | Yes|Callback plugin object, which is used to register the callback capability with the SA. The **DlpConnPlugin** API needs to be inherited and the **connectServer** method needs to be implemented so that the processing result can be returned using a callback when the API is called on the SA.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Registration result. The unique ID of the callback is returned. The value range is [0, 2<sup>64</sup>-1].|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100001 | Invalid parameter value. |
| 19100002 | Credential service busy due to too many tasks or duplicate tasks. |
| 19100003 | Credential task time out. |
| 19100004 | Credential service error. |
  
**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';
import { Callback } from '@kit.BasicServicesKit';

export default class DataCapsulePlugin implements dlpPermission.DlpConnPlugin {
  private accountId: string;
  private accountName: string;
  constructor() {
    this.accountId = 'accountId'; // Initialize account information.
    this.accountName = 'accountName';
  }

  connectServer(requestId: string, requestData: string, callback: Callback<string>): void {
    let callbackJson = JSON.stringify({
      'requestId': requestId,
    });
    callback(callbackJson);
  }
}
  
let pluginId: number = dlpPermission.DlpConnManager.registerPlugin(new DataCapsulePlugin());
```

### unregisterPlugin<sup>21+</sup>
static unregisterPlugin(): void
  
Unregisters a callback from the SA.

This API unregisters a callback and releases resources when an application exits, ensuring that the callback capability is correctly released.

> **NOTE**
>
> **unregisterPlugin** unregisters a plug-in from the SA.
  
**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE or ohos.permission.ACCESS_DLP_SERVICE since API version 26.0.0. ohos.permission.ENTERPRISE_ACCESS_DLP_FILE for API versions 21 to 24.

**System capability**: SystemCapability.Security.DataLossPrevention

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 19100001 | Invalid parameter value. |
| 19100002 | Credential service busy due to too many tasks or duplicate tasks. |
| 19100003 | Credential task time out. |
| 19100004 | Credential service error. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.DlpConnManager.unregisterPlugin();
```

## DlpFileQueryOptions

Represents the query options about an enterprise DLP file.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.DataLossPrevention

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| classificationLabel | string | No| Yes| User-defined classification label of an enterprise DLP file. This parameter is left empty by default. The value contains a maximum of 255 bytes. If the value is out of range, error code 19100001 is thrown.|

## dlpPermission.queryOpenedEnterpriseDlpFiles

queryOpenedEnterpriseDlpFiles(options?: DlpFileQueryOptions): Promise&lt;Array&lt;string&gt;&gt;

Queries the URIs of enterprise DLP files that have been opened and meet the specified options. This API uses a promise to return the result.

This API is called when the system needs to manage or track enterprise DLP files that have been opened by the current application. It can be used in scenarios such as file status check and resource management.

> **NOTE**
>
> - This API can only query enterprise DLP files generated by the caller application through [generateDlpFileForEnterprise](#dlppermissiongeneratedlpfileforenterprise21). Enterprise DLP files generated by other applications cannot be queried.
> - Read-only enterprise DLP files with the same classification label are opened in the same sandbox. If multiple such files are opened in a sandbox, the URIs of all files that have been opened (including manually closed files) are returned.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [DlpFileQueryOptions](#dlpfilequeryoptions) | No| Query options about an enterprise DLP file. This parameter is required when specific enterprise DLP files are queried by classification label. It is optional when all enterprise DLP files are queried. If this parameter is not passed or an empty string is passed, all enterprise DLP files are queried.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the URI list of the target enterprise DLP files that have been opened.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 801 | Capability not supported. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

let options: dlpPermission.DlpFileQueryOptions = {
  classificationLabel: 'label1'
}; // Set query options and specify the classification label.
dlpPermission.queryOpenedEnterpriseDlpFiles(options).then((uris: Array<string>) => {
  console.info("try to query opened enterprise dlp files, result: ", JSON.stringify(uris));
}).catch((error: BusinessError)=> {
  console.error(error.message);
}).finally(()=> {
  console.info("after querying opened enterprise dlp files");
});
```

## dlpPermission.closeOpenedEnterpriseDlpFiles

closeOpenedEnterpriseDlpFiles(options?: DlpFileQueryOptions): Promise&lt;void&gt;

Closes all opened enterprise DLP files that meet the specified options. This API uses a promise to return the result.

This API can be called to close enterprise DLP files in batches, clear file resources, or release file handles before exiting the application.

> **NOTE**
>
> This API can only close enterprise DLP files generated by the caller app through [generateDlpFileForEnterprise](#dlppermissiongeneratedlpfileforenterprise21).
  
**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions**: ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability**: SystemCapability.Security.DataLossPrevention

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| options | [DlpFileQueryOptions](#dlpfilequeryoptions) | No| Query options about an enterprise DLP file. This parameter is passed when you need to disable specific enterprise DLP files by category tag. This parameter is not required when you need to disable all enterprise DLP files. If this parameter is not passed or an empty string is passed, all enterprise DLP files are closed.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [DLP Error Codes](errorcode-dlp.md).

| Error Code| Error Message|
| -------- | -------- |
| 201 | Permission denied. |
| 801 | Capability not supported. |
| 19100001 | Invalid parameter value. |
| 19100011 | The system ability works abnormally. |

**Example**

```ts
import { dlpPermission } from '@kit.DataProtectionKit';

let options: dlpPermission.DlpFileQueryOptions = {
  classificationLabel: 'label1'
};
dlpPermission.closeOpenedEnterpriseDlpFiles(options).then(() => {
  console.info("try to close opened enterprise dlp files");
}).catch((error: BusinessError)=> {
  console.error(error.message);
}).finally(()=> {
  console.info("after closing opened enterprise dlp files");
});
```
