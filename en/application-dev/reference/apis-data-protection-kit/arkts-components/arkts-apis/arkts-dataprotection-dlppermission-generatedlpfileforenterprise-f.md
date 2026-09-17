# generateDlpFileForEnterprise

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## generateDlpFileForEnterprise

```TypeScript
function generateDlpFileForEnterprise(plaintextFd: number, dlpFd: number, property: DLPProperty, customProperty: CustomProperty): Promise<void>
```

Encrypts a plaintext file to generate a DLP file for an enterprise account. This API can be called only by enterprise accounts. This API uses a promise to return the result.

This API encrypts a plaintext file to generate a DLP file that can be accessed only by enterprise accounts, implementing enterprise-level file permission management.

> **NOTE:** 
> 
> This API can be called only by enterprise accounts. Enterprises need to set up their own enterprise account
> servers. This API generates a DLP file, which is an encrypted file that can be accessed only by accounts
> authorized by the enterprise server.

**Since:** 21

**Required permissions:** ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**System capability:** SystemCapability.Security.DataLossPrevention

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| plaintextFd | number | Yes | FD of a plaintext file. The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value of **fd** is less than 0, an error log is generated, and the function stops running. If the value of **fd** is greater than 2&lt;sup&gt;31&lt;/sup&gt;-1, the excess part will be truncated. |
| dlpFd | number | Yes | FD of an encrypted file. The value range is [0, 2&lt;sup&gt;31&lt;/sup&gt;-1]. If the value of **fd** is less than 0, an error log is generated, and the function stops running. If the value of **fd** is greater than 2&lt;sup&gt;31&lt;/sup&gt;-1, the excess part will be truncated. |
| property | [DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i.md) | Yes | General policy of DLP files. |
| customProperty | [CustomProperty](arkts-dataprotection-dlppermission-customproperty-i.md) | Yes | Enterprise custom policy. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs.<br>**Applicable version:** 20 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-encryption-and-decryption-error) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-encryptiondecryption-timeout) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-credential-service-error) | Credential service error. |
| [19100005](../errorcode-dlp.md#19100005-credential-authentication-server-error) | Credential authentication server error. |
| [19100009](../errorcode-dlp.md#19100009-failed-to-operate-the-dlp-file) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
| [19100014](../errorcode-dlp.md#19100014-account-not-logged-in) | Account not logged in. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';

let plaintextFd: number | undefined = undefined;
let dlpFd: number | undefined = undefined;
let plainFilePath: string = 'file://docs/storage/Users/currentUser/Documents/test.txt';
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
  console.error(`Failed to generate DLP file for enterprise. Code: ${error.code}, message: ${error.message}`);
}).finally(()=>{
  if (dlpFd) {
    fileIo.closeSync(dlpFd);
  }
  if (plaintextFd) {
    fileIo.closeSync(plaintextFd);
  }
});
```
