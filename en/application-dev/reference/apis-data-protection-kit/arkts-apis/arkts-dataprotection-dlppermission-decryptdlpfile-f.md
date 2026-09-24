# decryptDlpFile

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## decryptDlpFile

```TypeScript
function decryptDlpFile(dlpFd: number, plaintextFd: number): Promise<void>
```

Decrypts a DLP file to generate a plaintext file. This API can be called only by enterprise accounts. This API uses a promise to return the result.

This API decrypts DLP files into plaintext files, which is applicable to exporting or migrating files by users with owner permissions.

> **NOTE:** 
> 
> This API can be called only by enterprise accounts. Enterprises need to set up their own enterprise account
> servers. The enterprise server determines whether an account is authorized to decrypt DLP files.

**Since:** 21

**Required permissions:** ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dlpFd | number | Yes | FD of the DLP file to be decrypted. The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value of **dlpFd** is less than 0, n error log is generated, and the function stops running. If the value of **dlpFd** is greater than 2&lt;sup&gt;31&lt;/sup&gt;-1, the excess part will be truncated. |
| plaintextFd | number | Yes | FD of the decrypted file. The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value of **plaintextFd** is less than 0, an error log is generated, and the function stops running. If the value of **plaintextFd** is greater than 2&lt;sup&gt;31&lt;/sup&gt;, the excess part will be truncated. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs.<br>**Applicable version:** 20 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.0.1 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-encryption-and-decryption-error) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-encryptiondecryption-timeout) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-credential-service-error) | Credential service error. |
| [19100005](../errorcode-dlp.md#19100005-credential-authentication-server-error) | Credential authentication server error. |
| [19100008](../errorcode-dlp.md#19100008-non-dlp-file) | The file is not a DLP file. |
| [19100009](../errorcode-dlp.md#19100009-failed-to-operate-the-dlp-file) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
| [19100013](../errorcode-dlp.md#19100013-user-access-denied) | The user does not have the permission. |

**Examples**

```TypeScript
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
