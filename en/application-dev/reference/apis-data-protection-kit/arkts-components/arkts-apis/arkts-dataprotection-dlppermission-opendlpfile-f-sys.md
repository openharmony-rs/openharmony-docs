# openDLPFile (System API)

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## openDLPFile

```TypeScript
function openDLPFile(ciphertextFd: number, appId: string): Promise<DLPFile>
```

Opens a DLP file. After the API is successfully called, the **DLPFile** object is returned, which can be used to manage the permissions on the DLP file and perform related operations. This API uses a promise to return the result.

After calling **openDLPFile()** to return a **DLPFile** object, the system must call [closeDLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#closedlpfile) to release resources after using the object.

When a DLP management application or an authorized application needs to access a DLP file, it must first open the file to obtain the managed object.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ciphertextFd | number | Yes | FD of the encrypted file. The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value of **fd** is less than 0, an error log is generated, and the function stops running. If the value of **fd** is greater than 2&lt;sup&gt;31&lt;/sup&gt;-1, the excess part will be truncated. |
| appId | string | Yes | ID of the caller. The value contains 8 to 1024 bytes. If the value is out of range, error code 401 is thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md)&gt; | Promise If the value is **resolve**, a **DLPFile** object is returned, indicating that a DLP file is successfully opened. If the value is **reject**, an error is returned, indicating that the DLP file fails to be opened. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-encryption-and-decryption-error) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-encryptiondecryption-timeout) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-credential-service-error) | Credential service error. |
| [19100005](../errorcode-dlp.md#19100005-credential-authentication-server-error) | Credential authentication server error. |
| [19100008](../errorcode-dlp.md#19100008-non-dlp-file) | The file is not a DLP file. |
| [19100009](../errorcode-dlp.md#19100009-failed-to-operate-the-dlp-file) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
| [19100018](../errorcode-dlp.md#19100018-application-unauthorized) | The application is not authorized. |
| [19100019](../errorcode-dlp.md#19100019-dlp-file-has-expired) | The DLP file has expired. |
| [19100020](../errorcode-dlp.md#19100020-network-disconnected) | No network connection. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId; // The app ID is obtained from the application package.

  file = fileIo.openSync(uri).fd; // The FD is obtained by opening a file.
  dlpFile = await dlpPermission.openDLPFile(file, appId); // Open a DLP file.
  await dlpFile?.closeDLPFile(); // Close the DLP object.

  if (file) {
    fileIo.closeSync(file);
  }
}

ExampleFunction();
```


<a id="opendlpfile-1"></a>

## openDLPFile

```TypeScript
function openDLPFile(ciphertextFd: number, appId: string, callback: AsyncCallback<DLPFile>): void
```

Opens a DLP file. This API uses an asynchronous callback to return the result. After the API is successfully called, the **DLPFile** object is returned, which can be used to manage the permissions on the DLP file and perform related operations. After using the **DLPFile** object, call **closeDLPFile** to close the object to prevent resource leakage.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ciphertextFd | number | Yes | FD of the encrypted file. The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value of **fd** is less than 0, an error log is generated, and the function stops running. If the value of **fd** is greater than 2&lt;sup&gt;31&lt;/sup&gt;-1, the excess part will be truncated. |
| appId | string | Yes | ID of the caller. The value contains 8 to 1024 bytes. If the value is out of range, error code 401 is thrown. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md)&gt; | Yes | Callback used to receive the result of opening a DLP file. The callback parameters include **err** and **res**. **err** is **undefined** when the operation is successful; otherwise, **err** is an error object. **res** is a **DLPFile** object that represents the DLP file opened. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-encryption-and-decryption-error) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-encryptiondecryption-timeout) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-credential-service-error) | Credential service error. |
| [19100005](../errorcode-dlp.md#19100005-credential-authentication-server-error) | Credential authentication server error. |
| [19100008](../errorcode-dlp.md#19100008-non-dlp-file) | The file is not a DLP file. |
| [19100009](../errorcode-dlp.md#19100009-failed-to-operate-the-dlp-file) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
| [19100018](../errorcode-dlp.md#19100018-application-unauthorized) | The application is not authorized. |
| [19100019](../errorcode-dlp.md#19100019-dlp-file-has-expired) | The DLP file has expired. |
| [19100020](../errorcode-dlp.md#19100020-network-disconnected) | No network connection. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
let file: number | undefined = undefined;
let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
let appId = '';
let bundleName = 'com.ohos.note';
let userId = 100;

let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
appId = data.signatureInfo.appId; // The app ID is obtained from the application package.

file = fileIo.openSync(uri).fd; // The FD is obtained by opening a file.
dlpPermission.openDLPFile(file, appId, async (err, res) => { // Open a DLP file.
  if (err) {
    console.error(`Failed to open DLPFile. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('res', JSON.stringify(res));
  }
  await res?.closeDLPFile(); // Close the DLP object.
  if (file) {
    fileIo.closeSync(file);
  }
});
```
